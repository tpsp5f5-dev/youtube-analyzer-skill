---
type: task
mode: AFK
status: open
blocked_by:
  - 02-align-baseline.md
---

# Can saved artifacts remain readable, safe and verifiable by exact path?

## Evidence

The reference defines analysis.md, source-notes.md, link-checks.md and optional Watch reports but has no local examples or validator. [Open PR #6](https://github.com/grevalyn/youtube-analyzer-skill/pull/6) proposes clickable URLs, valid optional YAML and exact-path checks to avoid backup-file confusion.

## Work

Add sanitized examples and precise output guidance for the selected baseline. Exercise quotes, backslashes and colons in titles, timestamp links, metadata URLs, optional YAML URL fields, sensitive query values, no-Watch cases and similarly named backup reports. Keep optional frontmatter optional. If the adopted baseline includes host-agent local review, distinguish visual-observations.md from the extraction report.

## Done when

- Markdown prose URLs are clickable, any YAML frontmatter parses, and generated values retain intended text without leaking tokens.
- Verification reads the exact intended artifact paths and cannot mistake a backup for the current report.
- The chat/analysis example has matching substantive judgments and coverage, and no empty Watch report is created when visual review was unnecessary.
- Synthetic fixtures and expected results are available for ticket 08, with no copyrighted full captions or personal project history.
