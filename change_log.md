# Change Log — Engage v2

Audit trail of decisions made as we build. Newest entries at the top.

Format: `## YYYY-MM-DD — Decision title` followed by what was decided, who was involved, and why.

---

## 2026-08-08 — Root-cause diagnosis of retention metrics

**Decision**: Run a full diagnosis on top of the week-5 experiment data — a metric tree decomposing 30-day retention, specific (not generic) causes of the weeks 1-4 decline, the mechanism behind the summary's treatment effect, and 4 ranked, confidence-scored hypotheses for why 64% of treatment users still churned. Saved to [data/metric-diagnosis.md](data/metric-diagnosis.md); key findings folded into strategy.md (Quantitative Evidence section) and docs/hypothesis.md.

**Who**: Me.

**Why**: The week-5 findings showed treatment worked, but not why or where its limits are. Diagnosis found: (1) the weeks 1-4 decline is driven by eroding session frequency and a week-4-specific nudge-engagement collapse, not by declining goal-setting; (2) the summary's effect operates primarily by doubling week-1 goal-setting conversion (44% vs. 22%), not vague engagement; (3) among treatment churners, engagement itself isn't the problem (churners opened/acted at equal-or-higher rates than retainers) — a pre-existing platform gap (iOS 47.8% vs. Android 27.3%, despite equal open rates) and a paid-acquisition gap are the best-supported explanations, while the intuitive "no goal set" explanation is directly contradicted by near-identical rates (43.8% vs. 44.4%).

**Status**: Diagnosis complete; the platform gap is flagged as the top candidate for next-sprint investigation (largest reachable population, cheapest to test further) but not yet root-caused as fixable vs. structural.

---

## 2026-08-08 — First quantitative evidence: week-5 experiment results

**Decision**: Pull and analyze the week-5 summary_v1 vs. control experiment data (5 tables from the Nudge Dataset Google Sheet), and fold the results into strategy.md (new "Quantitative Evidence" section) and docs/hypothesis.md (closing the "no quantitative impact" gap). Saved to [data/metric-findings.md](data/metric-findings.md).

**Who**: Me.

**Why**: Everything in this project up to this point was qualitative (interviews, NPS, competitive research, prototype testing). This is the first real behavioral data: treatment retained 76% vs. 46% at day 7 and 36% vs. 22% at day 30 versus control, and weekly summary open rate rose 28%→56% across 4 sends for treatment while control stayed flat at 4-6%. This directly answers Marcus's known question about retention impact and counters the "engagement mechanic may go stale" risk flagged from the Cleo competitive comparison, at least within the 4-week window tested.

**Status**: Strong, directionally clear result from a single 50-vs-50 cohort over 4 weeks. Not yet confirmed to replicate across additional cohorts or hold beyond week 4 — flagged as the residual open question in both updated files.

---

## 2026-08-08 — Formatting standard added; Slack draft moved out of spec-readiness.md

**Decision**: Added a standing instruction to CLAUDE.md — use a plain hyphen `-` instead of an em dash `—` in any text meant to be pasted elsewhere (Slack messages, emails, other external copy). Also removed the drafted Raj Slack message from [docs/spec-readiness.md](docs/spec-readiness.md); it's now delivered in-chat only rather than stored in the file.

**Who**: Me, per explicit request.

**Why**: Wanted the dash substitution applied consistently to all future paste-ready text, and preferred the Slack draft not live permanently in the spec doc.

**Status**: Applied. No content or findings changed — this is a formatting/organization decision only.

---

## 2026-08-08 — Spec readiness consolidated

**Decision**: Produce [docs/spec-readiness.md](docs/spec-readiness.md), consolidating spec-readiness findings from the interrupted Raj roleplay, the design review, the QA checklist, and the reference codebase check into a single assessment.

**Who**: Me.

**Why**: An earlier Raj roleplay was started but never finished (no answers to his two questions — definition of done, success metric). Rather than re-run that exchange, subsequent work had already independently surfaced most of the same gaps (and several new ones), so consolidating what's actually known was more useful than simulating dialogue.

**Status**: 4 solid points identified; 8 unresolved gaps, including the still-open Marcus approval contradiction and Raj's two original questions, neither of which has an answer anywhere in current materials. A draft Slack message to Raj is included in the doc but not yet sent.

