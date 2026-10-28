# Loop: interview-pipeline prep

**Category:** Periodic prep. **Built and tested:** designed for this pack, the job-search-lens cousin of row 5 (user interview synthesis). this version watches your own candidate pipeline instead of customer interviews.

**How to use this:** Copy the prompt into Claude Code or a Routine while you're actively interviewing. Runs before each interview round so you walk in with the full context instead of skimming notes five minutes before.

## 1. Trigger
Recurs the morning of any day with a scheduled interview (calendar-triggered, similar to the morning brief but interview-specific).

## 2. Skill file (the full prompt)
```
Morning-of loop, fires the morning of any calendar day with an interview
tagged "job search." Read the calendar entry, the company research
notes, and the state file for what was covered and asked in prior rounds
with this company. Draft a one-page prep: what's already been discussed,
what's likely next (based on the interview stage), and 3 questions worth
asking this round that weren't already asked. Post to Slack DM.
```

## 3. Maker
Drafts the one-page prep: prior-round summary, likely focus for this round, 3 fresh questions.

## 4. Checker
Confirms none of the 3 suggested questions duplicate a question already logged as asked in an earlier round with the same company. asking the same thing twice reads as unprepared.

## 5. Gate
Doesn't fire if no interview is tagged for that day. this loop should never produce noise on a day with nothing to prep for.

## 6. State file
**Where:** `interview-pipeline-state.md`, one section per company.
**Read:** the maker reads all prior rounds logged for that company before drafting.
**Write:** after each interview, log what was covered and asked, so the next round's prep doesn't repeat it.

## Swap in your own data
No fabricated interview-pipeline set ships in this pack; `demo-workspace/job-search/` has a resume and two postings you can use to rehearse the research-notes step. For real use, connect your calendar and keep your own round-by-round notes in the state file as you go.
