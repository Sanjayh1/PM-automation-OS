# The six primitives

**How to use this:** Screenshot this table. These six words get used interchangeably by most PMs, and that's why automations die in week 2. Each row is mutually exclusive. Read top to bottom once, then use this page as the lookup whenever you're not sure which primitive a task needs.

| Primitive | Definition | PM example |
|---|---|---|
| **Scheduled task** | Runs on a clock. | 7:30 AM meeting brief. |
| **Goal** | Runs until a written finish line, verified by a referee model. | Bug backlog to zero overnight. |
| **Loop** | A recurring automation that keeps memory between runs and gates its own output. | A weekly business review that remembers last week. |
| **Workflow** | A fixed sequence of agent steps; the order never varies. | A launch checklist that runs the same way every time. |
| **Sub-agent** | A delegate inside one session with its own separate memory. | A checker that scores your draft. |
| **Graph** | The map of how your automations feed each other. | Your feedback digest filing bugs into engineering's fix loop. |

## The one-line test

- Runs at a fixed time, no memory needed → **scheduled task**
- Needs to know what happened last time → **loop**
- You can write "done when X" → **goal**
- The order of steps must never change → **workflow**
- One piece of work needs a second, independent set of eyes → **sub-agent**
- You have 3+ automations and need to see how they connect → **graph**

Source: slide 2 of the PM Automation webinar deck.
