---
type: task
mode: AFK
status: open
blocked_by: land-upstream-prs
---

# Document caption retrieval fallback chain

The skill mentions yt-dlp and PR #3 adds fallback to `youtube-transcript-api` on HTTP 429, but the full fallback chain across different agent environments isn't documented in one place.

**What needs doing:** Write a concise reference (or extend `evidence-workflow.md`) that documents the caption retrieval priority:

1. yt-dlp subtitle extraction (preferred, needs local shell)
2. youtube-transcript-api (fallback for 429, needs Python)
3. Browser/connector retrieval (for agents without shell access)
4. Watch-based transcription (last resort, costs API calls)

Include which agent environments support which methods, common failure modes and their solutions, and how to record provenance for each method.

**Done when:** A clear fallback chain is documented and the SKILL.md references it.
