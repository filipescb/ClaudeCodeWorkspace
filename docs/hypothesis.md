# Learning Synthesis & Hypothesis Update — Engage v2

Synthesized from [change_log.md](../change_log.md) and [docs/decision-brief.md](decision-brief.md), plus the two prototype usability testing rounds (see [research/prototype-usability-testing.md](../research/prototype-usability-testing.md)).

## What We Know

- 30-day retention dropped from 44% to 37% over two quarters, and week-1 goal-setters churn at roughly half the rate of non-setters (internal data).
- The first aha moment (the initial spending breakdown) is not the problem — it's consistently well-received across interviews, NPS, and both usability testing rounds. The drop-off happens after it.
- The dominant complaint across independent sources (NPS, interviews) is a static, repetitive post-onboarding experience with nothing pulling users back.
- Savings goals are set once and never referenced again — a specific, recurring complaint (NPS, and reproduced in the Round 2 persona playtest via Priya's reaction).
- No competitor combines deep personalization with a low-effort, passive experience, or treats goal progress as a recurring touchpoint — this white space is still open (competitive research).
- A passive, personalized engagement mechanic can still go stale: Cleo's "roast me" feature loses its pull within about a month once it starts repeating (competitive sentiment research).
- Prototype comprehension is strong: in both testing rounds, users/personas correctly identified the feature's purpose unprompted and indicated they'd change behavior based on it.
- Trust in the underlying number is a hard gate, not just friction, for at least one user type: Amara (Round 2) stated flatly she would not act on a recommendation she couldn't verify.
- Judgmental or lecturing framing repels skeptical, previously-churned users: Tom (Round 2) read the insight as "another guilt trip," consistent with why he'd abandoned three prior budgeting apps.
- A visible reward/streak mechanic was explicitly requested and well received in concept (Round 1 interview: "more interactive, more rewards").
- An empty state and a broken/missing state are indistinguishable to a user who expects data to already be there — Priya's reaction to the (deliberately scripted) no-goal empty state was confusion and a trust hit, not an invitation.
- The weekly summary's retention effect operates primarily through goal-setting conversion, not abstract "engagement" — treatment users set a goal within week 1 at roughly double the rate of control (44% vs. 22%), which is the single strongest lever in the dataset ([data/metric-diagnosis.md](../data/metric-diagnosis.md)).
- Engagement with the summary (opening it, acting on it) does not by itself predict retention — churned treatment users opened and acted on sends at equal-or-higher rates than retained treatment users, meaning whatever ultimately drives their churn happens downstream of interacting with the nudge, not from ignoring it.
- A platform-correlated retention gap (iOS > Android > web) exists both inside and outside the treatment group, at similar magnitude, despite near-equal open rates across platforms — this predates the summary and isn't something it currently addresses.

## What We Assume

- That closing the gap between the first aha moment and a deeper personalized payoff (which currently takes ~3 months to arrive organically) will meaningfully move 30-day retention — inferred from qualitative research, not yet measured.
- That a weekly cadence is the right frequency for this touchpoint — not tested against alternatives (daily, biweekly, event-triggered).
- That the specific feature shape (one insight + one nudge + goal progress) is right — validated for comprehension in a single sitting, not for sustained engagement across multiple weeks.
- That fixing trust/verifiability and adding a reward mechanic will meaningfully reduce the "no reason to return" complaint — plausible from testing reactions, not yet measured behaviorally.
- That the streak/reward mechanic won't itself go stale the way Cleo's roast feature did — an open risk we've named but not tested over time.
- That real users will behave similarly to the simulated Priya/Tom/Amara personas used in Round 2 — a useful proxy for early direction-setting, not a substitute for real user testing.

## What We Still Don't Know

- Whether this feature changes real behavior over multiple weeks — every test so far captures a single-session reaction, not repeated use.
- Whether a "has-goal" experience works, since every round to date has tested only the no-goal scripted scenario (flagged as an open test-coverage gap after Round 2).
- What the actual entry point/trigger should be — the weak re-engagement trigger friction point from Round 1 remains untested in any round; the streak badge is only a partial mitigation.
- Whether transaction-level transparency is sufficient to earn trust for users like Amara, or whether more (category-level detail, multi-week trends) is needed.
- Whether expanding insight categories — a repeatedly requested want — can be done without reintroducing the "irrelevant nudge" opt-out problem NPS already flagged.
- ~~Actual quantitative impact on 30-day retention~~ — **now partially answered**: a week-5 experiment (50 summary_v1 vs. 50 control) showed 76% vs. 46% day-7 retention and 36% vs. 22% day-30 retention (see [data/metric-findings.md](../data/metric-findings.md)). Still open: whether this holds up across more cohorts and a longer time horizon than the single 4-week window tested so far.
- How this experience should relate to users who already have a parallel system elsewhere (Amara's spreadsheet) — replace, supplement, or something else is unresolved.
- Whether the platform-correlated retention gap (iOS vs. Android vs. web) is a fixable technical/UX issue or a fixed population difference the feature can't reach — flagged as the top candidate for next-sprint investigation in [data/metric-diagnosis.md](../data/metric-diagnosis.md), not yet root-caused.

## How the Hypothesis Changes

**Original hypothesis** (see [strategy.md](../strategy.md)): users go passive because the app stops feeling relevant after the first week; a personalized weekly summary (insight + nudge + goal progress) should close that gap.

Usability testing — both the real interview (Round 1) and the simulated persona playtest (Round 2) — does not overturn this hypothesis, but sharpens it in three ways:

1. **Relevance alone isn't sufficient — it has to be verifiable.** The original hypothesis assumed personalization would be trusted because it's personalized. Amara's reaction shows trust requires transparency into the underlying data, not personalization alone. This is now a precondition for adoption, not a nice-to-have.
2. **Delivery framing matters as much as content.** The hypothesis was silent on tone. Tom's reaction shows a correct, relevant insight can still fail if it reads as judgment rather than support — an explicit new constraint on execution, not just on what content to surface.
3. **The engagement mechanic needs its own renewal strategy.** Competitive research already flagged that personalization can go stale (Cleo); the Round 1 interview independently arrived at the same conclusion by asking for "more rewards." The hypothesis now needs an explicit sub-claim: recurring value requires a mechanic that itself doesn't become repetitive. The streak/reward addition is a first attempt, not a proven solution.

Testing also surfaced a **state-design risk the hypothesis didn't anticipate**: for users who already have a goal or history with the product, showing a universal onboarding-style empty state — rather than reflecting their real state — actively damages trust instead of nudging them. The current prototype's "one experience for everyone" assumption is likely too narrow; the feature probably needs to branch by user state rather than present a single screen.

**Net assessment**: the core hypothesis — that closing the post-aha gap with something personalized and recurring should recover retention — still holds, and is now reinforced by two rounds of testing. It needs three additions before being treated as validated: (1) trust/verifiability as a requirement, not an enhancement, (2) tone/framing as an explicit design constraint, and (3) a plan for the mechanic to stay fresh over time — plus closing the test-coverage gap (a has-goal variant) before drawing firmer conclusions.

The resulting updated hypothesis has been formally recorded in [strategy.md](../strategy.md)'s Hypothesis section, alongside the original for comparison. That file is the single source of truth for the current hypothesis wording going forward — this document stays the reasoning and evidence behind the update, not a second copy of the statement itself.
