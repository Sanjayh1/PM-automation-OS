# Live Demo Kit. AI Automations webinar (v2 deck)

Two demos run genuinely live. Everything else in the deck is a captured run presented as a capture.

| # | Demo | Deck slide | Chip on slide | Runtime |
|---|---|---|---|---|
| 1 | The 7:30 AM brief Routine, fired with Run Now | 11 (prompt) and 12 (output) | `RUN LIVE` | 40-70 seconds |
| 2 | The `/goal` interview synthesis over `ig-pm-os/interviews/` | 24 (prompt + receipts) | `RUN LIVE` | 3-5 minutes |

Rule for both: **start the run, then keep talking.** Never watch a progress bar on camera. Both demos are built so the talking track covers the runtime.

---

## Demo 1. The 7:30 AM brief, fired live

### Setup (do this the morning of, not five minutes before)

1. Open `claude.ai/code/routines`. Confirm the Routine named **morning-brief** exists, is enabled, and its last run shows Success.
2. Confirm connectors: Google Calendar and Gmail attached, everything else detached. A fresh Routine can see every connected account, and a stray connector is the most common cause of a slow or weird run.
3. Confirm the Slack destination channel is the DM you will screen-share, not a team channel. Post one throwaway message in it and delete it, to check you still have write access.
4. Seed the test calendar for the demo day so the brief has something to write about: the five meetings from `ig-pm-os/calendar.md` (Tue Aug 4, 2026), each with 2 or more participants.
5. Do a full rehearsal run 60 minutes before the webinar. If it fails then, you present the capture and say so.
6. Screen layout: browser on the Routines page, Slack open in a second window, deck on the shared screen. Practise the alt-tab once.

### What to click, live

On slide 11, after reading the terminal card aloud:

1. Alt-tab to the Routines page.
2. Open **morning-brief**.
3. Click **Run Now**.
4. Alt-tab straight back to the deck and advance to slide 12.

### The prompt on screen (already saved in the Routine; read it, do not retype it)

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

### Talking track that covers the runtime

Slide 12 has the three rules on the right. Read all three at normal pace: write instructions not questions, strip the connectors down to the three it needs, and always Run Now before you schedule. That is 45 to 60 seconds, which is the whole runtime. Then alt-tab to Slack and read the first paragraph of whatever actually landed.

### Reset (so the demo is repeatable)

1. Delete the demo run's Slack message from the DM.
2. Leave the Routine enabled. Do not delete and rebuild it; rebuilding is a 20-minute job and the whole point of the demo is that it already exists.
3. If you ran it more than twice, check the run counter: Pro is 5 runs a day, Max 15, Team and Enterprise 25.

### Fallback if wifi dies or the run stalls

- **Do not debug on camera.** Say: "The run is still going, and that is a good moment to tell you what it produces." Advance to slide 12 and present the Slack card on the slide as the output. It is a real capture of this exact Routine.
- The slide-12 Slack card is the fallback. Nothing extra to load.
- If Slack itself is down, the same content is in `ig-pm-os/morning-brief.md`. Full-screen that file rather than showing a broken app.
- Line to say once, honestly: "That is a capture of a real run from this Routine, not a mockup."

---

## Demo 2. `/goal` interview synthesis, run live

### Setup

1. Open a terminal in the `ig-pm-os/` workspace. Confirm `interviews/` contains all 14 files, `INT-01.md` through `INT-14.md`.
2. Confirm the three trap files are intact, because the honest-blocking behaviour is the whole point of the demo:
   - `INT-06.md`. corrupted audio, no backup notes
   - `INT-09.md`. consent form missing
   - `INT-11.md`. duplicate of INT-04
3. Delete any `goal-interviews.md` output left over from a previous rehearsal. If the answer file is already sitting in the directory, the run finishes suspiciously fast and someone in the chat will notice.
4. Set the terminal font large enough to read on a compressed Zoom share. 18pt minimum.
5. Rehearse once the morning of and note the actual turn count. If it comes back at 14 turns instead of 17, say the number you got.

### The exact prompt to paste

```
/goal

I have 14 raw interview notes in interviews/. Roadmap review is Friday.

DONE WHEN: every note has a 2-line summary, a theme tag, and one verbatim
quote I can paste into the roadmap review. Un-processable notes are logged
with the reason. Duplicates are flagged and closed against the note they
duplicate.

VERIFY: print a completion table with one row per note ID, its status
(Processed / Blocked / Duplicate), and its theme tag.

OUTPUT: write the summaries, tags, and quotes to goal-interviews.md, then
print the completion table to the terminal.
```

### Expected runtime and what to say over it

3 to 5 minutes. That is long enough that you must have a plan for it. Run this order while it works:

1. Read the finish line aloud, slowly, and point at each of the three parts: Done When, Verify, Output. This is the callback to slide 23.
2. Explain the referee: a second, cheaper model reads the transcript after every turn and asks one question, is the condition met. Not met, another turn. Met, control returns.
3. Say the honest cost out loud before anyone else does: 10 to 20 times the tokens of a single prompt.
4. Take one chat question.
5. Come back when the completion table prints. Read only the counts and one blocked reason. Do not read 11 summaries.

Then advance to slide 25 and read the INT-04 quote out loud: "I'm not trying to go viral, I'm trying to not feel random."

### Reset

1. `rm goal-interviews.md` in the workspace.
2. Leave `interviews/` untouched. Never edit the three trap files; they are what makes the run honest.
3. If you rehearse more than twice in a day, start a fresh session so scroll-back does not leak previous answers into the run.

### Fallback if wifi dies or the run stalls

- Slide 24 already carries the full receipts table (2 turns / 2 touched / 12 untouched, versus 17 turns / 11 processed / 2 blocked / 1 duplicate / 0 remaining). Present it as the captured run and say so plainly.
- Slide 25 carries two finished outputs, INT-04 and INT-14, with quotes. That is the payoff and it survives without the live run.
- The full captured output, all 11 summaries plus the blocked and duplicate detail, is in `ig-pm-os/goal-interviews.md`. Full-screen it only if someone asks to see all of them.
- Line to say once: "That is the output of the same prompt when I ran it this morning. Same workspace, same 14 notes."

---

## Pre-flight checklist, 60 minutes before

- [ ] Rehearsal run of the morning-brief Routine, Success
- [ ] Rehearsal run of the `/goal` interview synthesis, completion table prints
- [ ] `goal-interviews.md` deleted after the rehearsal
- [ ] Slack DM cleared of rehearsal messages
- [ ] Terminal font at 18pt or larger
- [ ] Connectors trimmed to Calendar and Gmail only
- [ ] Both fallback slides (12, 24, 25) checked in presenter view
- [ ] Decide now: if either rehearsal fails, both demos run as captures and you say so at the top

## The honesty line, if you fall back

Say it once, plainly, and move on. Do not apologise twice.

> "Wifi is not cooperating, so I am showing you the capture from this morning's run instead of running it in front of you. Same prompt, same workspace, same numbers."
