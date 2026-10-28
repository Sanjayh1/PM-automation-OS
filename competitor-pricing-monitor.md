# Loop: metric anomaly alert

**Category:** Threshold monitoring. **Built and tested:** designed for this pack; rehearsable against `demo-workspace/wbr-data.md`'s Android regression row, the same real anomaly the deck's WBR demo surfaces.

**How to use this:** Copy the prompt into Claude Code or a Routine pointed at your core metrics. This loop's whole job is catching the thing that would otherwise wait until Monday's WBR to get noticed.

## 1. Trigger
Checks daily (or hourly for volatile metrics); fires only on a threshold crossing.

## 2. Skill file (the full prompt)
```
Daily loop: check [list of core metrics] against their 7-day rolling
baseline in the state file. If any metric moves more than [threshold,
e.g. 5%] in a single day, or diverges from a normally correlated metric
(e.g. watch time up while payouts down, unexpectedly), post an alert to
Slack: the metric, the move, the likely cause if one is visible in
nearby data, and whether this looks like signal or noise.
```

## 3. Maker
Checks each metric against its rolling baseline, drafts the alert with a first-pass read on cause (a recent deploy, a regional pattern, a known seasonal effect).

## 4. Checker
Confirms the move actually exceeds the defined threshold against the real baseline (not a stale one) and that any claimed cause is stated as a hypothesis, not a fact, unless it's directly confirmed in the data.

## 5. Gate
Silent below threshold. A metric that wobbles inside its normal daily range never reaches Slack. that discipline is what keeps this loop from getting muted.

## 6. State file
**Where:** `metric-anomaly-state.md`.
**Read:** the maker reads the rolling 7-day baseline and any anomalies already flagged this week.
**Write:** every check logs the day's values, regardless of whether it triggers an alert, so the baseline stays current.

## Sample of the pattern (real data, different loop's output)
The WBR loop's own test run caught exactly this shape of signal: Android watch time down 9.1% in the affected cohort, isolated to a specific change (the Jul 26 autoplay buffer update). A metric-anomaly loop is what would have caught that the same day it happened, instead of at Monday's review.

## What needs a connector
Live access to your core metrics (analytics tool, data warehouse, or BI dashboard API) with a rolling baseline you can query daily.

## Swap in your own data
Rehearse the anomaly-detection logic against `demo-workspace/wbr-data.md`. For real use, connect your actual metrics source and set thresholds per metric before turning this on.
