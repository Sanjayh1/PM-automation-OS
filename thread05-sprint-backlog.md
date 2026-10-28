# Loop: spec drift check

**Category:** Event-triggered. **Built and tested:** designed for this pack, following row 9 of the 20-task map. Needs a repo/doc-change connector before its first real run.

**How to use this:** Copy the prompt into Claude Code or a Routine with access to your spec doc and your implementation repo. Fires on a spec edit, not on a clock.

## 1. Trigger
Event-triggered: fires when the linked spec document changes (a webhook from Notion/Confluence/Google Docs, or a repo commit that touches the spec file).

## 2. Skill file (the full prompt)
```
Event-triggered loop: when [spec doc] changes, diff the new version
against the state file's last logged version. Identify what actually
changed (not formatting, the substance). Check whether the current
implementation in [repo] still matches. If it diverges, post the
specific mismatch to the team's Slack channel with a link to both the
spec diff and the code location.
```

## 3. Maker
Diffs the spec, drafts a plain-language description of what changed, checks the current code against the new spec section.

## 4. Checker
Confirms the claimed mismatch is real. points at the exact spec line and the exact code line, not a general "might be out of sync."

## 5. Gate
Only posts on a confirmed implementation mismatch. A spec change that doesn't affect any shipped behavior yet gets logged silently, not broadcast.

## 6. State file
**Where:** `spec-drift-state.md`.
**Read:** the maker reads the last logged spec version to diff against.
**Write:** every trigger appends the new spec version and the mismatch verdict (drift found / no drift).

## What needs a connector
Read access to the spec doc's edit history or a webhook on save, plus read access to the implementation repo. Without the trigger connector, this has to run as a scheduled daily check instead of true event-triggered. still useful, just less immediate.

## Swap in your own data
Point `[spec doc]` and `[repo]` at your actual PRD location and codebase. This loop assumes engineering already has some CI or fix loop that consumes the mismatch report. see `definitions.md`'s graph example for how the two connect.
