# Stakeholder: Raj

## Role

- **From workspace**: Senior Engineer, triad member for the Engage squad ([project.md](../project.md)).
- **From default profile**: Framed as "Engineering Lead" — owns technical architecture, sprint scope, and feasibility decisions for the squad.
- ⚠ **Flag**: The workspace consistently calls Raj "Senior Engineer," not "Lead." Functionally he's been the sole engineering voice on this initiative so far, which may be why the default assumes a lead-level role — but the title itself is unconfirmed. Worth checking whether "Lead" is accurate before using it in writing to him or about him.

## What He's Contributed So Far (from workspace)

- Surfaced the data link between week-1 savings goal setup and churn — goal-setters churn at roughly half the rate of non-setters ([strategy.md](../strategy.md), [project.md](../project.md)).
- Surfaced that the home feed doesn't vary by recency of use ([strategy.md](../strategy.md)).
- Assessed the personalized weekly summary concept as technically feasible with existing data sources, requiring new ranking logic to determine which insight to surface ([strategy.md](../strategy.md), [docs/decision-brief.md](../docs/decision-brief.md)).

## Open Items

- **From workspace**: The triad session ([docs/triad-session.md](../docs/triad-session.md)) has a set of feasibility questions queued for Raj — has-goal variant complexity, transaction-detail data availability, and push-notification trigger feasibility — but the session hasn't happened yet, so none of these are answered.
- **From default profile**: Still waiting on data model clarification for the savings goal field. This lines up with an independent finding from exploring a reference codebase ([docs/codebase-summary.md](../docs/codebase-summary.md)) — no savings-goal data model exists there either — so this open item is plausible and worth prioritizing at the triad session, even though it's not yet confirmed as Raj's literal words.

## How to Work With Him (default profile — not yet confirmed in workspace)

- **Pushes back on**: underspecified requirements, scope that grows mid-sprint, anything touching the data pipeline without a clear rollback plan.
- **Needs before saying yes**: clear acceptance criteria, edge cases called out upfront, an explicit definition of "done."
- **Questions he's asked before that went unanswered**: "How will we know if this is working after it ships?" and "What happens if the user has no transactions this week?" — both are real edge cases the current prototype doesn't yet address (no success metric defined, no zero-transaction empty state designed).
- **Communication preference**: async-first, short messages, bullet points over prose; dislikes being surprised in standups.

## One Thing That Would Most Change How You Prepare For Him

He's likely to ask "what happens when there's no data" (zero transactions this week) and "how will we know this worked" — neither has an answer yet. Walk into the triad session with at least a first-pass answer to both, or expect the conversation to stall there instead of moving to feasibility.
