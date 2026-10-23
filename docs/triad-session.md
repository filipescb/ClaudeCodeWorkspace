# Triad Working Session: Weekly Summary Prototype

30 minutes — Raj, Lena, me.

## Purpose

Walk the triad through the prototype and two rounds of usability testing, get Raj's and Lena's read on feasibility/design implications of what testing surfaced, and leave with a scoped next iteration.

## Pre-read (share before the session)

- [prototype/index.html](../prototype/index.html) — the prototype itself (5 min to click through)
- [research/prototype-usability-testing.md](../research/prototype-usability-testing.md) — both testing rounds in full
- [docs/hypothesis.md](hypothesis.md) — how testing changed the hypothesis

## Agenda

**1. What to show (10 min)**
- Quick click-through of the prototype's current state: insight card with expandable transactions, dining-cap nudge → confirmation → streak badge, goal empty state → goal-setup flow → progress card.
- One-slide recap of the two testing rounds: what worked (comprehension, directional behavior change), and the three things that surfaced as *preconditions* rather than nice-to-haves — trust/verifiability, tone/framing, and mechanic freshness — plus the state-design gap (empty vs. broken state for users like Priya who already have a goal).

**2. Questions for Raj (eng feasibility) (8 min)**
- How hard is a "has-goal" variant — same screen, but branching on whether the user already has an active goal? Is this a real fork in the data model/logic, or a straightforward conditional render?
- The expandable transaction list assumes transaction-level detail is readily available per insight — is that true today, or does it require new query/aggregation work?
- What would a real entry-point/trigger (push notification or similar) take to prototype and test properly? Rough feasibility, not a timeline commitment.

**3. Questions for Lena (design implications) (8 min)**
- How do we rework insight/nudge copy so it reads as supportive rather than judgmental (Tom's reaction) — is this a copy-only fix or does it need a visual/tone system change?
- Does the streak/reward mechanic need a design system of its own to avoid going stale the way Cleo's did, or can copy variation alone solve it?
- How should the empty-state vs. has-state problem be handled visually — same card with different content, or genuinely different layouts?

**4. Decisions to walk out with (4 min)**
- Which one or two of the four open gaps (verifiability depth, tone rework, mechanic freshness plan, has-goal variant) become the next prototype iteration's scope.
- Whether the re-engagement trigger gets prototyped next round or stays explicitly out of scope for now.
- Whether this is ready to go back to Marcus as an update to the decision brief, or needs one more round first.
- Who owns what for the next iteration (not a timeline — see [CLAUDE.md](../CLAUDE.md) Open/TBD — just next-step ownership).

## Post-Session Alignment Doc (template)

Fill in and save as its own dated file after the session.

---

**Date**: [ ]
**Attendees**: [ ]

**Decisions made**:
- [ ]

**Scope for next prototype iteration**:
- [ ]

**Open questions / not resolved today**:
- [ ]

**Owners / next steps**:
- [ ] — Owner: [ ]

**Routing**: [ Ready for Marcus update / needs another round / other ]

---

## Slack Message (invite)

> Hey Raj, Lena — want to grab 30 min to walk through the weekly summary prototype and what we learned from two rounds of testing (1 real interview, 1 simulated persona playtest). Comprehension and directional behavior change are landing, but testing surfaced a few things I want your read on before we scope the next iteration — trust/verifiability of the insight numbers, tone of the nudge copy, and a state-design gap for users who already have a goal set.
>
> Pre-read if you have 5 min beforehand: [prototype/index.html](../prototype/index.html) (just click through it), and the testing writeup here: [research/prototype-usability-testing.md](../research/prototype-usability-testing.md).
>
> Does [day/time] work for both of you?
