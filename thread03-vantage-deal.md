# Loop: sales deal intelligence

**Category:** Repeating synthesis. **Built and tested:** yes, real output on test data.

**How to use this:** Copy the prompt below into Claude Code or a Routine, connected to your CRM. Needs a state file so week 2 doesn't repeat week 1's flagged deals.

## 1. Trigger
Weekly, Monday 8 AM, ahead of the sales sync.

## 2. Skill file (the full prompt)
```
Build me a loop that runs every week.

It uses our CRM connector to check deals in pipeline and closed in the
last week. It mines the deals for opportunities for PM to help a deal
close (not by building a feature, but explaining), as well as learnings
for PM in the roadmap.

It delivers me a succinct set of takeaways with links for more
information. Check the state file first: don't re-flag a deal already
surfaced last week unless something changed.
```

## 3. Maker
Drafts the takeaways: which deals PM can unblock by explaining (a date, a number, a timeline), which need a different owner (Finance, Legal), and what the pipeline is teaching the roadmap.

## 4. Checker
Confirms every dollar figure and blocker claim traces to the CRM export, and that no deal already flagged last week is repeated without a state change.

## 5. Gate
Doesn't post if zero deals are unblockable by PM this week. a quiet week gets a one-line "nothing new" note, not padding.

## 6. State file
**Where:** `sales-loop-state.md`.
**Read:** the maker reads which deals were flagged in the last 2 weeks and their status, before drafting.
**Write:** after each run, append flagged deal names, the blocker, and this week's date.

## Sample output (real run, test data)
> **$16.4M in open pipeline. 3 deals are blocked on product answers PM can give this week, no eng work required.** Vantage Media ($4.2M/yr). Blocker is a date, not a feature. Eng's real ETA is Sep 20. Give it to Sam before Friday or Vantage downgrades to a 1-year deal.

## Swap in your own data
Test run used `demo-workspace/pipeline.csv` and `demo-workspace/emails/`. Replace with a real CRM connector (Salesforce, HubSpot) plus your engineering-timeline source.
