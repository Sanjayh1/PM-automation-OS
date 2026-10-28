# Loop: launch-week monitor

**Category:** Event-triggered. **Built and tested:** designed for this pack.

**How to use this:** Copy the prompt into Claude Code or a Routine during the week around a launch. Triggered by threshold crossings on your launch metrics, not a plain clock. it should stay quiet unless something needs your attention.

## 1. Trigger
Event-triggered: fires when a launch-tracked metric (crash rate, signup funnel drop-off, support ticket spike) crosses a defined threshold during the launch window.

## 2. Skill file (the full prompt)
```
Launch-week loop, active [start date] through [end date]. Check
[metrics source] every hour during the launch window. Compare each
metric against its pre-launch baseline in the state file. If any metric
crosses its defined threshold (state the thresholds explicitly per
metric), post an alert to Slack with the metric, the baseline, the
current value, and the percent change. Otherwise stay silent.
```

## 3. Maker
Checks each tracked metric against its threshold, drafts the alert with baseline, current value, and percent change if a threshold is crossed.

## 4. Checker
Confirms the threshold math is right and that the metric source is the same one used to set the baseline (a metric definition change mid-launch would otherwise trigger a false alarm).

## 5. Gate
Silent below threshold. This loop's entire value is that it doesn't need watching. it only speaks when something crosses the line you set in advance.

## 6. State file
**Where:** `launch-monitor-state.md`.
**Read:** the maker reads the pre-launch baseline and any alerts already fired this launch, so it doesn't re-alert on the same crossing every hour.
**Write:** logs every check (even non-alerts) plus a flag on whether an alert already fired for this threshold, to avoid alert spam.

## What needs a connector
Live access to your launch metrics dashboard or analytics tool. Set the thresholds before launch day, not during. a threshold picked mid-incident is not a threshold.

## Swap in your own data
No fabricated launch-metrics set ships in this pack. Use `demo-workspace/wbr-data.md`'s Android regression row (-9.1% watch time) as a rehearsal example of what a real threshold-crossing alert looks like, then point this at your own launch dashboard.
