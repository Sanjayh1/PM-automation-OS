# Loop: exec update prep

**Category:** Periodic prep. **Built and tested:** designed for this pack, adjacent to row 13 (weekly status update) and row 19 (stakeholder update draft) on the 20-task map.

**How to use this:** Copy the prompt into Claude Code or a Routine ahead of your recurring exec or stakeholder update. This is a loop, not a bare scheduled task, because the draft needs to remember what was promised last time, so this week's update can report against it.

## 1. Trigger
Recurs on your update cadence (weekly or bi-weekly), 1 day before it's due.

## 2. Skill file (the full prompt)
```
Recurring loop, fires 1 day before the exec update is due. Read this
period's metrics and shipped work. Read the state file for what was
promised last update. Draft the update: what shipped against what was
promised, what's slipping and why, what's newly at risk. Flag any claim
that doesn't trace to a source. Post the draft (not the final) to my
Slack DM for review before it goes out.
```

## 3. Maker
Drafts the update in your voice: promised-vs-shipped, slippage with reasons, new risks.

## 4. Checker
Flags any claim in the draft that doesn't trace to a metric, ticket, or commit. the callback to the deck's honest gap: a checker can verify execution, not strategy, so it checks sourcing, not judgment.

## 5. Gate
Never auto-sends. This loop's gate is a human: it drafts, it never posts the final version without your review, because an exec update carries your name.

## 6. State file
**Where:** `exec-update-state.md`.
**Read:** the maker reads the last update's promises to report progress against them.
**Write:** after you approve and send each update, log what was promised this round for the next cycle to check against.

## Swap in your own data
No fabricated exec-update set ships in this pack. Rehearse the promised-vs-shipped structure using `demo-workspace/wbr-data.md`'s metrics, then point the real version at your actual shipped-work tracker and your last sent update.
