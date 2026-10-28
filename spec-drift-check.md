# Weekly business review loop

**What it does:** Synthesizes this week's metrics against last week, with memory of the weeks before that, and posts the story (not just the numbers) to Slack before Monday's WBR.

**Where to run it:** Claude Code or Claude Routines, pointed at your metrics source (a BI export, a dashboard connector, or a CSV you refresh weekly). Needs a state file so it can say "this is week three of the same trend," not just "this week vs last week."

**What to customize:** Swap the metric source for your own weekly export. Swap the metric names in the prompt for the numbers your team actually reviews (DAU, revenue, whatever your WBR tracks).

---

```
Weekly business review loop: synthesize this week's metrics vs last week,
with memory of prior weeks. Post to Slack before Monday's WBR.
```

## Sample output (real run, test data)

> **Watch time is up. Payouts are down. That gap is this week's real story.**
>
> **Creator payouts:** $18.6M total, -2.6% w/w. This is the one that looks wrong until you check the mix. Avg payout per 1K views is down 6.6% ($2.58 → $2.41). Users are watching more, but shifting toward shorter Reels that pay less per view. Not a bug.
>
> **vs last week's WBR:** payouts per 1K views have now dropped two weeks running. If this is week three of the same mix shift, it stops being a footnote and becomes the headline metric for next Monday.

That last line is the payoff of the state file: it remembers the last WBR and tells you when a footnote becomes a headline.

## Swap in your own data

Test run used `demo-workspace/wbr-data.md` (fictional this-week-vs-last-week metrics). To run for real:
- Connect your actual metrics source (BI tool export, dashboard API, or a weekly CSV pull).
- Give it a real state file location (see `loops/weekly-business-review.md` for exactly what to read and write).
