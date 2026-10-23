# Metric Findings — Weekly Summary Experiment (Week 5)

Source: [Nudge Dataset (Google Sheet)](https://docs.google.com/spreadsheets/d/1jMZXItXhbYxdBkzM74z2BXbCHHbnvqh4Eyclmmhdiww/edit), 5 tables (`nudge_users`, `nudge_sessions`, `nudge_retention`, `nudge_nudges`, `nudge_weekly_summary_sends`), 500 users across 5 weekly cohorts (100/cohort). Cohort week 5 is the only cohort in the `summary_v1` vs. `control` experiment (50/50 split); all other cohorts have `variant = ''` and are not part of the experiment.

*(Note: no SQL engine was available in this environment to execute queries directly. SQL below is written to standard syntax; the actual numbers were computed by loading the same CSVs and running equivalent group-by/join logic, then spot-checked against the SQL's intent.)*

## Q1: 30-day retention by cohort week

```sql
SELECT
  cohort_week,
  COUNT(*) AS n_users,
  SUM(day_30) AS retained_day_30,
  ROUND(100.0 * SUM(day_30) / COUNT(*), 1) AS day_30_retention_pct
FROM nudge_retention
GROUP BY cohort_week
ORDER BY cohort_week;
```

**Plain English**: For each weekly signup cohort, count how many users were still active at day 30 and divide by the cohort size.

**Result**:

| cohort_week | n | day_30 retained | rate |
|---|---|---|---|
| 1 | 100 | 32 | 32.0% |
| 2 | 100 | 25 | 25.0% |
| 3 | 100 | 25 | 25.0% |
| 4 | 100 | 22 | 22.0% |
| 5 | 100 | 29 | 29.0% |

**What it means for scaling the weekly summary**: Retention declines steadily from week 1 to week 4 (32% → 22%), consistent with the retention drop this whole initiative exists to address. Week 5 breaks that decline (22% → 29%) — but week 5 is also the only cohort with the summary_v1/control experiment running inside it, so this uptick is very likely the experiment's effect showing through at the cohort level, not a reversal of the underlying trend. Q3 below isolates that effect directly.

## Q2: Week-1 goal-setters vs. non-setters — day-30 retention

```sql
SELECT
  CASE
    WHEN u.goal_set_date IS NOT NULL
         AND u.goal_set_date <= u.signup_date + INTERVAL '7 days'
    THEN 'goal_set_week1'
    ELSE 'no_goal_week1'
  END AS goal_segment,
  COUNT(*) AS n_users,
  SUM(r.day_30) AS retained_day_30,
  ROUND(100.0 * SUM(r.day_30) / COUNT(*), 1) AS day_30_retention_pct
FROM nudge_users u
JOIN nudge_retention r ON r.user_id = u.user_id
GROUP BY goal_segment;
```

**Plain English**: Join users to their retention record, split into two groups based on whether they set a savings goal within 7 days of signup, and compare day-30 retention between the groups.

**Result**:

| Segment | n | day_30 retained | rate |
|---|---|---|---|
| Goal set in week 1 | 165 | 60 | 36.4% |
| No goal in week 1 | 335 | 73 | 21.8% |

**What it means for scaling the weekly summary**: Confirms the internal finding this whole initiative was built on — goal-setters retain meaningfully better (36.4% vs. 21.8%, a 1.7x difference). This doesn't test the weekly summary directly, but it reinforces the design decision to make goal progress a core part of the feature and to treat the goal-setting nudge as high-leverage.

## Q3: Week 5 only — day-7 and day-30 retention, treatment vs. control

```sql
SELECT
  u.variant,
  COUNT(*) AS n_users,
  ROUND(100.0 * SUM(r.day_7) / COUNT(*), 1) AS day_7_retention_pct,
  ROUND(100.0 * SUM(r.day_30) / COUNT(*), 1) AS day_30_retention_pct
FROM nudge_users u
JOIN nudge_retention r ON r.user_id = u.user_id
WHERE u.cohort_week = 5
  AND u.variant IN ('summary_v1', 'control')
GROUP BY u.variant;
```

**Plain English**: Restrict to week-5 users only (the experiment cohort), join to retention, and compare day-7 and day-30 retention between the two variants.

**Result**:

| Variant | n | day_7 rate | day_30 rate |
|---|---|---|---|
| summary_v1 | 50 | 76.0% | 36.0% |
| control | 50 | 46.0% | 22.0% |

**What it means for scaling the weekly summary**: This is the core result. Treatment users retained 30 points better at day 7 (76% vs. 46%) and 14 points better at day 30 (36% vs. 22%) than control, in the same cohort, same signup week — the cleanest causal comparison available in this data. This is a strong, direct signal in favor of scaling the feature. Caveat: n=50 per arm is a small sample for a single week; before scaling company-wide, worth confirming this holds up with more weeks of experiment data rather than acting on one cohort alone.

## Q4: Weekly summary open rate across 4 sends, treatment vs. control

```sql
SELECT
  week_number,
  variant,
  COUNT(*) AS n_sends,
  SUM(opened) AS n_opened,
  ROUND(100.0 * SUM(opened) / COUNT(*), 1) AS open_rate_pct
FROM nudge_weekly_summary_sends
GROUP BY week_number, variant
ORDER BY week_number, variant;
```

**Plain English**: For each of the 4 weekly sends, compute what fraction of users in each variant opened it.

**Result**:

| week_number | summary_v1 open rate | control open rate |
|---|---|---|
| 1 | 28.0% | 4.0% |
| 2 | 52.0% | 4.0% |
| 3 | 52.0% | 4.0% |
| 4 | 56.0% | 6.0% |

**What it means for scaling the weekly summary**: Open rate did improve across the 4 sends for treatment (28% → 56%, roughly doubling), while control stayed flat and low (4-6%) throughout. This is a notably positive sign against the "engagement mechanic goes stale" risk flagged earlier in discovery (see [strategy.md](../strategy.md) — the Cleo comparison) — at least within this 4-week window, engagement is climbing, not decaying. It does not resolve the longer-horizon question (does this hold at week 8, week 12?), which remains untested.

## Overall: Does This Support Scaling the Weekly Summary?

Yes, directionally, with one caveat. All three feature-specific results (Q3 retention lift, Q4 rising open rate, plus Q2's reinforcement of the goal-setting mechanism) point the same direction and are internally consistent with each other — not just individually positive but mutually corroborating. The caveat is sample size and duration: this is one 50-vs-50 cohort over 4 weeks. Before a full scale decision, it's worth checking whether this result replicates in additional cohort weeks and whether engagement continues climbing (or starts to flatten/decline) past week 4, rather than treating this single experiment as final proof.
