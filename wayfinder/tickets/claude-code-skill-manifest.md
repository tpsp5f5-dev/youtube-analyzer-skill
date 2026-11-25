---
type: grilling
mode: HITL
status: open
blocked_by: none
---

# Should this skill ship a Claude Code manifest?

The skill currently targets Codex via `agents/openai.yaml` and the `$skill-installer` flow. Claude Code uses a different skill format (`.claude/skills/` with `SKILL.md` frontmatter). This fork lives in a Claude Code workspace, suggesting interest in using it here too.

**The question:** Should we add a Claude Code-compatible skill definition alongside the Codex one? What would that look like — a parallel `agents/claude.md` file, a `.claude/skills/` directory, or something else? Does the SKILL.md already work if placed in the right location, or does it need adaptation for Claude Code's skill discovery?

**Tradeoffs:**
- Adding it broadens the user base but means maintaining two platform targets.
- The skill instructions themselves are platform-agnostic Markdown, so the adaptation may be minimal (just the manifest/discovery mechanism).
- If upstream doesn't want Claude Code support, this becomes a fork-only feature.
