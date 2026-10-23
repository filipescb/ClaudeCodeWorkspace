# Codebase Summary — maybe-finance/maybe

Reference repo for Engage v2 spec-writing, explored directly via `gh` CLI. Note: repo is archived/unmaintained — useful as a structural reference only.

## PM Tour

**What it does**: A self-hostable personal finance app (Rails) — connect/track accounts, categorize transactions, budget by category, track net worth, chat with an AI assistant.

**Folder structure**: `app/models/` (domain logic), `app/controllers/` (one per resource), `app/jobs/` (background work — sync, imports, categorization), `app/mailers/` (auth emails only, no digests), `config/schedule.yml` (cron jobs), `db/schema.rb` (source of truth for what data exists).

**3 files to know**:
1. `family.rb` — tenant root; data model is family-first, not user-first.
2. `income_statement.rb` (+ `category_stats.rb`) — cached category-level spend aggregation, medians/averages. Closest existing building block to "what did I spend, is it unusual."
3. `trend.rb` — reusable current-vs-previous comparison object (direction, %, color). Nearly exactly the "+45% vs. usual" logic needed.

**What the data model tells you**: `Entry`/`Account` are polymorphic (handles transactions, valuations, trades / depository, credit card, investment, etc. uniformly) — built for heterogeneous account types from day one. `Budget` is monthly, auto-synced to categories — not a one-time setup. `Rule` shows the team already invested in automation patterns. `Chat`/`Assistant` shows LLM-generated insight already exists, but only on-demand (pull), never pushed. `MobileDevice` registers devices for OAuth only — no push token field.

## Feature Mapping

**Where it'd live**: new `WeeklySummary` model scoped to `Family`, following the `Budget` pattern; new scheduled job in `schedule.yml`; new mailer/notification path (none exists today).

**Depends on**: `IncomeStatement` (category spend), `Trend` (comparison formatting), possibly `BudgetCategory` (if the cap-nudge reuses budgets), and a net-new goal-tracking model (doesn't exist here).

**Blast radius**: bad category aggregation could leak into other screens sharing `IncomeStatement`'s cache; a slow new job could delay other scheduled jobs sharing the `scheduled` queue; writing to `BudgetCategory` directly could silently alter a user's real monthly budget.

## Spec Flags

**Data that doesn't exist yet**: a savings-goal model (nothing here tracks "saving toward $X by date Y"); push notification infrastructure (no device tokens, no APNs/FCM); a defined "typical week" baseline to compare against.

**Constraints to call out**: category aggregation is cached and keyed off `entries_cache_version` — new aggregation should follow this, not invent a parallel scheme; scheduled jobs share one Sidekiq queue.

**The question to answer before kickoff**: is the dining-cap nudge a `BudgetCategory` edit (fast, but couples it to the user's real budget) or a separate concept (slower, safer)? This is a real fork in implementation approach, not a detail.
