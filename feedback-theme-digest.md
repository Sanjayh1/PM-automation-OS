# Job search: resume tailoring, maker-checker

**What it does:** A maker sub-agent tailors your resume bullets to a specific job posting. A separate checker sub-agent, with its own independent memory, scores each bullet and blocks anything generic before it ships. This is rows 11-12 on the 20-task map: the same primitives that run your PM job also run your job search.

**Where to run it:** Claude Code, with your resume and the target job posting as files in the same folder.

**What to customize:** Swap the resume filename and posting filename for your own. The checker's bar (specific number, matches the posting's language, verifiable by a stranger) stays the same regardless of role.

---

```
Maker: tailor resume-[yourname].md bullets to posting-[role].md.
Checker: score each bullet, block anything generic, give a reason.
```

## Why two agents, not one

If the same model drafts and grades its own draft, it grades generously. A separate sub-agent with its own memory can't see the maker's excuses. it only sees the bullet and the posting. That independence is what makes the checker's "pass" mean something.

## Sample output (real run, test data)

Maker:
> 1. Owned end-to-end payout formula design for a $18M/week creator payout system, including a Q3 shift to completion-weighted payouts that reduced overpay on low-completion, high-view content.

Checker:
| # | Bullet | Score | Verdict |
|---|---|---|---|
| 1 | Payout formula, $18M/week, Q3 shift | 9/10 | Pass. Specific number, specific mechanism, matches posting's language word for word. |

Blocked from the original resume:
> ❌ "Skills: Roadmapping, SQL, A/B testing, payout/monetization systems...". Blocked. A skills list with zero evidence attached. A checker can't verify "roadmapping" as a skill; it can verify "owned a $18M/week payout system."

## Swap in your own data

Test run used `demo-workspace/job-search/resume-maya-torres.md` and `demo-workspace/job-search/posting-tiktok-monetization-pm.md` (both fictional). To run for real:
- Replace with your actual resume file.
- Replace with the actual job posting you're targeting (paste the text into a file, or point at the URL).
- Run it once per posting. A generic tailored resume defeats the point.
