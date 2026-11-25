---
type: task
mode: HITL
status: open
blocked_by: evidence-pr-shape
---

# After a patch shape is chosen, do all four evidence rules survive on top of v1.2.0?

Someone has to put the chosen text on a branch whose parent is upstream `35b0116` and read the result against v1.2.0's local-review and auto-dub paragraphs. Those paragraphs are easy to clip because the 429 fallback is appended to the same caption step.

**The question:** Does the resulting `SKILL.md` and `references/evidence-workflow.md` contain every rule below, with the v1.2.0 local-review and `--sub-lang` language check still intact?

1. `yt-dlp` HTTP 429 falls back to another caption endpoint such as `youtube-transcript-api`, written as VTT, and a rate limit is recorded as provenance rather than as "no captions."
2. HTTP 403, 429, and retail/affiliate 503 stay distinct from a broken link. Broken is reserved for 404/410 or a confirmed removal.
3. A project named in the description with no standalone URL is an evidence gap. An unrelated repo is not substituted to create a link.
4. Saved artifacts use Markdown links, and generated YAML titles stay plain text with quotes and backslashes escaped.

**Done when:** The branch diff shows those four rules, a read-through confirms the v1.2.0 engine and language-check sentences are still present, and the chosen GitHub PR points at that diff. Merging remains the upstream maintainer's act.
