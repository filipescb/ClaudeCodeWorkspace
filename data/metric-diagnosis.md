# Metric Diagnosis — 30-Day Retention

Built on [data/metric-findings.md](metric-findings.md). All numbers below are computed directly from the same 5 tables (`nudge_users`, `nudge_sessions`, `nudge_retention`, `nudge_nudges`, `nudge_weekly_summary_sends`), not estimated.

## 1. Metric Tree: What Actually Moves 30-Day Retention

```
30-Day Retention
│
├── Acquisition Composition (who signs up) — pre-existing, not fixed by any in-app feature
│   ├── Channel: organic 30.9% vs. referral 26.5% vs. paid 20.2% (day-30, all 500 users)
│   └── Platform: iOS 29.8% vs. android 25.3% vs. web 23.2% (day-30, all 500 users)
│
├── Week-1 Activation
│   └── Goal set within 7 days of signup: 34.8% retained vs. 21.6% for no goal in week 1
│       (largest single lever measured in this dataset)
│
├── Sustained Engagement Cadence (weeks 1→4)
│   ├── Session frequency per user (5.74 → 5.08 → 4.48 → 3.69 across cohort weeks 1-4)
│   └── Nudge open/act rate per cohort week (12.1%/4.2% → 11.7%/4.5% → 14.3%/6.6% → 9.4%/3.2%)
│
└── Recurring Touchpoint (the weekly summary, treatment-only lever)
    ├── Drives session frequency (5.28 vs. 3.68 sessions/user, treatment vs. control, week 5)
    └── Drives week-1 goal-setting conversion (44% vs. 22%, treatment vs. control, week 5) —
        this is the mechanism connecting the summary to the Week-1 Activation branch above
```

**Reading the tree**: acquisition composition is a lever the weekly summary cannot pull — it's who signs up, not what happens after. The two levers actually reachable by product work are week-1 goal-setting and engagement cadence, and the data below shows the weekly summary's main effect is pulling the goal-setting lever, not inventing a new mechanism.

## 2. What Caused the Weeks 1-4 Decline (Specific, Not Generic)

Day-30 retention by cohort: 32% → 25% → 25% → 22%. Two specific, data-supported causes:

**Session frequency erodes steadily, cohort over cohort.** Average sessions per user: 5.74 (week 1) → 5.08 (week 2) → 4.48 (week 3) → 3.69 (week 4) — a 36% drop from week 1 to week 4. This tracks the retention decline's general direction, though not perfectly step-for-step (week 2→3 retention is flat at 25% despite sessions still falling).

**Nudge engagement specifically collapses in week 4**, the cohort with the lowest retention. Open/act rates: week 1 12.1%/4.2%, week 2 11.7%/4.5%, week 3 14.3%/6.6%, week 4 **9.4%/3.2%** — a sharp dip coinciding exactly with week 4's lowest retention (22%). This is the most specific, localized signal in the weeks 1-4 data.

**What does *not* explain the decline**: goal-setting rate by cohort week is 32% → 29% → **44%** → 27% — week 3 has the highest goal-setting rate of any week 1-4 cohort, yet its retention (25%) is flat with week 2, not higher. So while goal-setting is a strong retention lever overall (Section 1), its week-to-week rate doesn't explain the specific shape of the weeks 1-4 decline — the decline is better explained by eroding session frequency and (in week 4 specifically) collapsing nudge engagement, not by fewer people setting goals.

## 3. What the Week 5 Treatment vs. Control Split Actually Fixed

The weekly summary's effect operates through two concrete, measurable mechanisms — not a vague "engagement" lift:

**It roughly doubles week-1 goal-setting.** 44% of treatment users set a goal within week 1, vs. 22% of control — exactly a 2x conversion difference. Since goal-setting-in-week-1 is independently the strongest retention lever in this entire dataset (34.8% vs. 21.6% day-30 retention, Section 1), this is very likely the primary channel through which the summary's retention lift operates: the summary isn't just "more engaging" in the abstract, it's specifically driving the one activation behavior already known to predict retention.

