---
type: grilling
mode: HITL
status: open
blocked_by: none
---

# Cross-agent portability scope beyond Codex

## Question

Should `youtube-analyzer-skill` remain a Codex-first skill (`$skill-installer`, `agents/openai.yaml`), or should it formally document and support additional Agent Skills runtimes (Claude Code, Cursor, Antigravity / Gemini CLI)?

## Context

- `SKILL.md` itself is written in portable prose with standard frontmatter (`name`, `description`, `metadata.version`), and `skills/youtube-analyzer-skill/` already follows the Agent Skills folder convention.
- However, both READMEs give Codex-only installation and invocation instructions (`Use $skill-installer...`, `Use $youtube-analyzer-skill...`), and `agents/` only contains `openai.yaml`.
- v1.2.0 relies on behaviors that vary across agent harnesses: an interactive user-input prompt tool for the stack-comparison intake question, hidden browser tabs (`visible: false`), and writing `~/.config/youtube-analyzer-skill/preferences.json` outside the workspace sandbox.

## Options to decide between

1. **Stay Codex-first:** Keep install docs and `agents/openai.yaml` scoped to Codex; treat other runtimes as best-effort manual installs without maintaining per-agent instructions.
2. **Document generic Agent Skills install + runtime caveats:** Keep `SKILL.md` tool-agnostic, add a brief multi-agent install note (folder drop-in for Claude Code / Cursor / Gemini CLI), and document graceful degradation when an agent lacks interactive prompt tools or hidden browser tabs.
3. **First-class multi-agent packaging:** Maintain verified install instructions, manifests, and end-to-end test runs per supported agent runtime.

## Decision output

Record the supported runtime boundary in `wayfinder/MAP.md`, which unblocks `preferences-schema-and-cross-platform-paths` and informs the scope of `end-to-end-test-matrix-and-eval-corpus`.
