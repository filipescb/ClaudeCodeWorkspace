# Design Review: Weekly Summary Prototype — Prep for Lena

## Research vs. Prototype Crosswalk

Source: [research/interview-synthesis.md](../research/interview-synthesis.md) (Priya, Tom, Amara).

**Addressed well:**
- **Explicit next step, not just data.** Amara: *"I have been waiting for Nudge to tell me the next step."* The prototype gives one nudge card with one concrete action (the $120 dining cap), not a dashboard to interpret.
- **Proactive engagement, not passive display.** Tom: *"I switched to YNAB because at least that feels like it is asking something of me."* The nudge CTA plus the streak mechanic give the app something to actively ask of the user.
- **Non-obvious, personalized insight.** Priya: *"It started surfacing patterns I had not consciously registered — like that I always overspend in the last week of the month."* The dining-spike insight ("+45% vs. usual") is structurally the same kind of pattern-surfacing insight that hooked Priya, delivered in week 1 instead of arriving organically at month 3.

**Not yet addressed:**
- **Sustained, ritual value over time.** Priya: *"It took about three months to get there... I open Nudge every Sunday morning... It has become a ritual."* The prototype is a single-week snapshot; nothing demonstrates or tests whether this insight stays valuable across multiple weeks.
- **Tone risk for skeptical, previously-burned users.** Tom's profile (guilt-averse, abandoned three prior apps) means the current insight copy has not been validated against his specific skepticism — comprehension has been tested, tone has not.
- **A proactive trigger/entry point.** Per the interview synthesis: *"Tom and Amara both want the app to proactively tell them what to do next... Priya's ritual, by contrast, is self-directed."* The prototype has no notification or trigger mechanism — it opens directly to the summary.

## Design Review Roleplay

**Lena's 3 hardest questions:**
1. Priya's ritual took three months to build organically — this prototype is one week. What's the evidence this insight stays valuable in week 4, week 8, not just week 1?
2. Tom said he felt judged by budgeting apps and left three of them. Where's the evidence this exact copy doesn't read like the same guilt trip?
3. What does the user actually do after they read this? They tap the cap button — then what? Do they come back Tuesday, or just close the app?

**Answers given, and Lena's pushback:**
1. *No multi-week evidence exists* — every test so far captured a single-session reaction (documented in `docs/hypothesis.md`). Lena's response: fine to say so, but this can't be presented as solved — need a plan to test repeat-week value.
2. *No copy-specific tone testing has been done* — the evidence we have is that Tom wants proactive prompting, not that this specific phrasing avoids landing as judgmental. Lena's response: comprehension isn't trust; wants copy tested with a Tom-type user before this ships broadly.
3. *The streak badge is the intended "next moment"* — designed to persist as a visible reason to return, but untested: no evidence on whether it works or what day someone would return. Lena's response: a badge is not a re-engagement strategy until it's tested — same underlying gap as Q1.

## Single Highest-Impact Change for Week-1 Retention

Design and test an actual proactive re-engagement trigger (e.g., a notification), not another in-app refinement. Week-1 retention specifically requires pulling a user back within days — the streak badge and improved copy only matter if the user opens the app in the first place, and nothing today does that job. This is also the one gap common to both Tom and Amara, the two personas most at churn risk.

## Product Decision vs. Lena's Call

**Product/PM decision:**
- Whether to invest in notification infrastructure now or defer it
- Whether goal-setting is required or optional for v1
- Whether the cap nudge writes to a real budget object (a tradeoff with engineering, not design)

**Lena's to own:**
- Exact tone/copy of the insight and nudge language
- Visual/interaction design of the streak mechanic
- How the empty-state vs. has-goal-state visually differ
- Design of the notification content itself, once product decides whether to build it
