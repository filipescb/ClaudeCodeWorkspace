# Strategy: Recovering the Retention Drop

## The Gap

30-day retention fell 7 points, from 44% to 37%, over the last two quarters.

## Supporting Signals

- Users who don't set a savings goal in week 1 churn at almost double the rate of users who do (Raj, data analysis).
- User research shows people who connect their account and see the dashboard don't know what to do next — there's no clear next step after the spending breakdown (Lena).
- The home feed doesn't change based on recency of use — it looks the same whether a user opened the app yesterday or three weeks ago (Raj).
- The weekly summary email has a 22% open rate (decent), but the in-app experience doesn't continue the story the email starts — the handoff is jarring (Lena).
- Savings goals are set once and never referenced again — directly undercutting the app's own known retention driver (NPS #6).
- At least one user disabled notifications entirely after a low-value nudge (a $12 coffee purchase alert) — nudge relevance, not just nudge existence, drives engagement or disengagement (NPS #4).

## Supporting Research

Interviews with 3 users at different lifecycle stages (see [research/interview-synthesis.md](research/interview-synthesis.md)):

- A power user's deepest value — the app surfacing personal spending patterns — only emerged after ~3 months of organic use. Churned and struggling new users (5 weeks, 10 days in) don't stick around long enough to reach that point.
- Both a churned user and a new user independently described wanting the app to actively tell them what to do next, rather than leaving them to interpret a static dashboard on their own.

**Implication**: the retention problem isn't the first aha moment (both users described it positively) — it's that nothing closes the gap between that first moment and the deeper, personalized payoff that currently takes months to arrive organically.

NPS analysis of 10 comments corroborates this: the dominant complaint (4/10) is a static, repetitive experience with nothing pulling users back (see [research/nps-analysis.md](research/nps-analysis.md)).

## Competitive White Space

Analysis of 5 competitors (YNAB, Monarch Money, Rocket Money, Copilot Money, Cleo — see [research/competitive-matrix.md](research/competitive-matrix.md)) surfaced two gaps none of them own well:

1. **Deep personalization delivered passively.** Competitors re-engage users either through required manual effort (YNAB's budgeting, Cleo's chat) or automation tied to a narrow use case (Rocket Money's subscriptions/bills). None deliver a genuinely personalized, non-obvious insight to a user who does nothing but glance at a screen — exactly what Nudge's own interview and NPS research shows users want.
2. **Goal continuity as a recurring, first-class touchpoint.** Every competitor treats savings/financial goals as a static setup step rather than something actively narrated over time. Given Nudge's own data (week-1 goal-setters churn at half the rate) and NPS feedback (a goal "never mentioned again"), no competitor is claiming this territory.

**Implication**: both gaps point at the same direction already being explored below — the weekly summary concept isn't just a plausible internal hypothesis, it also targets space competitors aren't occupying.

**Real-user sentiment check** (see [research/competitive-reddit.md](research/competitive-reddit.md)): Cleo is the one competitor that actually attempted passive, personality-driven personalization (its "roast me" AI feature) — and real user feedback shows it goes stale within about a month, mirroring Nudge's own repetition problem. This validates Gap 1 (personalization) but adds a constraint: freshness over time matters as much as personalization itself, or any new touchpoint decays the same way. Gap 2 (goal continuity) is not contradicted by this data, but also isn't directly confirmed — confidence there is lower than Gap 1.

## Hypothesis

**Original**: Users go passive because the app stops feeling relevant after the first week. The initial spending breakdown is a compelling "aha moment," but after that, Nudge doesn't give users a reason to come back that feels personal, timely, or actionable.

**Updated** (per [docs/hypothesis.md](docs/hypothesis.md), based on two rounds of prototype usability testing): Users go passive because nothing after the first week gives them a reason to return that they *trust* and that *stays fresh*. A personalized weekly summary can close that gap, but only if it (1) makes its claims verifiable rather than asking users to take a number on faith, (2) frames insights as support rather than judgment, (3) includes a reward mechanic that itself doesn't go stale with repetition, and (4) reflects each user's actual state (e.g., has-goal vs. no-goal) rather than presenting one universal screen. The core mechanism is unchanged — close the post-aha gap with something personal and recurring — but trust, tone, staleness, and state-branching are now treated as preconditions for that mechanism to work, not later refinements.

## Direction Being Explored

A personalized weekly summary screen, in-app (not email-only): shows the user's top insight for the week, one actionable nudge based on their actual patterns, and progress toward their savings goal if they have one (Lena's concept).

Raj's initial assessment: technically doable with existing data sources; would require building new ranking logic to determine which insight to surface.

**Constraint identified from NPS feedback**: any recurring touchpoint (including this weekly summary) must be filtered for relevance and must reference active savings goals — otherwise it risks the same fate as current notifications (ignored, or actively opted out of).

**Constraint identified from competitive sentiment**: the insight/nudge content must stay genuinely fresh over time, not just personalized once — Cleo's roast feature shows that even a personalized, passive mechanic loses its engagement value within about a month if it starts to repeat.

**Status**: A working prototype now exists ([prototype/index.html](prototype/index.html)) and has been through two rounds of testing — one interview-style feedback round and one simulated persona playtest (Priya/Tom/Amara). Findings so far: comprehension and directional behavior change are landing, but a weak re-engagement trigger and lack of trust-verification (now partially addressed via an expandable transaction list) both surfaced as risks. See [CLAUDE.md](CLAUDE.md) for remaining open decisions (timeline, sign-off).

## Quantitative Evidence (Week 5 Experiment)

A live experiment in cohort week 5 (50 users summary_v1 vs. 50 control) provides the first quantitative evidence for this direction — see [data/metric-findings.md](data/metric-findings.md):

- **Retention**: treatment retained 76% vs. 46% (control) at day 7, and 36% vs. 22% at day 30.
- **Engagement**: weekly summary open rate rose from 28% to 56% across the 4 sends for treatment, while control stayed flat at 4-6% — a positive signal against the "goes stale" risk flagged in Competitive White Space above, at least within the 4-week window tested.
- **Caveat**: single 50-vs-50 cohort over 4 weeks — directionally strong, but worth confirming replication across more cohorts before treating as final proof.

**Mechanism** (see [data/metric-diagnosis.md](data/metric-diagnosis.md)): the summary's retention lift traces to two concrete effects, not a vague engagement boost — it roughly doubles week-1 goal-setting conversion (44% vs. 22%, treatment vs. control), which is independently the strongest retention lever in the whole dataset (34.8% vs. 21.6% day-30 retention), and it lifts raw session frequency 43% (5.28 vs. 3.68 sessions/user). It does not yet close two pre-existing gaps that persist even within the treatment group: a platform-correlated retention gap (iOS 47.8% vs. Android 27.3% day-30, despite equal open rates — ruling out a delivery/engagement explanation) and a paid-acquisition-channel gap (consistent across the whole dataset, not summary-specific). Both are flagged as candidate next-sprint investigations, not yet root-caused.

## Recommended Action

Build and user-test a prototype of the personalized weekly summary screen, since it's the only option considered that directly closes the identified gap (nothing pulls users back after the first aha moment) rather than just improving a funnel that already works. Recommendation submitted to Marcus for decision — see [docs/decision-brief.md](docs/decision-brief.md).
