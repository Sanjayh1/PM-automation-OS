# Morning brief. scheduled task (Routine)

**What it does:** Reads your calendar every weekday morning, pulls the recent email history for anyone in a meeting with 2+ people, and posts a one-paragraph prep note per meeting to your Slack DM before you're awake.

**Where to run it:** claude.ai/code/routines. New Routine, paste the prompt below, attach only Google Calendar and Gmail as connectors, set the schedule, then hit **Run Now** once before you trust it on autopilot.

**What to customize:** Swap "Google Calendar" and "Slack DM" for wherever your calendar and your preferred inbox for this actually live. If you don't use Slack, change the last line to "Post the result to [your channel]". email, a Notion page, whatever you check first each morning.

---

```
Schedule: weekdays, 7:30 AM.

Read my Google Calendar for today. Find every meeting with 2 or more
participants.

For each of those meetings, pull the last 10 email threads from the past
45 days that include any of that meeting's participants.

Write one paragraph per meeting: what the meeting is about, what each
participant most recently pushed for, and the one decision or stance I
need to walk in with.

Post the result to my Slack DM. No preamble, no summary of what you did.
```

---

## The three rules that make this work

1. **Write instructions, not questions.** A Routine that asks you something mid-run stalls until you answer it. Front-load every decision into the prompt.
2. **Strip connectors to the 3 it needs.** A new Routine can see every account you've connected. Detach everything except Calendar and Gmail before the first run.
3. **Run Now before you schedule.** Watch it end to end once. Don't hand it a 7:30 AM slot until you've seen a 7:30 AM output.

## Swap in your own data

The demo ran this against `demo-workspace/calendar.md` (5 fictional meetings) and `demo-workspace/emails/` (8 fictional threads). To run it for real:
- Replace the calendar source with your actual Google Calendar (just connect the account, no file needed).
- Replace the email source with your actual Gmail (same, connector not a file).
- Replace the destination Slack DM with your own.

## Sample output (real run, test data)

> Good morning. 5 meetings today. Here's what's loaded before you walk in.
>
> **9:00 Creator Payouts Sync**. Priya wants the Q3 formula shift on the agenda: weight completion rate over raw views. Devon's estimate is 1 sprint, but he's blocked on Chen confirming the completion-rate signal is stable (it's noisy under 500 views/week per BUG-408). Bring a stance on whether that noise is a ship-blocker or a footnote.
>
> **10:00 Reels Watch-Time Regression Review**. Chen has the data: Android watch time down 6.2% platform-wide, 9.1% in the affected cohort, isolated to the Jul 26 autoplay buffer change on 50% of Android. Devon can pull the flag today. This is a rollback-or-fix decision, not a discovery meeting.

That's the format: one paragraph per meeting, a name, a number, a decision. Nothing generic makes it in.
