# Loop: sprint prep sweep

**Category:** Periodic prep. **Built and tested:** designed for this pack, following row 8 of the 20-task map. Rehearsable against `demo-workspace/bugs.md`.

**How to use this:** Copy the prompt into Claude Code or a Routine ahead of each sprint planning meeting. The loop's value is memory: it carries forward what slipped last sprint instead of you re-explaining it live in the room.

## 1. Trigger
Recurs every sprint cycle, 1-2 days before planning.

## 2. Skill file (the full prompt)
```
Recurring loop, fires 2 days before each sprint planning meeting. Read
the current backlog. Read the state file for what slipped from last
sprint and why. Draft a prioritized prep doc: what's carrying over (with
the reason it slipped), what's new and ready, what's blocked and on
whom. Post to Slack before the meeting.
```

## 3. Maker
Drafts the prep doc: carryover items with slip reasons, new ready items, blocked items with an owner named.

## 4. Checker
Confirms every carryover item actually appears in last sprint's state entry (no items invented as "carried over"), and every blocked item names a real owner, not "TBD."

## 5. Gate
Doesn't post if the backlog is unchanged from last sprint's prep. that signals someone hasn't updated the tracker, and the loop should flag that instead of producing a stale report.

## 6. State file
**Where:** `sprint-prep-state.md`, one entry per sprint.
**Read:** the maker reads the last sprint's entry for carryover items and slip reasons.
**Write:** after each run, log this sprint's carryover, new, and blocked lists so next sprint's run has something to diff against.

## Swap in your own data
Rehearse against `demo-workspace/bugs.md` (14 fictional bugs, 2 blocked-external). For real use, connect your actual sprint tracker (Jira, Linear, Asana) in place of the bug file.
