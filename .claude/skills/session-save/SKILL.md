---
name: session-save
description: End-of-session hygiene pass for Nudge Engage v2. Reviews what was discussed/decided in the current conversation and proposes updates to project.md, strategy.md, change_log.md, and CLAUDE.md — asking for approval before writing anything. Use when the user types /session-save or asks to wrap up / save session progress.
---

# Session Save

Project-scoped skill for the Nudge Engage v2 project (C:\Users\filip\ClaudeCodeWorkspace).

## What this project's files are for

- `CLAUDE.md` — orientation only: key tension, open decision, project files index, working notes. Never duplicate content that lives in another file.
- `project.md` — what the product is, squad, current phase, stakeholders, problem statement
- `strategy.md` — hypothesis and candidate direction(s)
- `change_log.md` — audit trail of decisions, format: `Date — Decision — Rationale — Owner`, newest entries at top

## Steps

1. Review the session for anything that changes the project's understanding: new facts, hypothesis changes, stakeholder/context updates, or decisions made.
2. Sort findings by destination (facts → project.md, hypothesis/direction → strategy.md, decisions → change_log.md). Anything that doesn't fit — ask before creating a new file.
3. Check CLAUDE.md hygiene — don't duplicate content that now lives elsewhere; only update it if Key Tension/Open Decision/Working Notes/file index actually changed.
4. Present a proposed diff, file by file, before writing anything. Wait for approval.
5. On approval, write the changes, matching each file's existing structure and tone.
6. If nothing warrants an update, say so — don't invent changes to justify the save.
