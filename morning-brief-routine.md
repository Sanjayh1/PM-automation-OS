# Open Bug Backlog. 14 tickets, ahead of Thursday sprint planning

| ID | Title | Severity | Repro notes |
|---|---|---|---|
| BUG-401 | Reels autoplay buffer causes watch-time drop on Android | High | Confirmed via A/B, Jul 26 buffer change, affected cohort -9.1% vs control. Reproduces on Android 13+, all regions. |
| BUG-402 | Creator payout dashboard shows stale totals for 24h after payout run | Medium | Cache TTL set to 24h instead of 1h. Reproduces every payout cycle. |
| BUG-403 | DM spam filter false-positives legit brand-deal messages | High | New keyword filter (shipped Aug 2) flags messages containing "sponsorship" + a link. Reproduces on ~4% of legit brand DMs. |
| BUG-404 | Creator Bonus API returns 500 on malformed date range | Medium | Repro: pass end_date before start_date. Stack trace points to validation layer missing a bounds check. |
| BUG-405 | Payout CSV export drops rows with non-ASCII creator names | Medium | Repro: export any batch containing a name with accented characters. Encoding bug in export job. |
| BUG-406 | Stripe payout webhook retries fail silently | High | BLOCKED-EXTERNAL. Stripe staging environment down since Aug 1, ETA Friday per Stripe status page. Cannot reproduce/test until staging restored. |
| BUG-407 | Stripe test-mode payouts show wrong currency symbol | Low | BLOCKED-EXTERNAL. same Stripe staging outage as BUG-406. |
| BUG-408 | Reels watch-time completion metric has noisy signal at low sample sizes | Medium | Flagged by Data Science (Chen). Repro: any creator with <500 views/week shows completion-rate swings of 15%+ day to day. |
| BUG-409 | DM spam filter false-positives legit brand-deal messages containing links | High | DUPLICATE of BUG-403. same root cause, filed separately by a different reporter. |
| BUG-410 | Creator Payouts Sync agenda doc link broken in calendar invite | Low | Repro: click agenda link from recurring calendar invite, 404s. Google Calendar link rot, easy fix. |
| BUG-411 | Reels ranking model over-indexes on completion rate for sub-10s clips | Medium | Reproduces consistently for clips under 10 seconds; short clips get ranking boost disproportionate to engagement. |
| BUG-412 | Vantage Media test account missing early-access feature flag | Medium | Repro: log in as Vantage test account, Creator Bonus API menu item absent. Flag not provisioned in staging config. |
| BUG-413 | Support ticket auto-tagging misclassifies "payout delay" as "account access" | Medium | Repro: submit ticket with "payout" + "delay" keywords, auto-tagger routes to wrong queue ~30% of the time. |
| BUG-414 | Creator onboarding flow skips payout-method step for EU accounts | High | Repro: sign up with an EU-region test account, flow jumps from profile to dashboard, skipping payout setup. Confirmed on 3 EU test accounts. |
