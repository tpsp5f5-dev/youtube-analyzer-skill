---
type: task
mode: AFK
status: open
blocked_by: review-and-merge-hardening-prs
---

# Create a reproducible test fixture for the skill

The skill has been "structurally validated" but there's no repeatable way to verify it works. A test fixture would use a known public video (stable, unlikely to be deleted) with pre-captured expected outputs: caption availability, description links, expected section headings, and key claims.

**Question:** Build a test fixture under `tests/` or `fixtures/` with a reference video ID, its expected metadata, a golden-path checklist an agent can self-score against, and instructions for running a smoke test manually or via an agent.
