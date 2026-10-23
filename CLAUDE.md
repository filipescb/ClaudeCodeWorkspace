# CLAUDE.md

Project context for Claude Code when working in this repository.

**Note**: This is a fictional scenario used for a course exercise (AI/Claude Code training). Nudge, its people, and its numbers are not real. Treat it as a realistic simulation, not an actual job or company.

## Summary

Nudge is a consumer personal finance app. I'm the PM for the Engage squad, working on Engage v2 to address a 7-point drop in 30-day retention (44% → 37%). Currently in the discovery phase. Full details live in the working files below — this file should stay a lean index, not a duplicate.

## Key Tension

Momentum toward a specific solution (Lena's weekly summary concept) vs. staying genuinely open until discovery data (user feedback, competitive intel, etc.) comes in. Marcus explicitly wants problem alignment before solution design. Discovery research has since converged on this direction (see [docs/decision-brief.md](docs/decision-brief.md)), and a working prototype now exists and has been through two rounds of testing — the tension has shifted from "should we commit to this direction" toward "does this specific execution hold up," per [strategy.md](strategy.md).

## Open / TBD

The following are intentionally undecided and should not be assumed or invented:
- **Primary open decision** — not yet identified; whether one of the items below is the immediate priority, or all are genuinely parallel, is unresolved
- **Timeline** — not a current priority/constraint
- **Sign-off** — who needs to approve the discovery output, and on what specifically, will be defined as the process progresses

When work touches these open items, treat them as TBD rather than assuming specifics. As items resolve, move them to change_log.md and remove them from this list.

## Working Files

- [project.md](project.md) — what Nudge is, squad, current phase, key stakeholders
- [strategy.md](strategy.md) — hypothesis and direction for recovering the retention drop
- [change_log.md](change_log.md) — audit trail of decisions made as we build (newest first)
- [research/interview-synthesis.md](research/interview-synthesis.md) — synthesis of user interviews (themes, quotes, tensions, key insight)
- [research/nps-analysis.md](research/nps-analysis.md) — NPS feedback analysis (themes, praise/complaints, top actionable issues)
- [research/competitive-matrix.md](research/competitive-matrix.md) — competitor comparison and white-space analysis
- [research/competitive-reddit.md](research/competitive-reddit.md) — real-user sentiment on competitors; validates/refines white-space gaps
- [docs/decision-brief.md](docs/decision-brief.md) — 1-page decision brief for Marcus synthesizing all discovery research
- [docs/pm-brief.md](docs/pm-brief.md) — PM brief for the weekly summary prototype (user, JTBD, feature, constraint)
- [prototype/index.html](prototype/index.html) — interactive click-through prototype of the personalized weekly summary
- [prototype/README.md](prototype/README.md) — prototype brief + key decisions made while building it
- [research/prototype-usability-testing.md](research/prototype-usability-testing.md) — consolidated log of both usability testing rounds run against the prototype
- [docs/hypothesis.md](docs/hypothesis.md) — learning synthesis (know/assume/don't know) and the resulting hypothesis update
- [docs/triad-session.md](docs/triad-session.md) — agenda, post-session alignment template, and invite for the Raj/Lena prototype review session
- [stakeholders/raj.md](stakeholders/raj.md), [stakeholders/lena.md](stakeholders/lena.md), [stakeholders/marcus.md](stakeholders/marcus.md) — stakeholder profiles (workspace facts + flagged default-profile inferences)
- [docs/design-review.md](docs/design-review.md) — Lena design review prep: research crosswalk, roleplay findings, highest-impact gap
- [docs/qa-checklist.md](docs/qa-checklist.md) — edge case list, PM QA pass against the prototype, and first PR comment for Raj
- [docs/spec-readiness.md](docs/spec-readiness.md) — synthesized spec readiness (solid vs. unresolved gaps), consolidating findings from the interrupted Raj roleplay, design review, and QA checklist
- [data/metric-findings.md](data/metric-findings.md) — week-5 experiment results (SQL + findings): retention and open-rate lift, treatment vs. control
- [data/metric-diagnosis.md](data/metric-diagnosis.md) — root-cause diagnosis: metric tree, weeks 1-4 decline drivers, treatment mechanism, ranked churn hypotheses

**Standing instruction**: proactively prompt the user to update the relevant file(s) whenever the conversation produces new information that belongs in one of them (or in any similar file created later) — new decisions → change_log.md, shifts in stakeholders/phase → project.md, hypothesis changes → strategy.md. Ask before writing; don't write silently.

**Formatting instruction**: in any text meant to be pasted elsewhere (Slack messages, emails, other external copy), use a plain hyphen `-` instead of an em dash `—`.
