# The 20 PM tasks, mapped to a primitive

**How to use this:** Find the task closest to something you do every week. The primitive column tells you which prompt template to reach for. The reason column is the test you run on your own tasks once these 20 run out. Rows 11 and 12 apply twice: to your current PM job, and to landing your next one.

| # | Task | Primitive | Why |
|---|---|---|---|
| 1 | Pre-meeting prep brief | Scheduled task | Same clock every weekday, fresh data each run |
| 2 | Weekly business review | Loop | Needs last week's numbers; memory between runs |
| 3 | Competitor pricing monitor | Loop | Compares today against yesterday's log |
| 4 | Support ticket themes | Scheduled task | Monday 6 AM ranked report (a Managed Agent when the whole team needs it) |
| 5 | User interview synthesis | Goal | Done when every note has a summary, a theme tag, and a quote |
| 6 | PRD first draft | Sub-agent | A maker drafts, a checker scores it against your template |
| 7 | Bug backlog triage | Goal | Runs until zero open, blockers logged honestly |
| 8 | Sprint prep sweep | Loop | Recurs every sprint, carries what slipped last time |
| 9 | Spec drift check | Loop | Event-triggered; fires when the spec changes |
| 10 | Feedback theme digest | Loop | Recurring synthesis with memory of prior themes |
| 11 | Resume tailoring per job post | Sub-agent | A maker writes, a checker blocks anything generic |
| 12 | Job board scan | Scheduled task | Nightly clock, ranked digest by morning |
| 13 | Weekly status update | Scheduled task | Same format, same time, every week |
| 14 | Launch readiness checklist | Workflow | Fixed order and validation gates, auditable |
| 15 | Analytics narrative for reviews | Workflow | Fixed assembly steps; the raw numbers stay in your BI tool |
| 16 | Social sentiment scan | Scheduled task | Weekly clock, pure web reading |
| 17 | Meeting notes to tickets | Workflow | Extraction in a fixed sequence with an approval gate |
| 18 | Roadmap or stakeholder review prep | Goal | Done when five sections exist, each one sourced |
| 19 | Stakeholder update draft | Sub-agent | A maker drafts in your voice, a checker flags unsourced claims |
| 20 | Release notes from the git log | Goal | Done when the file matches the format, every skip explained |

## Job-search lens

Rows 11 and 12 are the whole game if you're searching right now. A resume-tailoring sub-agent pair plus a nightly job-board scan is most of a job-search system. See `prompts/job-search-maker-checker.md`.

Source: slides 3-4 of the PM Automation webinar deck.
