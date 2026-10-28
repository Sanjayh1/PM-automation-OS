# Loop: churn-signal watch

**Category:** Threshold monitoring. **Built and tested:** designed for this pack.

**How to use this:** Copy the prompt into Claude Code or a Routine connected to your usage and support data. Watches for the combination of signals that precedes churn, not any single metric alone.

## 1. Trigger
Daily check; only produces output when a defined combination of thresholds is crossed for an account (event-triggered in effect, framed as threshold monitoring).

## 2. Skill file (the full prompt)
```
Daily loop: for each account above [revenue/seat threshold], check usage
trend (7-day active vs 30-day baseline), open support ticket sentiment,
and any recent downgrade or seat-reduction request. If an account
crosses 2 or more of these thresholds (define thresholds explicitly:
e.g. usage down 30%+, 2+ negative-sentiment tickets in 7 days, any
downgrade request), post an alert to Slack with the account name, which
thresholds triggered, and the account's last logged status from the
state file.
```

## 3. Maker
Checks each tracked account against the defined thresholds, drafts the alert only for accounts crossing 2+.

## 4. Checker
Confirms the threshold count is accurate against the raw data (not rounded up) and that the account wasn't already alerted this week for the same combination.

## 5. Gate
Requires 2+ simultaneous signals, not 1. a single dip in usage is noise; usage down plus a downgrade request plus negative tickets is a pattern worth a human's attention.

## 6. State file
**Where:** `churn-watch-state.md`, one section per account.
**Read:** the maker reads whether this account was already alerted recently, to avoid re-alerting on the same unresolved signal daily.
**Write:** logs every alert fired, with the triggering thresholds and date, so the pattern is auditable later.

## What needs a connector
Product usage data (an analytics tool or data warehouse connector) and your CRM or support tool for sentiment and downgrade requests. This loop can't run on file exports alone; it needs live account-level data.

## Swap in your own data
No fabricated usage-and-churn set ships in this pack. `demo-workspace/pipeline.csv` shows the shape of an account-level table you can adapt; for real use, connect your actual usage and support tools.
