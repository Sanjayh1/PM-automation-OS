# Loop: feedback theme digest

**Category:** Repeating synthesis. **Built and tested:** designed for this pack, following the outline's row 10 spec (feeds engineering's fix loop. see the graph example in `definitions.md`).

**How to use this:** Copy the prompt into Claude Code or a Routine connected to wherever qualitative feedback lands (support tickets, app reviews, a feedback inbox). Needs a state file so recurring themes get flagged as recurring, not re-discovered weekly.

## 1. Trigger
Weekly.

## 2. Skill file (the full prompt)
```
Weekly loop: read this week's feedback sources (support tickets, app
store reviews, in-app feedback). Cluster into themes appearing 3+ times.
Check the state file: if a theme was flagged in the last 3 weeks, note
it as recurring and whether it's trending up or down in volume. File any
theme with a clear bug behind it directly into the tracker with the
theme summary attached. Post the digest to Slack.
```

## 3. Maker
Clusters raw feedback into named themes, drafts a one-line summary per theme, checks whether each theme maps to an existing bug ID.

## 4. Checker
Confirms each theme actually has 3+ independent mentions (not 3 mentions from the same user) and that recurring-theme claims match the state file.

## 5. Gate
Doesn't file a bug-tracker entry without a clear, repeatable reproduction pattern across the mentions. vague themes get reported, not filed.

## 6. State file
**Where:** `feedback-theme-state.md`.
**Read:** the maker reads the last 3 weeks of themes to flag recurrence and trend direction.
**Write:** after each run, append this week's themes, volumes, and filed bug IDs.

## The graph connection
This is the loop the deck uses as the cross-functional example: this digest files the bug, engineering's fix loop picks it up, a PR is waiting for human review by morning. See `definitions.md` for the graph primitive.

## What needs a connector
A real feedback source (support tool, app store review API, or feedback inbox) and write access to your bug tracker to file themes directly.

## Swap in your own data
No fabricated feedback set ships in this pack's demo-workspace. `demo-workspace/tickets/last-7-days.md` is close enough to rehearse the clustering step; swap in your real ticket/review export for the full loop.
