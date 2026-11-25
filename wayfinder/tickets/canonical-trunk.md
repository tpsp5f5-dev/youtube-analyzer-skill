---
type: grilling
mode: HITL
status: open
blocked_by: none
---

# Should origin/main fast-forward to upstream v1.2.0 before any further fork work?

`origin/main` and this checkout are `5a7c851` (v1.1.0 plus the website blurb). `upstream/main` is `35b0116`, tag v1.2.0. Every commit on the fork is already contained in upstream. The fork README still tells people to install v1.1.0. The four open evidence-rule PRs are already based on v1.2.0, so further branches cut from `origin/main` start one release behind the patches they are trying to carry.

**The question:** Should `origin/main` be fast-forwarded to `upstream/main` now?

**Done when:** A yes or no is recorded. A yes includes the fast-forward on the fork and a check that the root README, the skill README, and `SKILL.md` metadata all say v1.2.0. A no states which tree new fork work is allowed to branch from.
