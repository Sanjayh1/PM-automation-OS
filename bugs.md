# Filled example: release notes from the git log (row 20)

**What it does:** Turns a raw git log into formatted release notes, done when the file matches your format and every skipped commit is explained, not silently dropped. Use this as the pattern for any "transform a raw log into a formatted artifact" task.

**Where to run it:** Claude Code, terminal, in your repo.

---

```
/goal

Write release notes for the commits since the last tag.

DONE WHEN: RELEASE-NOTES.md exists, every user-facing commit has one line
in the correct section (Added / Fixed / Changed), and every skipped
commit (internal-only, revert, typo fix) has a one-line reason in a
"Skipped" section at the bottom.

VERIFY: diff the commit count in the git log against the sum of lines in
RELEASE-NOTES.md plus the Skipped section. They must match exactly.

OUTPUT: print the final counts (included vs skipped) to the terminal
alongside the file path.
```

## Why the verify line matters here

Without a count-matching check, it's easy for a run to quietly drop a commit that didn't fit neatly into a category. The diff-the-counts verify step forces every single commit to land somewhere, either in the notes or in the explained-skip list.

## What to customize

Swap the section names (Added / Fixed / Changed) for whatever format your team's release notes already use. Swap the tag reference if you don't use git tags to mark releases.
