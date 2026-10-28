# Interview synthesis. /goal

**What it does:** Turns a stack of raw customer interview notes into a roadmap-ready summary, theme tag, and verbatim quote per note, logs anything it can't process with the honest reason, and flags duplicates. Runs until every note is accounted for, not until you get bored and say "keep going" for the fifteenth time.

**Where to run it:** Claude Code, in a terminal, in the folder holding your interview notes. Type `/goal`, then paste the finish line below.

**What to customize:** Swap "14 raw interview notes in interviews/" for your actual folder and count. Swap "roadmap review is Friday" for your real deadline. The Done When / Verify / Output structure stays the same for any synthesis task; see `goal-templates/three-part-finish-line.md` for the template this was built from.

---

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

## What actually happens

A second, cheaper referee model reads the transcript after every turn and asks one question: is the condition met? No: another turn. Yes: control returns. You don't watch a progress bar; you get a finished file.

## Receipts (real run, test data)

| | Without /goal | With /goal |
|---|---|---|
| Turns | 2 | 17 |
| Notes touched | 2 | 14 |
| Processed (summary + tag + quote) | 0 | 11 |
| Blocked (logged w/ reason) | 0 | 2 |
| Duplicates caught | 0 | 1 |
| Still untouched | 12 | 0 |

Cost, honestly: 10-20x the tokens of a single prompt. You're buying back the checking hours, not the tokens.

## Swap in your own data

Test run used `demo-workspace/interviews/` (14 fictional notes, INT-01 through INT-14, with 2 deliberately un-processable files and 1 duplicate built in so you can see the honest-blocking behavior). To run for real:
- Point the folder at your own raw interview notes.
- Adjust the note count in the prompt to match.
- Keep the Done When condition demanding, not vague: "a summary, a theme tag, and a quote" is specific enough for the referee to check. "Good synthesis" is not.
