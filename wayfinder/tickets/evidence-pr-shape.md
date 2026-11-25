---
type: grilling
mode: HITL
status: open
blocked_by: none
---

# Do the evidence-rule edits land as one patch or as four open PRs?

The same four rules exist twice on GitHub:

- Open PRs #3, #4, #5, and #6, each a one-commit slice on top of upstream `35b0116` (v1.2.0). PRs #4, #5, and #6 all edit `references/evidence-workflow.md` in the same region, so they will not merge as four independent diffs.
- Closed PR #2 (`90dc28b`) already combines the 429 caption fallback, the 403/429/503 versus broken-link distinction, the missing-URL evidence gap, and the clickable-link plus frontmatter rule.

These PRs sit on top of the already-published v1.2.0. They are a follow-on to that release, not the change that creates it.

**The question:** Which shape should be the one asked of the grevalyn maintainer: reopen the combined PR #2, sequence the four open PRs, or replace both with a single new PR?

**Done when:** One shape is chosen, and the other GitHub objects are named as the ones to close or leave untouched.
