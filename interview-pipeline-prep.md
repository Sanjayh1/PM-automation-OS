# Support ticket theme agent

**What it does:** Reads the last 7 days of support tickets, finds themes appearing 3 or more times, maps each theme to its roadmap implication (a bug ID, a shipping fix, an owner), ranks by volume, and posts a Slack report before Monday standup.

**Where to run it:** This one is a team-scale task (row 4 on the 20-task map), which makes it a good candidate for a Managed Agent: it runs in your company's Claude cloud, anyone on the team can see it, and an engineer wires it up once. You write the brief; the engineer configures the connector to your ticket system. If you're running solo, the same prompt works fine as a personal scheduled task in Claude Code or Routines. you'll just be the only one who sees the report.

**What to customize:** Swap "support tickets" for your actual ticket source (Zendesk, Intercom, Linear, a shared inbox). Swap "3+ times" for whatever volume actually signals a theme at your ticket volume. 3 works for a 25-ticket week, not for a 2,000-ticket week.

---

```
Mondays 6 AM: read the last 7 days of support tickets, find themes
appearing 3+ times, map each to a roadmap implication, rank by volume,
post a Slack report before standup.
```

## Sample output (real run, test data)

> **3 themes, 25 tickets, one of them is a phishing campaign your creators are actively getting hit by right now.**
>
> **1. Phishing DMs impersonating brand deals. 6 tickets.** Every report describes the same pattern: a DM claiming to be a brand partner, asking the creator to click a link to "claim payout." → Roadmap implication: this is the same campaign flagged in Tuesday's DM Safety Escalation Triage. The filter fix ships this week; ticket volume is your leading indicator it's working.

That's the difference between a report and a report you can act on: every theme has a bug ID and an owner attached, not just a count.

## Swap in your own data

Test run used `demo-workspace/tickets/last-7-days.md` (25 fictional one-line tickets, 3 themes at 5-6 occurrences each) and `demo-workspace/bugs.md` (the fictional backlog the themes map to). To run for real:
- Connect your real ticket source.
- Connect your real bug tracker so the "roadmap implication" line has something to map to. without it, the agent can only report themes, not implications.
