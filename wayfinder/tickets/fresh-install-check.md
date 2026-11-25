---
type: task
mode: HITL
status: open
blocked_by: canonical-trunk
---

# Does a clean install of the published tag produce the eight-section assessment?

The v1.2.0 README says the skill has been structurally validated and that one 30-second Windows interval exercised local captions, frames, and host-agent inspection. The same README says a full fresh-account installation and every provider/platform combination have not been tested. This fork's README still points installers at v1.1.0, so the check has to wait until the trunk to test is chosen.

**The question:** On a skill directory that does not already contain `youtube-analyzer-skill`, does the documented installer URL for the chosen tag yield a skill whose first run produces the eight chat sections and the evidence files the README names?

**Done when:** One clean install is recorded with the tag, the host (Codex or another), the video URL, whether Watch was used, and which of `analysis.md`, `source-notes.md`, and `link-checks.md` were actually written. A failure is a result, recorded against the step that failed.