---

## 2026-08-08 — QA checklist run against prototype; 3 blocking gaps found

**Decision**: Run a PM-level QA pass against [prototype/index.html](prototype/index.html) and produce a comprehensive edge-case list, saved to [docs/qa-checklist.md](docs/qa-checklist.md).

**Who**: Me.

**Why**: Feature is heading into QA. The pass found 3 blocking gaps (no zero-transaction/empty-data state, no accessible/keyboard-navigable interactive elements, no fallback for an undefined "typical week" baseline) and 2 items that can't be resolved from a static prototype at all (real data-write integrity, validated non-judgmental copy tone) and need answers in the real spec instead.

**Status**: Findings ready to raise with Raj (draft PR comment included in the doc) — not yet actually posted or discussed with him. Reinforces the still-open spec gaps from the unfinished Raj spec-readiness exchange (`docs/spec-readiness.md` was never completed).

---

## 2026-08-08 — Design review prep completed for Lena

**Decision**: Produce a research-vs-prototype crosswalk and a simulated design-review roleplay to prepare for the upcoming Lena review, saved to [docs/design-review.md](docs/design-review.md).

**Who**: Me.

**Why**: The roleplay surfaced that every round of testing to date (real interview, persona playtest) has only captured single-session comprehension — no evidence yet on repeat-week value, copy tone durability, or whether the streak badge actually drives return behavior. This confirms the re-engagement trigger as the single highest-impact open gap, since it's the one thing common to both at-risk personas (Tom, Amara).

**Status**: Prep complete; review with Lena not yet held. No new finding beyond what's already in [docs/hypothesis.md](docs/hypothesis.md) — this reinforces rather than changes the existing "what we still don't know" list.

---

## 2026-08-08 — Stakeholder profiles created (Raj, Lena, Marcus)

**Decision**: Create [stakeholders/raj.md](stakeholders/raj.md), [stakeholders/lena.md](stakeholders/lena.md), and [stakeholders/marcus.md](stakeholders/marcus.md), combining confirmed workspace facts with default-profile assumptions, clearly labeled by source.

**Who**: Me.

**Why**: Needed a per-stakeholder reference for how each pushes back, what evidence they need, and what's unresolved, ahead of upcoming conversations (triad session, Marcus decision routing).

**Status**: Two contradictions were flagged during creation and explicitly deferred by request ("let's take that later"):
1. `docs/pm-brief.md` and `prototype/README.md` both state "the decision Marcus approved," while this change_log's own record says "awaiting Marcus's decision" — unresolved.
2. The default profile claims Marcus asked for a rollout timeline, which conflicts with this file's Open/TBD note that timeline is "not a current priority." Unresolved — CLAUDE.md's Open/TBD list has intentionally not been changed until this is clarified.

---

## 2026-08-08 — Triad review session scoped

**Decision**: Prepare a 30-minute working session with Raj and Lena to walk through the prototype and both usability testing rounds, get eng/design feasibility input on the open gaps (has-goal variant, transaction-detail availability, re-engagement trigger, tone rework, mechanic freshness), and scope the next prototype iteration.

**Who**: Me.

**Why**: Solo iteration on the prototype has reached the point where the open gaps identified in [docs/hypothesis.md](docs/hypothesis.md) need eng feasibility input (Raj) and design system input (Lena) before further iteration — this moves the work from solo prototyping to triad alignment.

**Status**: Session materials prepared ([docs/triad-session.md](docs/triad-session.md)); session not yet held. Outcome will determine next prototype scope and whether this routes back to Marcus as an update to the decision brief.

**Decision**: Update the Hypothesis section in strategy.md. The core mechanism (close the post-aha gap with something personal and recurring) is unchanged, but trust/verifiability, tone/framing, mechanic freshness over time, and state-branching (has-goal vs. no-goal) are now treated as preconditions for that mechanism to work, not later refinements.

**Who**: Me, based on a learning synthesis (see [docs/hypothesis.md](docs/hypothesis.md)) of change_log.md, docs/decision-brief.md, and both prototype usability testing rounds (one real interview, one simulated agent persona playtest).

