---
type: task
mode: HITL
status: open
blocked_by: none
---

# Shepherd upstream PRs #3–#6 through maintainer review

## Question

What review feedback, rebases, or maintainer follow-ups are needed to land upstream PRs #3, #4, #5, and #6 in `grevalyn/youtube-analyzer-skill`?

## Context

Four focused documentation PRs from `tpsp5f5-dev` have been open on `grevalyn/youtube-analyzer-skill` for ~7 days with no maintainer response yet (`@GB525` was pinged on PR #3; CodeRabbit skipped auto-review because the repo has 6 stars):

- **PR #3** (`tpsp5f5-dev/yt-pr-caption-fallback`): HTTP 429 caption fallback (`SKILL.md`).
- **PR #4** (`tpsp5f5-dev/yt-pr-link-status`): 403/429/503 vs 404/410 link status accuracy (`references/evidence-workflow.md`).
- **PR #5** (`tpsp5f5-dev/yt-pr-evidence-gaps`): Missing standalone URL recorded as evidence gap (`references/evidence-workflow.md`).
- **PR #6** (`tpsp5f5-dev/yt-pr-artifact-format`): Markdown link syntax, YAML frontmatter escaping, exact-path verification (`references/evidence-workflow.md`).

## Steps / verification

1. Check mergeability and conflict risk among PRs #4, #5, and #6 — all three touch `skills/youtube-analyzer-skill/references/evidence-workflow.md` near the link-check and artifact sections.
2. Respond to any review comments from `@GB525` and rebase remaining PR branches as soon as the first `evidence-workflow.md` PR merges.
3. Confirm with `@GB525` whether a version bump (`v1.2.1`) and release zip update are desired once the set lands.
4. Record outcomes (merged / revised / closed) and prune merged `tpsp5f5-dev/yt-pr-*` branches from `origin`.
