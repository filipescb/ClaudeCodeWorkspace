# Spec Readiness — Weekly Summary Feature

Generated from work completed across discovery, prototyping, design review, and QA — not from a completed live exchange with Raj (that roleplay was started but never finished; see below). This synthesizes what's actually known against the questions Raj would reasonably ask, per [stakeholders/raj.md](../stakeholders/raj.md).

## What Prompted This

An earlier session started a roleplay with Raj reviewing the spec materials. He raised two questions before the exchange was cut short:
1. What does "done" look like for the first ship — which state variants (has-goal/no-goal × has-transactions/no-transactions)?
2. `docs/pm-brief.md` says "the recommendation Marcus approved" — is that accurate, given other records say it's still pending?

Neither was answered in that exchange. Since then, separate work (design review, QA pass, codebase reference check) has independently surfaced most of the same gaps — this doc consolidates all of it.

## Spec Readiness Summary

### Solid
- **Feature concept is clear**: user, job-to-be-done, feature composition (insight + nudge + goal progress), and constraint (existing data only, no new integrations) are all explicitly defined in [docs/pm-brief.md](pm-brief.md).
- **Core interaction flow is prototyped and comprehension-tested**: two rounds of testing (real interview + persona playtest) confirm users understand the feature's purpose and would act on it — see [research/prototype-usability-testing.md](../research/prototype-usability-testing.md).
- **Two real building blocks exist in a comparable reference codebase** (`Trend`, `IncomeStatement` category stats) that reduce general feasibility risk for the comparison/insight logic — see [docs/codebase-summary.md](codebase-summary.md).
- **Design risks have named owners**: tone/copy risk and empty-vs-has-state visual handling are explicitly assigned to Lena, not left ambiguous — see [docs/design-review.md](design-review.md).

### Needed Work (unresolved, blocking a real spec)
- **No definition of "done" for v1.** Which state combinations ship first (has-goal vs. no-goal, has-transactions vs. zero-transaction)? Raj's original question — still unanswered.
- **Approval status contradiction, unresolved.** `docs/pm-brief.md` and `prototype/README.md` state Marcus approved the recommendation; `change_log.md`'s own record says it's still awaiting his decision. Flagged in [stakeholders/marcus.md](../stakeholders/marcus.md), explicitly deferred by request.
- **Three QA-blocking gaps**, from [docs/qa-checklist.md](qa-checklist.md):
  - No defined empty/zero-data state (directly affects the target persona — someone with low/no engagement).
  - No accessible/keyboard-navigable interactive elements.
  - No fallback for an undefined "typical week" baseline (new users with no history).
- **No success metric defined.** Raj's other known question — "how will we know if this is working after it ships" — has no answer anywhere in the current materials.
- **No savings-goal data model confirmed to exist.** Flagged as a gap in the reference codebase; unconfirmed whether Nudge's actual system has one ([docs/codebase-summary.md](codebase-summary.md)).
- **No re-engagement trigger designed or feasible-checked.** The design review identified this as the single highest-impact open gap; no notification infrastructure has been confirmed to exist ([docs/design-review.md](design-review.md)).
- **Unresolved implementation fork**: does the dining-cap nudge write to a real budget object, or does it need its own decoupled concept? Named explicitly in [docs/codebase-summary.md](codebase-summary.md) as a pre-estimation question, not a detail.
- **Copy tone not validated** against a skeptical, previously-churned user type (Tom) — comprehension has been tested, tone has not ([docs/design-review.md](design-review.md)).

## Rewrite: Unclear Sections

**`docs/pm-brief.md` — Grounding section, currently says:**
> "[docs/decision-brief.md](decision-brief.md) — the recommendation Marcus approved"

**Should read** (until the contradiction is actually resolved):
> "[docs/decision-brief.md](decision-brief.md) — the recommendation submitted to Marcus (approval status unconfirmed — see [stakeholders/marcus.md](../stakeholders/marcus.md))"

**New section needed — Definition of Done (does not exist anywhere today):**
> **V1 scope**: [to be filled in — which state combinations ship first]
> **Out of scope for V1**: [to be filled in — e.g., has-goal variant, push notification trigger, if deferred]
> **Success metric**: [to be filled in — what specifically will be measured post-launch to know this worked]

**New section needed — Known Edge Cases (currently scattered across qa-checklist.md, not in the spec itself):**
> Zero-transaction/empty state, undefined "typical week" baseline, accessibility requirements — pull directly from [docs/qa-checklist.md](qa-checklist.md) Section 1 rather than restating.
