---
type: grilling
mode: HITL
status: open
blocked_by: sync-fork-to-v1.2.0
---

# How should the four evidence PRs land?

Open PRs #3–#6 each teach one rule from real analyses (429 caption fallback, link-status discipline, missing-URL gaps, artifact link/frontmatter hygiene). A consolidated branch `yt-analyzer-upstream-pr` already combines related wording.

**Question:** After syncing to v1.2.0, should we merge the four PRs separately on the fork, squash them into one contribution aimed at `grevalyn/youtube-analyzer-skill`, or close the individuals and open a single rebased PR from `yt-analyzer-upstream-pr`?