**Why**: Both testing rounds converged on the same underlying pattern — personalization and recurrence alone aren't enough. Amara's refusal to act on an unverifiable number, Tom's reading of the insight as judgmental, and Priya's negative reaction to a state that didn't reflect her real goal status all point to specific, addressable gaps in the original hypothesis rather than reasons to abandon it.

**Status**: Hypothesis refined, not overturned. See [strategy.md](strategy.md) and [docs/hypothesis.md](docs/hypothesis.md).

---

## 2026-08-08 — Usability testing consolidated into one file

**Decision**: Create [research/prototype-usability-testing.md](research/prototype-usability-testing.md), consolidating the Round 1 interview feedback and Round 2 persona playtest (previously only captured as individual change_log entries) into a single reference document.

**Who**: Me.

**Why**: Testing findings, friction points, and the reasoning behind each resulting prototype change were dispersed across multiple change_log entries, making it harder to see the full testing history in one place.

**Status**: Reference document only; no new findings. See [research/prototype-usability-testing.md](research/prototype-usability-testing.md).

---

## 2026-08-08 — Persona playtest (Priya/Tom/Amara); transaction transparency added

**Decision**: Add an expandable transaction list under the top insight ("See what's behind this →"), showing the individual transactions ($22 + $18 + $42 + $64 + $41 = $187) that make up the reported figure. Also flagged, but did not fix, a goal-state mismatch for Priya's persona.

**Who**: Me, based on a simulated 3-persona playtest (Priya, Tom, Amara) against the existing prototype.

**Why**: Amara (high-trust-bar, already has her own spreadsheet system) stated she will not act on a recommendation from a number she can't verify — the clearest non-adoption risk surfaced across all three personas, since it's a hard "won't use it" rather than friction. Making the $187 figure expandable into real transactions addresses this directly, and secondarily helps Tom, for whom an unverifiable claim reads more like a lecture than a fact. Priya's reaction — confusion that her (per-profile) existing Europe trip goal wasn't reflected, seeing the empty-state instead — was not fixed, since the prototype was deliberately scripted for a no-goal persona; this is logged as a gap in test coverage (need a "has-goal" variant of the prototype for a future round), not a defect in current logic.

**Status**: Prototype updated ([prototype/index.html](prototype/index.html)); not yet re-tested with users. Two things remain open: (1) a "has-goal" variant of the prototype for testing users like Priya, (2) the weak re-engagement trigger friction point flagged in the previous round, still only partially mitigated by the streak badge.

---

## 2026-08-08 — First user-test round on prototype; streak/reward added

**Decision**: Add a streak/reward badge to the prototype (shown on the cap-confirmation screen and persistently on the summary header once a nudge is acted on), rather than expanding the number of insight categories shown.

**Who**: Me, based on 1 interview round.

