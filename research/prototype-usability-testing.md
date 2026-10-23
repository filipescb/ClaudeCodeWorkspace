# Prototype Usability Testing — Engage v2

Consolidated log of usability testing rounds run against [prototype/index.html](../prototype/index.html) (the personalized weekly summary prototype). Each round's findings, the resulting change, and reasoning are also logged individually in [change_log.md](../change_log.md); this file gathers them in one place for reference.

## Round 1: Interview Feedback

Single interviewee, asked to react to the prototype cold.

**Q&A:**
1. *What do you think this does?* — "Tracks personal expenses and helps signalling trends that will steer way from saving money, allows to set cap for types of expenses like dining, and helps you track your savings towards a goal."
2. *How would you arrive at this experience?* — "Opening an app."
3. *Would you change your spending based on this?* — "Yes, maybe reduce dining expenditure."
4. *If you had a magic wand, what would you change?* — "More interactive, more rewards, more insights in other categories."

**What was working:**
- Instant, unprompted comprehension of the feature's purpose (trend signaling, category caps, goal tracking) without explanation.
- Directional behavior change: the interviewee said they'd actually reduce dining spend based on the insight.

**Top 2 friction points:**
1. **Weak re-engagement trigger** — the answer to "how would you arrive here" was generic ("opening an app"), with no distinctive pull or reason to return.
2. **No reward loop after action** — the magic-wand answer wanted more interactivity and rewards, suggesting completing an action (setting the cap) currently feels like a dead end. "More insights in other categories" was a related, lower-priority want — treated as lower priority since expanding categories risks reintroducing the "irrelevant nudge" opt-out problem already flagged in NPS feedback.

**Highest-priority change made**: Added a streak/reward badge — shown on the dining-cap confirmation screen and persistently on the summary header once a nudge is acted on. Chosen over adding more insight categories because it directly answers "more interactive/rewards" without diluting the single-insight focus NPS validated, and it partially addresses friction #1 by giving users a concrete reason to return next week.

**Status**: Not yet re-tested with real users after this change. Friction #1 (weak re-engagement trigger) remains only partially mitigated.

## Round 2: Persona Playtest (Priya / Tom / Amara, simulated)

Simulated in-character reactions using the three interview personas from [interview-synthesis.md](interview-synthesis.md), tested against the updated prototype (post streak/reward change).

**Priya** (power user, has a Europe trip goal, motivated by progress, anxious about surprise totals):
- Recognized the recap/insight/nudge purpose immediately, but was confused and unsettled that her (per-profile) existing savings goal wasn't reflected — the empty state read as "the app forgot" rather than an invitation.
- Would act on the dining cap; the $187 figure "stings a little."
- Magic wand: wants her goal restored and more than one category of insight.

**Tom** (churned-type, abandoned 3 budgeting apps, guilt-averse, skeptical):
- Read the insight as judgmental ("telling me what I already feel bad about"), consistent with why he abandoned prior apps.
- No intrinsic reason to open the app absent an external push — matches his real behavior (hasn't opened Nudge since day one).
- Magic wand: wants the app to *do* something for him, not just flag failure.

**Amara** (high trust bar, already has her own spreadsheet system, checks accounts regularly):
- Understood the screen correctly but stated she would not act on the $120 cap recommendation without verifying the $187 figure against her own tracking first.
- Magic wand: wants to see the underlying transactions, and considers one category insufficient to replace her existing system.

**Synthesis:**
- **What each struggled with**: Priya hit a trust-breaking data mismatch (goal missing); Tom experienced the exact judgmental framing that drove him off prior apps; Amara had no basis to trust an unverifiable aggregate number.
- **What was surprising**: the empty goal state — built specifically to fix the NPS "goal forgotten" complaint — became a *new* trust problem for a persona who already has a goal. An empty state and a broken state look identical to a user who expected data to be there.
- **Most concerning answer**: Amara's. Tom's cynicism is the expected baseline for his persona type. Priya's issue is specific to this test's scripted no-goal scenario. Amara represents a real adoption cliff — a highly engaged, organized user stating flatly she won't act without verification. That's an immediate non-adoption risk, not just friction.

**Highest-priority change made**: Added an expandable transaction list under the top insight ("See what's behind this →"), showing the individual transactions ($22 + $18 + $42 + $64 + $41 = $187) making up the reported figure. Directly addresses Amara's stated blocker; secondarily helps Tom, since a claim backed by visible receipts reads more like a fact than a lecture.

**Not fixed, flagged for a future round**: Priya's goal-state mismatch. The prototype was deliberately scripted for a no-goal persona (per the original PM brief); testing a user like Priya properly requires a "has-goal" variant of the prototype, not a change to current logic.

## Open Issues Carried Forward

- **"Has-goal" prototype variant** needed to properly test users who, like Priya, already have an active savings goal.
- **Weak re-engagement trigger** (Round 1, friction #1) remains only partially mitigated by the streak badge — no round has yet tested an actual notification/entry-point design.
