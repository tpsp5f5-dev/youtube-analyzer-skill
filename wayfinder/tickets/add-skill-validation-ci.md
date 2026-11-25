---
type: task
mode: AFK
status: open
blocked_by: sync-origin-main-to-v1-2
---

# Add automated skill validation and release-check CI

## Question

Can we build a lightweight, dependency-minimal validation script and GitHub Actions workflow that automates every structural check currently done by hand on releases?

## Context

- The repository has no `.github/workflows/`, linter, or packaging check.
- Upstream PR #1's validation section relied on manual runs of Codex skill validation, `agents/openai.yaml` parsing, and git whitespace checks, plus manual zip + `SHA256SUMS.txt` release assembly.
- Because the skill's surface area is small and strict (YAML frontmatter in `SKILL.md`, Codex manifest in `agents/openai.yaml`, version tags repeated across two READMEs, relative links, LF line endings via `.gitattributes`), regressions are easy to catch deterministically.

## Steps / verification

1. Implement a portable validation script (e.g., Python stdlib or POSIX shell) checking:
   - `skills/youtube-analyzer-skill/SKILL.md` frontmatter parses and contains non-empty `name`, `description`, and semver `metadata.version`.
   - `skills/youtube-analyzer-skill/agents/openai.yaml` parses and defines `interface.display_name`, `short_description`, `default_prompt`, and `policy.allow_implicit_invocation`.
   - Version strings match across `SKILL.md` and install/release URLs in both `README.md` files (with an explicit opt-out or warning during unreleased dev work).
   - Every relative Markdown link resolves to an existing file in the repo and inside the packaged `skills/youtube-analyzer-skill/` folder.
   - All `*.md` and `*.yaml` files use LF endings and have no trailing whitespace (`git diff --check` equivalent).
   - No forbidden local/private files (`preferences.json`, `.env`, `outputs/`, `work/`) are tracked.
2. Add a GitHub Actions workflow running the validator on pushes and PRs.
3. Verify the script passes cleanly against `upstream/main` (`35b0116`) and catches an intentional broken link or version mismatch in a dry run.