**It increases raw session frequency.** 5.28 sessions/user (treatment) vs. 3.68 (control) — 43% more app opens. The `weekly_summary` screen is treatment users' single most-visited screen (114 visits, more than `home`'s 72), meaning the summary is functioning as a real destination, not just a passive notification users dismiss.

**What it does not yet fix**: web and platform-level gaps persist inside the treatment group too (Section 4) — the summary lifts everyone somewhat, but doesn't close pre-existing platform/channel-driven differences.

## 4. Four Ranked Hypotheses for Why Treatment Users Still Churned

32 of 50 week-5 treatment users (64%) churned despite being in the summary_v1 arm. Each hypothesis below was checked directly against churned (n=32) vs. retained (n=18) treatment users.

### Rank 1: Platform-correlated baseline gap, not an engagement gap

**Prediction**: Treatment users on Android and web churn at meaningfully higher rates than iOS users, *despite opening the weekly summary at equal rates* — meaning the gap is a pre-existing platform-correlated factor, not the summary failing to land on those platforms.

**Confidence: 7/10** — the retention gap is large and consistent with the baseline (non-treatment) pattern, and open rates are nearly identical across platforms, which specifically rules out "the summary isn't being opened on Android" as the explanation.

**Data found**: Within treatment, day-30 retention is iOS 47.8%, Android 27.3%, web 0% (n=5, small) — but send open rate is nearly flat across platforms (iOS 47.8%, Android 46.6%, web 45%). The same ordering (iOS > Android > web) holds across *all* 500 users, not just treatment (29.8% / 25.3% / 23.2%), meaning this predates the summary entirely.

**What would confirm it**: A future cohort shows the same iOS > Android > web retention ordering *within* treatment, at a similar magnitude, even as sample size grows — confirming this is structural, not week-5 noise.

**What would rule it out**: If Android's open rate were meaningfully lower than iOS's (evidence of a delivery/notification problem specific to Android), that would point to a fixable technical issue instead of a baseline population difference — but that's not what the data shows (46.6% vs. 47.8%, effectively equal).

**What would raise confidence to 9-10**: This 7/10 reflects two separate gaps — statistical robustness (is the pattern even stable) and causal specificity (is "platform" the real mechanism, or a proxy for something else).

- *Statistical robustness*: n=22-23 per platform arm (n=5 for web) is thin for a 20pp gap — replication across 2-3 more treatment cohorts, an actual significance/proportion test rather than eyeballing percentages, and a check of whether the gap holds at day 60/90 (vs. converging past day 30) would all be needed before trusting the magnitude, not just the direction.
- *Causal specificity*: "opened" is a coarse signal that doesn't rule out post-open friction. Crash rates, load times, and whether the notification deep-link actually completes successfully by platform would distinguish "fixable technical issue" from "baseline population gap" — equal open rate with worse crash/load metrics on Android would flip the conclusion entirely. Notification permission opt-in rate by platform isn't in this dataset at all — if Android grants permission at a lower rate, the open-rate comparison only measures the reachable subset, hiding a delivery problem. A confound check beyond acquisition_channel (device age, OS version) is also missing — if Android skews toward older devices, that's an alternative explanation this data can't currently rule out. A qualitative cross-check (support tickets, app store reviews, or a direct question in the next interview round) would confirm whether this is a felt problem or a purely statistical artifact.
- *Highest-leverage single addition*: the crash/load-time/notification-permission data, since it's what actually distinguishes "a fixed population we can't reach" (current framing) from "a bug wearing a demographic disguise" — which would change the recommendation entirely.

### Rank 2: Paid-acquisition users churn regardless of treatment

**Prediction**: Users acquired via paid channels churn at a higher rate than organic/referral users even when they receive and engage with the weekly summary, because the gap reflects acquisition-time intent, not something the summary content can address.

**Confidence: 7/10** — the direction is consistent across three different cuts of the data (treatment-churn skew, week 1-4 baseline, and the full 500-user baseline), which is a real pattern, but the week-5 treatment-specific sample (32 churned) is small enough that this should be treated as strongly suggestive, not proven.

