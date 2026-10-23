# Prototype: Engage v2 — Personalized Weekly Summary

Interactive mobile-app-screen click-through prototype for the personalized weekly summary feature, built on top of the discovery research (see [CLAUDE.md](../CLAUDE.md) working files) and the decision Marcus approved (see [docs/decision-brief.md](../docs/decision-brief.md)).

Open [index.html](index.html) in a browser to view.

## PM Brief

**User**: 28-year-old who connected their Chase account 2 weeks ago and has not opened the app since.

**Job to be done**: understand where their money went this week and take one action.

**Feature**: personalized weekly money summary — top spending insight, one contextual nudge, savings goal progress.

**Constraint**: use data Nudge already has — no new integrations.

Full brief: [docs/pm-brief.md](../docs/pm-brief.md)

## Key Decisions Made During the Interview

- **Persona has no savings goal set** — deliberately chosen as the harder, more common case; research shows goal-skippers churn at roughly double the rate of goal-setters.
- **Entry point**: prototype opens directly to the summary screen — no notification/email trigger simulated.
- **Goal section shown as an empty state**, not omitted or faked — directly answers the NPS complaint that a set goal was "never mentioned again" by making the goal (or lack of one) visible every time.
- **Insight content**: a category-spike insight ("$187 on dining, 45% above typical"), not a generic total — matches the NPS/interview ask for something the user doesn't already know, not a restatement of what they suspect.
- **Nudge content**: a single, specific, actionable suggestion tied directly to the insight above ("cap dining at $120 next week") — deliberately avoids the "random low-value nudge" pattern (NPS #4) that caused a user to disable notifications entirely.
- **Visual format**: mobile phone-frame mockup (not a plain web page), since Nudge is primarily a mobile app.
- **Fidelity**: fuller click-through flow (revised from an initial static-mockup decision) — the dining-cap nudge and the goal CTA are both functional. Tapping "Set a $120 dining cap" leads to a confirmation screen and updates the nudge card's state on return. Tapping "Set your first goal" opens a goal-setup form (type, target amount, target date), which on submit shows a confirmation screen and replaces the summary's empty goal state with a real progress card. This lets user testing validate the actual behavior of the feature, not just its appearance.
- **No new data sources**: all content (spending by category, day-by-day totals, goal status) is data Nudge already collects; no new integrations required, per the constraint in the PM brief. Goal data entered during testing is held only in-browser (JS state), not persisted — appropriate for a prototype with no backend.

## Status

Prototype only — not yet validated with users. Next step per [strategy.md](../strategy.md) is user-testing this concept.
