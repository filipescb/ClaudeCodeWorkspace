# NPS Feedback Analysis — Engage v2

Source: 10 raw NPS comments. Prepared for Marcus.

## Overview

Feedback strongly corroborates the Engage v2 hypothesis: users are engaged by their first experience but find nothing pulling them back afterward. The dominant complaint, by a wide margin, is that the app feels static and repetitive after week one.

## Themes Ranked by Frequency

*(Only themes mentioned in more than one comment are ranked; single-mention issues are called out separately below as they're still actionable.)*

### 1. No reason to return — static, repetitive experience (4 mentions)

- *"I connected my bank, saw my spending was a mess, felt bad, and then just stopped opening the app. Nothing made me want to come back."* (#1)
- *"The home feed shows the same things every time I open it. There is nothing new to discover."* (#7)
- Also present in #2 ("after that it just felt repetitive") and #10 ("the app itself has not given me a reason to open it").

### 2. Wants proactive guidance, not passive data (2 mentions)

- *"I want Nudge to feel like a financial coach, not a spending tracker. Right now it just shows me what happened. I need it to tell me what to do."* (#3)
- *"Love the concept. I just forget it exists. If I got one really useful insight a week I would open it every week."* (#5)

### 3. Doesn't feel personalized — generic content (2 mentions)

- *"Deleted after 3 weeks. The app did not feel like it knew me at all. Just generic money tips I could find anywhere."* (#9)
- *"I wish it would surface things I do not already know about my spending instead of just confirming what I already suspect."* (#8)

## Single-Mention but Actionable

- **Notification relevance (#4)**: *"The nudges feel random. I got a notification that I spent $12 on coffee and I just turned off notifications entirely."* Low-value nudges are actively causing users to opt out of a channel that could otherwise pull them back.
- **Savings goals not followed up on (#6)**: *"I set a savings goal but Nudge has never once mentioned it since. It is like it forgot."* Directly contradicts the product's own stated hypothesis that savings goals drive retention (see [strategy.md](strategy.md)) — the app isn't reinforcing the one thing it knows correlates with staying engaged.

## Praise vs. Complaints

**Praise (limited, and mostly conditional):**
- The concept itself is liked (#5: "Love the concept")
- First-week experience is genuinely valued (#2: "genuinely eye-opening")
- The weekly email is effective at holding attention (#10: "the only thing keeping me engaged")

**Complaints (dominant):**
- Static/repetitive home feed and dashboard (#1, #2, #7, #10)
- Passive tracking instead of active guidance (#3, #5)
- Generic, non-personalized content (#8, #9)
- Irrelevant/low-value notifications (#4)
- Savings goals set but never referenced again (#6)

## Top 3 Actionable Issues

1. **Give users a reason to return on a recurring cadence.** The single most common complaint (4/10 comments) is that nothing changes after week one. This is the strongest available evidence for prioritizing a recurring, personalized in-app touchpoint — directly aligned with the weekly summary concept already in strategy.md.
2. **Make the app demonstrably "know" the user.** Multiple users explicitly want non-obvious, personalized insight (not confirmation of what they already suspect) and want the app to act more like a coach than a display. Savings goals — set once and never mentioned again — are a concrete, low-effort place to start closing this gap.
3. **Fix nudge relevance before expanding nudge volume.** At least one user disabled notifications entirely because of a low-value alert. Any new engagement mechanism (e.g., the weekly summary) risks the same fate if it isn't filtered for relevance — this is a design constraint, not just a new feature to build.

## Connection to Existing Research

This feedback reinforces the finding from [research/interview-synthesis.md](research/interview-synthesis.md): the problem isn't the first aha moment, it's the absence of anything that closes the gap to a deeper, personalized experience before users give up.
