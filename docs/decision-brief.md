# Decision Brief: Engage v2 — Recovering the Retention Drop

Prepared for: Marcus (Head of Product)

## Situation

30-day retention has dropped from 44% to 37% over the last two quarters: users are consistently engaged by their first spending breakdown, but a large share go passive shortly after and never come back. Discovery across user interviews, NPS feedback, and competitive research all points to the same root cause — nothing in the current experience gives users a reason to return after week one.

## Key Findings

- **The first aha moment isn't the problem — the silence after it is.** Interviewed users (churned and new alike) described the initial spending breakdown positively; the drop-off happens after, not because of, a weak first impression. ([research/interview-synthesis.md](../research/interview-synthesis.md))
- **A real personalized payoff exists, but arrives too late.** Our most retained user described the app finally "knowing" her habits — but only after ~3 months of organic use, far longer than churned/struggling users stick around. ([research/interview-synthesis.md](../research/interview-synthesis.md))
- **NPS confirms this at scale.** The single most common complaint (4 of 10 comments) is a static, repetitive experience with nothing new to discover; savings goals are set once and then never mentioned again, undercutting our own known retention driver. ([research/nps-analysis.md](../research/nps-analysis.md))
- **No competitor owns this space.** Across YNAB, Monarch Money, Rocket Money, Copilot Money, and Cleo, none combine deep personalization with a low-effort, passive experience, and none treat goal progress as a recurring touchpoint rather than a one-time setup step. ([research/competitive-matrix.md](../research/competitive-matrix.md))
- **Personalization alone isn't sufficient — it has to stay fresh.** Cleo is the one competitor that tried a passive, personalized engagement mechanic (its AI "roast" feature), and real user sentiment shows it loses its pull within about a month once it starts repeating — a direct cautionary parallel to our own static-feed problem.

## Options Considered

1. **Personalized weekly in-app summary** (Lena's concept): a recurring screen surfacing one personal insight, one actionable nudge, and savings goal progress. Directly targets the identified gap; Raj confirms it's technically feasible with existing data, requiring new ranking logic only.
2. **Push harder on week-1 goal-setting in onboarding**: since goal-setters already churn at half the rate of non-setters, increasing goal-setting conversion could lift retention without new post-onboarding surfaces.
3. **Make the existing home feed dynamic**: a lighter-weight fix that varies content by recency of use, without introducing a new dedicated screen or ranking system.

## Recommended Action

Build and user-test a prototype of the personalized weekly summary screen, since it's the only option that directly closes the identified gap rather than just improving the funnel that already works.

## Why Now

The retention drop is material (7 points in two quarters) and the underlying cause is now well-evidenced from four independent angles — internal data, user interviews, NPS feedback, and competitive research — reducing the risk of building the wrong thing. The competitive white space is real but not guaranteed to stay open, and the required engineering investment is modest since it uses data Nudge already has.
