# Sales intelligence loop

**What it does:** Reads your CRM's open pipeline and closed deals once a week, finds deals PM can unblock by explaining (not by building), and surfaces roadmap learnings hiding in the pipeline. Posts a takeaways doc to Slack every Monday at 8 AM.

**Where to run it:** Claude Code, pointed at your CRM connector (Salesforce, HubSpot, whatever you run), or Claude Routines if you want it fully hands-off in the cloud. This is a loop, not a bare scheduled task: it needs a state file (see below) so week 3 can reference week 2.

**What to customize:** Swap "Salesforce" for your actual CRM connector name. Swap the Slack channel for wherever sales-facing PM updates live at your company.

---

```
Build me a loop that runs every week.

It uses our Salesforce (our CRM) connector to check deals in pipeline and
closed in the last week. It mines the deals for opportunities for PM to
help a deal close (not by building a feature, but explaining), as well as
learnings for PM in the roadmap.

It delivers me a succinct set of takeaways with links for more
information.
```

## This is a loop, not just a scheduled task

A scheduled task fires and forgets. A loop needs memory (which deals were already flagged last week, so you don't repeat yourself) and a gate (don't post if nothing changed). See `loops/sales-deal-intelligence.md` in this pack for the full 6-piece version: trigger, maker, checker, gate, and state file.

## Sample output (real run, test data)

> **$16.4M in open pipeline. 3 deals are blocked on product answers PM can give this week, no eng work required.**
>
> **1. Vantage Media ($4.2M/yr, Negotiation)**. Blocker is a date, not a feature. Eng's real ETA for Creator Bonus API partner access is Sep 20. Sam hasn't been given that number yet. Give it to him before Friday or Vantage downgrades to a 1-year deal.

## Swap in your own data

Test run used `demo-workspace/pipeline.csv` (fictional deals) and `demo-workspace/emails/` (fictional threads with the blocker context). To run for real:
- Connect your actual CRM in place of the pipeline.csv stand-in.
- Connect your actual email or deal-notes source in place of the email threads.
- Point the Slack post at your real sales-PM channel.
