---
type: task
mode: HITL
status: open
blocked_by: sync-origin-main-to-v1-2
---

# Build and run cross-platform end-to-end test matrix

## Question

Does v1.2.0 (plus the PR #3–#6 evidence rules) pass a repeatable end-to-end test matrix across fresh installations, operating systems, and known real-world YouTube edge cases?

## Context

- Both READMEs explicitly state: *"A full fresh-account installation and every provider/platform combination have not been tested."*
- v1.2.0's only documented live visual test was a single 30-second YouTube interval on Windows using workspace-local portable binaries (`yt-dlp`, `ffmpeg/ffprobe`).
- Real runs in this fork uncovered recurring failure modes that are easy to regress when editing prompt prose:
  1. Auto-dubbed videos exposing multiple `*-orig` tracks (wrong language selected unless `--sub-lang` is verified).
  2. `yt-dlp` caption downloads hitting HTTP 429 rate limits (5 consecutive runs), requiring fallback to `youtube-transcript-api`.
  3. Link-heavy descriptions (39+ links) returning HTTP 403, 429, and 503 responses alongside named projects with no standalone URL.
  4. Generated artifacts breaking YAML frontmatter escaping or emitting unclickable raw URLs.

## Steps / verification

1. Curate a small public-video test corpus (4–5 stable public YouTube URLs) covering:
   - Auto-dubbed / multi-track captions.
   - Visual-heavy coding or UI demonstration (exercises local Watch frame extraction and `visual-observations.md`).
   - Link-dense description with affiliate/retail/login-walled URLs and a GitHub repository.
   - Lecture/interview where Watch should be skipped and justified in coverage.
2. Execute fresh-install checks across at least two platforms (e.g., macOS and Windows) and three Watch modes: local Watch (`--engine local --no-whisper`), explicit Gemini Watch, and Watch-not-installed fallback.
3. Verify intake behavior for all three stack-comparison choices (`standalone`, `compare`, `never` + one-time override).
4. Record pass/fail results, failure modes, and environment notes (without private transcripts or credentials) so the README's tested-matrix disclaimer can be updated accurately.
