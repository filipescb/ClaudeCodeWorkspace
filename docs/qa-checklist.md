# QA Checklist — Weekly Summary Feature

Prepared against [prototype/index.html](../prototype/index.html) and [prototype/README.md](../prototype/README.md). Re-run after [docs/spec-readiness.md](spec-readiness.md) was produced — findings below are unchanged (the prototype hasn't changed), and are consistent with spec-readiness.md's "Needed Work" list, which was itself partly built from this checklist. No finalized eng spec exists yet, so several items below remain "cannot determine" until the spec answers them.

## 1. Edge Case List

### Empty States
- No transactions at all this week (the account is connected but unused, or user is in a genuinely quiet week)
- No savings goal set (prototype's default scripted state — already designed for)
- No app sessions in the past week (does "this week" mean calendar week, or since-last-open? Ambiguous today)
- Zero categories with any spend (fully inactive account)
- Account connected mid-week — only a partial week of data exists

### Edge Data Conditions
- Single transaction only in the flagged category — is a 45%-style comparison meaningful or misleading with n=1?
- Duplicate/overlapping categories (e.g., "Dining" and "Restaurants" both exist) — which absorbs the aggregate?
- Zero-amount transactions (authorization holds, refunds that net to $0)
- Negative amounts (refunds/credits exceeding spend) — could make a category total negative; unclear how that should render
- One outsized transaction skewing the comparison (e.g., a $2,000 miscategorized purchase inflating "dining")
- Pending vs. posted transactions — does the weekly total include pending, and what happens if a pending amount changes later?
- A category with real spending history but literally $0 this week — is that "-100%," and does that read sensibly?
- A brand-new category with no prior history — "usual" baseline is undefined, not just zero

### Multi-Account Scenarios
- Multiple banks connected — does the insight aggregate across all accounts or per-account? Undefined today.
- Transfers/payments between a user's own linked accounts double-counted as spend
- One newly connected account (thin history) alongside an older account — skews the "typical" baseline
- An account disconnected or requiring re-auth mid-week — creates a data gap for that week
- A joint/shared account — whose "typical" baseline applies?

### Permission States
- Push notifications disabled — if the real re-engagement trigger is a notification, what's the fallback?
- Background app refresh disabled — data shown on open may be stale
- Bank connection revoked/needs re-auth — summary can't be generated; no defined fallback screen
- Goal card promises "we'll check in on this every week" — does that promise silently break if notifications are off?

## 2. PM QA Pass Against prototype/index.html

Screen by screen, the 10 most important things to verify before sign-off:

| # | Check | Result | Blocking / Known Issue |
|---|---|---|---|
| 1 | Transaction list under "See what's behind this" sums to the headline figure ($22+$18+$42+$64+$41 = $187) | **Pass** | — |
| 2 | Tapping "Set a $120 dining cap" gives clear confirmation and updates persistent UI (streak badge) | **Pass** | — |
| 3 | Goal empty state correctly transitions to a filled progress card after goal creation, returning to the right screen | **Pass** | — |
| 4 | A defined empty/zero-data state exists for "no transactions this week" | **Fail** | **Blocking** — the target persona's whole scenario is low/no engagement; shipping without this is a real gap, not an edge case. Tracked in [docs/spec-readiness.md](spec-readiness.md) Needed Work. |
| 5 | The cap action writes back to a real budget/data object correctly | **Cannot determine** | Static JS prototype, no backend — this is the same unresolved implementation fork named in [docs/spec-readiness.md](spec-readiness.md) (budget object vs. decoupled concept), not answerable from this file |
| 6 | Insight/nudge copy avoids reading as judgmental (per the design-review finding re: Tom) | **Cannot determine** | This is a user-perception question, not a code check — flagged as untested in `docs/design-review.md`, not something a QA pass against the file can resolve |
| 7 | Back-navigation (‹ Summary) doesn't leave partial/corrupted state if a flow is abandoned | **Pass** | — |
| 8 | Interactive elements are accessible (real buttons/keyboard-navigable, not divs-with-onclick) | **Fail** | **Blocking** — goal-type chips, tab bar, back links, and the transaction-reveal link are all `<div>`s with `onclick`, no keyboard access or ARIA labeling |
| 9 | Streak badge/reward mechanic degrades gracefully when no action has been taken yet | **Pass** | — |
| 10 | A defined fallback exists when the "typical week" baseline is undefined (new user, no history) | **Fail** | **Blocking** — no logic or fallback copy exists for this at all; directly affects the new-user persona this feature targets. Also tracked in [docs/spec-readiness.md](spec-readiness.md) Needed Work. |

**Summary**: 5 pass, 3 fail (all blocking), 2 cannot-determine (need spec/real-data answers, not prototype fixes).

## 3. First PR Comment for Raj

> Question, not a blocker on my end yet — what do we show if a user has $0 (or no transactions at all) in the flagged category this week? Right now the prototype always renders a fixed "+45% vs. usual" example, so I can't tell from the code whether we have a defined fallback for a zero or undefined baseline, or whether the percentage math would just produce something like "-100%" or blow up on a divide-by-zero. Given the target user for this feature is someone with low/no engagement in their first weeks, this feels like a fairly common case rather than a true edge case — want to make sure we've got an answer before this merges, even if the fallback itself is simple.
