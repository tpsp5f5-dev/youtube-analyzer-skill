---
type: grilling
mode: HITL
status: open
blocked_by: land-evidence-hardening-prs
---

# Is 429 caption fallback docs-only or a shared recipe?

PR #3 tells agents that an HTTP 429 from `yt-dlp` is not “no captions,” and to try another endpoint (e.g. `youtube-transcript-api`) while recording provenance. That rule was exercised on five rate-limited analyses, but the skill still ships no shared helper.

**Question:** Should the skill stay documentation-only for caption fallback, or should we add a short canonical recipe (commands + expected VTT/provenance shape) that every host agent is expected to follow the same way?
