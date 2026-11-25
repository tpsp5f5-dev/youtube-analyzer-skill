---
type: task
mode: AFK
status: open
blocked_by: fork-sync-and-upstream-strategy
---

# Sync origin/main to upstream v1.2.0 and prune closed PR #2 branch

## Question

Can `origin/main` be cleanly fast-forwarded to `upstream/main` (`35b0116`, v1.2.0) and can the superseded branch `tpsp5f5-dev/yt-analyzer-upstream-pr` (`90dc28b`, closed PR #2) be deleted with zero lost changes?

## Context

- `origin/main` (`5a7c851`) is an ancestor of `upstream/main` (`35b0116`), so fast-forwarding is conflict-free.
- PR #2 (`90dc28b`) was explicitly closed as superseded by PRs #3 (`1997854`), #4 (`eacab8e`), #5 (`ca0e252`), and #6 (`1311518`), but its remote branch still sits on `origin`.
- Until `origin/main` advances to v1.2.0, every new branch or worktree cut from `origin/main` starts from stale v1.1.0 files.

## Steps / verification

1. Diff `90dc28b` against the combined diffs of `1997854`, `eacab8e`, `ca0e252`, and `1311518` to confirm no wording or rule from PR #2 was dropped during the split.
2. Fetch latest `upstream` and fast-forward `main` to `upstream/main` (`35b0116` or newer), then push `main` to `origin` (and create the integration branch if chosen in `fork-sync-and-upstream-strategy`).
3. Delete `tpsp5f5-dev/yt-analyzer-upstream-pr` locally and on `origin` once step 1 confirms full coverage.
4. Verify `git rev-list --left-right --count origin/main...upstream/main` reports `0	0` (or matches the chosen strategy).
