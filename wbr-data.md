# Filled example: bug backlog triage (row 7)

**What it does:** Runs your entire open bug backlog to zero before sprint planning, with every blocker logged honestly instead of quietly dropped. Use this as the pattern for any "clear a queue to zero" task: bugs, support tickets, a review inbox.

**Where to run it:** Claude Code, terminal, pointed at your bug tracker or a bug list file. Best run overnight since it can take dozens of turns.

---

```
/goal

14 open bugs in bugs.md, sprint planning in 2 days.

DONE WHEN: every bug is either fixed with a passing test, logged as
blocked-external with a reason, or flagged as a duplicate. Stop rule:
don't touch Stripe-dependent bugs beyond logging them.

VERIFY: print a resolution table when done, one row per bug ID with its
resolution.

OUTPUT: the resolution table, plus test confirmation per fixed bug.
```

## Receipts (real run, test data)

| | Without /goal | With /goal |
|---|---|---|
| Turns | 2 | 31 |
| Bugs touched | 2 | 14 |
| Bugs fixed (tested) | 0 | 11 |
| Blocked-external (logged) | 0 | 2 |
| Duplicates caught | 0 | 1 |
| Still open | 12 | 0 |

"I wasn't watching. It ran 31 turns overnight and walked into sprint planning with a resolution for every single row."

## What to customize

The stop rule ("don't touch Stripe-dependent bugs beyond logging them") is what keeps the run from burning turns on something it can't actually fix. Name your own external dependency here. a vendor, an API you don't control, a legal review. so the run knows where to stop and log instead of loop.