**Data found**: Among treatment churners, 31% were paid-acquired vs. 22% of retained treatment users. This matches the baseline: across all 500 users, paid-channel day-30 retention is 20.2%, vs. organic's 30.9% and referral's 26.5% — the same direction, at similar magnitude, everywhere it's measured.

**What would confirm it**: Paid-acquired users show lower goal-setting conversion *even within treatment* (i.e., the summary's own core mechanism, Section 3, works less well on this subgroup specifically) — that would tie acquisition quality directly to the feature's own primary lever, not just to a generic retention gap.

**What would rule it out**: If, in a larger sample, paid-acquired treatment users' retention converged with organic/referral treatment users' retention (i.e., the gap present in control disappears under treatment), that would mean the summary *does* fully offset acquisition-channel quality — contradicting this hypothesis.

### Rank 3: Opening and acting on the summary is not sufficient for retention on its own

**Prediction**: Users who churn despite being in treatment are not churning from *lack* of engagement with the summary — they interact with it and still leave, meaning whatever ultimately drives their churn happens downstream of the nudge interaction, not from ignoring it.

**Confidence: 6/10** — very clearly supported as a negative finding (ruling out "they just didn't engage"), but it doesn't identify what the actual downstream driver is, which limits how directly actionable it is on its own.

**Data found**: Churned treatment users opened at least one send at a *higher* rate than retained users (96.9% vs. 94.4%), and acted on at least one send at a notably higher rate (62.5% vs. 50%). Send-level open and act rates are also equal-or-higher for churners (47%/19.5% vs. 47%/13.9%). Whatever is driving churn, it is not simply "these users never engaged."

**What would confirm it**: Qualitative follow-up (an interview or in-app survey) with churned-but-engaged treatment users identifying a specific reason unrelated to the nudge mechanics itself (e.g., "the cap felt punitive over multiple weeks," "I didn't like what happened after I acted on it") — this hypothesis is inherently under-specified until that reason is named.

**What would rule it out**: If a larger sample showed churned users' *engagement quality* was actually lower on a dimension not yet measured here (e.g., time spent per session, depth of interaction with the transaction detail view) — that would mean engagement wasn't actually equal, just equally "opened," undercutting this hypothesis.

### Rank 4: Churned users lack a savings goal, so the summary has nothing to help them progress on

**Prediction**: Treatment users who churned did not set a savings goal, so the summary's goal-progress component had nothing to show them, reducing its value and making churn more likely.

**Confidence: 2/10** — directly contradicted by the data already in hand.

**Data found**: Goal-set rate is virtually identical between churned (43.8%) and retained (44.4%) treatment users. If anything, retained users have a marginally *higher* goal-set rate, but the gap is negligible — this hypothesis does not explain the churn/retain split within treatment.

**What would confirm it**: N/A in this dataset — the existing data already argues against it. It would need a much larger sample to resurrect this as plausible, and even then, the near-identical rates found here are a real result, not a sampling artifact of a huge gap.

**What would rule it out**: This is already effectively ruled out by the near-equal rates above; no further data point is needed to reject it as the primary driver, though it remains theoretically possible goal-setting matters differently *combined* with another factor (e.g., goal type) not tested here.

## 5. Which Hypothesis to Test First Next Sprint

**Rank 1 (platform-correlated baseline gap)**, because it's the most concrete, most immediately actionable, and cheapest to test further. Unlike Rank 2 (acquisition channel, largely outside product's control) and Rank 3 (requires new qualitative research to even name the driver), Rank 1 has a clear next step already implied by the data: instrument and compare Android vs. iOS experience quality more deeply (crash rates, notification delivery success, load times, post-open session depth) to determine whether the gap is genuinely a fixed population difference or a solvable technical/UX issue currently disguised as one. If it turns out to be fixable, it's the single highest-leverage fix available, since it affects 217 of 500 users (43% of the entire user base is on Android) — far larger than the paid-acquisition segment or any single qualitative finding could reach.
