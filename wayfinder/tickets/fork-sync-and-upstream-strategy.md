---
type: grilling
mode: HITL
status: open
blocked_by: none
---

# Fork sync and upstream integration strategy

## Question

Should `tpsp5f5-dev/youtube-analyzer-skill` keep `origin/main` as a strict fast-forward mirror of `upstream/main`, or maintain an integration branch (or diverged `main`) carrying PRs #3–#6 until `@GB525` reviews them?

## Context

- `origin/main` is currently at `5a7c851` (v1.1.0), four commits behind `upstream/main` (`35b0116`, v1.2.0).
- Four open PRs from this fork (`#3`, `#4`, `#5`, `#6`) are based directly on `upstream/main` (`35b0116`) and have had no maintainer review yet.
- The superseded omnibus branch `tpsp5f5-dev/yt-analyzer-upstream-pr` (`90dc28b`, closed PR #2) still exists on `origin`.
- Any new work branched from `origin/main` today (like v1.1.0 worktrees) misses all v1.2.0 changes (opt-in stack comparison, local host-agent review, auto-dubbed caption verification).

## Options to decide between

1. **Strict upstream mirror + optional local integration branch:** Fast-forward `origin/main` to `upstream/main` (`35b0116`), keep `origin/main` untouched by fork-only commits, and optionally maintain a separate `fork-integration` branch combining `v1.2.0` + PRs #3–#6 for local daily installs.
2. **Soft fork on `origin/main`:** Fast-forward `origin/main` to `upstream/main`, then merge PRs #3–#6 onto `origin/main` so anyone installing from `tpsp5f5-dev` gets the hardened rules immediately (accepting rebase/merge maintenance when upstream moves).
3. **Wait on upstream:** Fast-forward `origin/main` to `upstream/main` and do not maintain a combined branch until `@GB525` responds to PRs #3–#6.

## Decision output

Record the chosen branching model in `wayfinder/MAP.md` (`Decisions so far`), which unblocks `sync-origin-main-to-v1-2`.
