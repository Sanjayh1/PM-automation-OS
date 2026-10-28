# Loop: competitor pricing monitor

**Category:** Event-triggered. **Built and tested:** designed from the deck's live-demo spec; not run against fabricated test data in this pack. Needs a web-reading connector before its first real run.

**How to use this:** Copy the prompt into Claude Code or a Routine with web access. This is the loop that most clearly shows why a loop beats a scheduled task: it compares today's read against yesterday's log and only speaks up when something actually moved.

## 1. Trigger
Checks daily; only produces output when a change is detected (event-triggered, not "report no matter what").

## 2. Skill file (the full prompt)
```
Daily loop: read [competitor]'s public pricing page. Compare against
yesterday's logged version in the state file. If nothing changed, log
"no change" and stay silent. If something changed (price, tier, feature
gating), write a one-paragraph summary of exactly what moved and post it
to Slack.
```

## 3. Maker
Reads the current pricing page, diffs it against the last logged version, drafts a summary of what changed (not a full re-description of the whole page).

## 4. Checker
Confirms the claimed change is a real diff against the state file's last snapshot, not a hallucinated one. re-reads both versions side by side before approving.

## 5. Gate
Silent on no-change days. Posts only on a confirmed diff. This gate is what keeps the loop from becoming noise you tune out by week 3.

## 6. State file
**Where:** `pricing-log.md`, one dated entry per check.
**Read:** the maker reads yesterday's logged snapshot to diff against.
**Write:** every run appends today's snapshot and a change/no-change flag, regardless of outcome. the log itself is the audit trail.

## What needs a connector
Live web reading (a browsing tool or a scheduled fetch) pointed at the competitor's actual pricing URL. Without it, this loop can't run. there's no test-data substitute for a live page, unlike the other 11 loops in this pack.

## Swap in your own data
Replace `[competitor]` with the actual company and URL. Add one loop per competitor you track; don't combine them into one prompt or the diff logic gets muddy.
