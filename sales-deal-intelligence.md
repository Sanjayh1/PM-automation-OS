# Loop: social sentiment scan

**Category:** Threshold monitoring. **Built and tested:** designed for this pack, following row 16 of the 20-task map (listed there as a scheduled task; built here as a loop because it needs memory to detect a genuine shift, not just a snapshot).

**How to use this:** Copy the prompt into Claude Code or a Routine with web-reading access. Reads full post text, not headline counts. that's the deck's proof point against a plain keyword alert.

## 1. Trigger
Weekly clock, plus a threshold override: fires early if mention volume on any platform spikes 2x+ its weekly baseline.

## 2. Skill file (the full prompt)
```
Weekly loop (with an early-fire threshold override): read the full text
of the top 30 most-engaged posts mentioning [product/company] across
Reddit, Product Hunt, G2, and X. Cluster into themes with 3+ independent
mentions in users' own words (not the same user posting 3 times). Check
the state file for themes flagged in prior weeks. Note new themes and
trend direction on recurring ones. Post the digest to Slack.
```

## 3. Maker
Reads full post text (not just counts), clusters into themes, drafts a one-line-per-theme digest with trend direction.

## 4. Checker
Confirms each theme has 3+ genuinely independent mentions and that any "trending up" claim matches the state file's prior-week counts.

## 5. Gate
Doesn't post if no theme clears the 3-mention bar that week. silence over noise.

## 6. State file
**Where:** `sentiment-scan-state.md`.
**Read:** the maker reads the last 2-3 weeks of themes to judge trend direction.
**Write:** after each run, append this week's themes, mention counts, and sources.

## Why this beats a keyword alert
A keyword tool counts mentions. This reads what people actually said and clusters it into themes in their own words. the difference between "47 mentions of 'slow'" and "12 people describing the same specific friction point."

## What needs a connector
Live web-reading access to Reddit, Product Hunt, G2, and X (or whichever platforms matter for your product). Without it, this loop can't run.

## Swap in your own data
No fabricated social-mention set ships in this pack. Swap `[product/company]` for your own and connect real platform access before the first run.