**Why**: Interviewee correctly identified the feature's purpose unprompted and said they'd change behavior based on it (reduce dining spend) — confirming comprehension and directional effectiveness. Two friction points surfaced: (1) asked how they'd arrive at this experience, the answer was just "opening an app," a vague, non-distinctive trigger; (2) the "magic wand" answer wanted "more interactive, more rewards, more insights in other categories." Chose the reward/streak mechanic as the single highest-priority fix because it directly answers "more interactive/more rewards" with the lowest risk — it doesn't dilute the single-insight focus NPS already validated (more categories risks reintroducing the "irrelevant nudge" opt-out problem from NPS #4), and a visible streak also starts to address friction #1 by giving users a concrete reason to return next week.

**Status**: Prototype updated ([prototype/index.html](prototype/index.html)); not yet re-tested with users. Friction point #1 (weak re-engagement trigger) remains open for a future round — the streak badge is a partial mitigation, not a full fix.

---

## 2026-08-08 — Decision brief for Marcus produced

**Decision**: Synthesize all discovery research (user interviews, NPS analysis, competitive matrix, competitive sentiment) into a 1-page decision brief for Marcus, recommending prototyping and user-testing the personalized weekly summary screen.

**Who**: Me.

**Why**: Discovery has converged from four independent angles on the same root cause — nothing pulls users back after the first aha moment — making this the point to bring a recommendation to Marcus rather than continue gathering evidence.

**Status**: Recommendation made; awaiting Marcus's decision. See [docs/decision-brief.md](docs/decision-brief.md).

---

## 2026-08-08 — Competitive sentiment analysis synthesized; freshness constraint added

**Decision**: Fold real-user sentiment findings (see [research/competitive-reddit.md](research/competitive-reddit.md)) into strategy.md, refining the competitive white-space gaps.

**Who**: Me.

**Why**: Cleo attempted the same kind of passive, personalized engagement mechanic being explored for Nudge (its "roast me" AI feature), and real user feedback shows it goes stale within about a month — validating Gap 1 but adding a new constraint that content must stay fresh over time, not just be personalized once. Gap 2 (goal continuity) was not contradicted but also wasn't directly confirmed by this data, so confidence there is lower than Gap 1.

**Status**: Refines existing hypothesis and direction; not a pivot. Data caveat: search tool could not pull direct, browsable Reddit threads — findings draw on review sites and secondary sources referencing user sentiment, treated as directional rather than systematic. See [strategy.md](strategy.md).

---

## 2026-08-08 — Competitive analysis synthesized; white space identified

**Decision**: Fold competitive white-space findings (5 competitors: YNAB, Monarch Money, Rocket Money, Copilot Money, Cleo — see [research/competitive-matrix.md](research/competitive-matrix.md)) into strategy.md as a new "Competitive White Space" section.

**Who**: Me.

**Why**: No competitor combines deep personalization with a low-effort/passive experience, and no competitor treats goal continuity as a recurring, first-class touchpoint. Both gaps independently point at the weekly summary direction already being explored, adding external market evidence on top of the internal data and user research already gathered.

**Status**: Reinforces hypothesis and existing direction; not a pivot. See [strategy.md](strategy.md).

---

## 2026-08-08 — NPS analysis synthesized; two new constraints identified

**Decision**: Incorporate NPS findings into strategy.md as supporting signals and as explicit constraints on the weekly summary direction (goal continuity, nudge relevance).

**Who**: Me.

**Why**: The goal-mention gap and notification opt-out both surfaced independently in raw user feedback, not just interviews — increasing confidence these are real issues, not isolated complaints. A user disabling notifications after one low-value nudge is a direct risk to any new recurring touchpoint if relevance isn't addressed first.

**Status**: Reinforces hypothesis; adds design constraints, not a pivot. See [strategy.md](strategy.md) and [research/nps-analysis.md](research/nps-analysis.md).

---

## 2026-08-08 — User interviews synthesized; hypothesis sharpened

**Decision**: Treat the 3-user interview synthesis (Priya, Tom, Amara — see [research/interview-synthesis.md](research/interview-synthesis.md)) as supporting evidence for the Engage v2 hypothesis, and incorporate its core finding into strategy.md.

**Who**: Me.

**Why**: Interviews showed the first aha moment (spending breakdown) is well received across a power user, a churned user, and a new user — the drop-off happens after it, not because of it. The power user's deeper payoff (personalized pattern recognition) took ~3 months to arrive organically, longer than churned/struggling users stuck around. This sharpens the hypothesis: the gap to close is between the first and second aha moments, not the first moment itself.

**Status**: Reinforces existing hypothesis; direction still not validated with users. See [strategy.md](strategy.md).

---

## 2026-08-08 — Align on problem before designing solutions

**Decision**: Before exploring any solution (including Lena's personalized weekly summary concept), write up the problem statement to confirm the team is aligned on what we're solving, ahead of Thursday's meeting.

**Who**: Marcus (requested), full triad.

**Why**: Marcus wants confirmation the team is aligned on the problem before solutioning begins.

---

## 2026-08-08 — Working hypothesis for retention drop

**Decision**: Adopt the working hypothesis that users go passive because the app stops feeling relevant after the first week's "aha moment," and that there's currently nothing that pulls users back with a reason specific to their own behavior.

**Who**: Raj, Lena, me — surfaced in #product-engage thread.

**Why**: Supported by data (week-1 savings goal setup correlates with retention), user research (no clear next step after dashboard), and product observation (static home feed, email/app handoff gap).

**Status**: Direction only, not yet validated with users. See [strategy.md](strategy.md).
