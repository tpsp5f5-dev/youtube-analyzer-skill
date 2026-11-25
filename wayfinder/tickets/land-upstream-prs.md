---
type: task
mode: HITL
status: open
blocked_by: none
---

# Land the four open upstream PRs

Four documentation PRs from this fork are open against `grevalyn/youtube-analyzer-skill`:

- PR #3: caption fallback for HTTP 429
- PR #4: distinguish restricted links from broken links
- PR #5: record missing standalone URLs as evidence gaps
- PR #6: require clickable links and valid artifact frontmatter

**What needs doing:** Follow up with the upstream maintainer to get these reviewed and merged. If upstream is unresponsive after a reasonable period, decide whether to maintain them as a local patch set on the fork. Check for merge conflicts if upstream has advanced.

**Done when:** All four PRs are merged upstream, or a conscious decision is made to carry them locally with a rebase strategy documented.
