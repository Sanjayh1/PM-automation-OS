# Loop: weekly business review

**Category:** Repeating synthesis. **Built and tested:** yes, real output on test data.

**How to use this:** Copy the prompt below into Claude Code or a Routine. Point it at your metrics source. It needs a state file (see below). create the file once, empty, before the first run.

## 1. Trigger
Weekly, before Monday's WBR. A scheduled clock, not an event.

## 2. Skill file (the full prompt)
```
Weekly business review loop: synthesize this week's metrics vs last
week, with memory of prior weeks. Post to Slack before Monday's WBR.

Read this week's metrics export. Read the state file for last week's
numbers and the trend called out in the prior WBR. Write the story, not
just the table: what changed, what it means, and whether a footnote from
last week has become a headline this week.
```

## 3. Maker
Drafts the synthesis: this week vs last week, one headline story, the metrics table, one line for the room to say out loud.

## 4. Checker
Confirms every number in the draft traces to the metrics export (no invented figures) and that the "vs last week" claims match the state file, not vibes.

## 5. Gate
Doesn't post if the checker finds an unsourced number, or if nothing material changed from last week (a flat week posts a one-line "no change" note, not a padded report).

## 6. State file
**Where:** `wbr-state.md` in the same workspace, one entry per week.
**Read:** the maker reads the last 2-3 entries to know what's trending, not just last week's snapshot.
**Write:** after each run, append this week's headline metrics and the one-line story to the bottom of the file. Never overwrite a prior week.

## Sample output (real run, test data)
> **Watch time is up. Payouts are down. That gap is this week's real story.** Avg payout per 1K views is down 6.6%... **vs last week's WBR:** payouts per 1K views have now dropped two weeks running. If this is week three of the same mix shift, it stops being a footnote and becomes the headline metric for next Monday.

## Swap in your own data
Test run used `demo-workspace/wbr-data.md`. Replace with your real BI export or dashboard connector. Needs a connector or export job that runs before the loop fires each week.
