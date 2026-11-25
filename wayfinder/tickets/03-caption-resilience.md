---
type: task
mode: AFK
status: open
blocked_by:
  - 02-align-baseline.md
---

# Can caption failures preserve language and timing without falsely declaring captions absent?

## Evidence

Local instructions distinguish empty responses from transcripts but do not name HTTP 429 fallback behavior. [Open upstream PR #3](https://github.com/grevalyn/youtube-analyzer-skill/pull/3) proposes another caption endpoint and VTT serialization. Upstream PR #1 also reports an incorrect automatic choice among auto-dubbed language tracks.

## Work

Review PR #3 against the selected baseline and update caption guidance with a bounded alternate-method path that respects access restrictions and never silently installs dependencies. Use small synthetic segment fixtures for 429 then success, all methods unavailable, multiple language tracks, overlapping rolling captions and an empty response. Record source, selected language, manual/auto/translated status and timestamps. Preserve any known source-language uncertainty.

## Done when

- Example source notes distinguish rate limiting from confirmed caption absence and identify fallback provenance.
- Converted VTT cues retain start/end times with valid millisecond formatting and no dropped new words.
- The all-failure example remains a bounded assessment, not an invented transcript or an unauthorized provider fallback.
- Sanitized fixtures and expected outputs are available for ticket 08. Synthetic checks are labeled as such, not described as successful live YouTube retrieval.
