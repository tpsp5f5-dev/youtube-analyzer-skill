---
type: grilling
mode: HITL
status: open
blocked_by: cross-agent-portability-scope
---

# Preferences file schema and cross-platform path contract

## Question

Should `~/.config/youtube-analyzer-skill/preferences.json` have an explicit schema, Windows path rule, and inspect/reset command contract — or stay a minimal prose convention inside `SKILL.md`?

## Context

- Upstream v1.2.0 introduced persistent user preferences outside the skill package at `~/.config/youtube-analyzer-skill/preferences.json`, currently using two keys:
  - `stack_comparison`: `"never"` or `"ask"`
  - `visual_review_engine`: `"local"` or `"gemini"`
- On Windows (where v1.2.0's local Watch test actually ran), `~` expansion differs between PowerShell, Git Bash, WSL, and sandboxed Codex environments, and Windows conventions normally prefer `%APPDATA%` vs `%USERPROFILE%\.config`.
- Today, `SKILL.md` tells the agent to preserve unrelated JSON fields and verify writes, but there is no documented schema, version field, or clear user-facing instructions for inspecting/resetting preferences (beyond asking the agent to resume asking).

## Options to decide between

1. **Keep minimal prose contract:** Leave `SKILL.md` as-is with `~/.config/youtube-analyzer-skill/preferences.json` (expanding `~` to the user's home directory on all OSes) and document a short manual reset snippet in `README.md`.
2. **Formalize schema + OS path resolution:** Document exact allowed keys/values, unknown-key preservation, explicit Windows (`%USERPROFILE%\.config\youtube-analyzer-skill\preferences.json`) resolution, and an explicit "show/reset preferences" prompt convention in `references/`.
3. **Defer until real cross-OS bug reports arrive:** Wait for macOS/Linux/Windows fresh-install test results from `end-to-end-test-matrix-and-eval-corpus` before adding complexity to `SKILL.md`.

## Decision output

Record the contract decision in `wayfinder/MAP.md` (`Decisions so far`) and, if option 1 or 2 is selected, follow up with a targeted docs PR.
