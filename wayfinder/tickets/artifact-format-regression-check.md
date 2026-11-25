---
type: task
mode: AFK
status: open
blocked_by: land-evidence-hardening-prs
---

# Regression-check saved artifact formatting rules

PR #6 requires Markdown link syntax for URLs in saved artifacts, plain titles in YAML frontmatter, escaped quotes/backslashes, and verification by exact path (not globs that hit backups). Easy to break once agents generate real `outputs/` trees.

**Question:** After the artifact-format wording is merged, can we generate one sample `analysis.md` / `link-checks.md` / frontmatter-bearing note and confirm links render, YAML parses, and exact-path verification would catch a backup-glob false positive?
