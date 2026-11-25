---
type: task
mode: AFK
status: open
blocked_by: sync-origin-main-to-v1-2
---

# Audit canonical grevalyn URLs and root vs skill README drift

## Question

Do the `github.com/GB525/youtube-analyzer-skill` URLs in both READMEs still need migrating to `github.com/grevalyn/youtube-analyzer-skill`, and which differences between root `README.md` and `skills/youtube-analyzer-skill/README.md` are accidental drift?

## Context

- Upstream lives at `https://github.com/grevalyn/youtube-analyzer-skill`, yet both root `README.md` and `skills/youtube-analyzer-skill/README.md` (even in v1.2.0 at `35b0116`) still use `https://github.com/GB525/youtube-analyzer-skill/...` for `$skill-installer` and Releases links.
- Root `README.md` includes a `## Website and sample assessment` section (linking to `https://youtube-analyzer-grevalyn.grevalyn.chatgpt.site/` and sample `YTA5a: Matt Pocock Skills Repo`) that is absent from `skills/youtube-analyzer-skill/README.md`, even though the rest of the two files are maintained as near-verbatim mirrors (differing only in relative `LICENSE` and `ATTRIBUTION.md` links).

## Steps / verification

1. Check HTTP redirect behavior for every `GB525/youtube-analyzer-skill` URL in both READMEs (`tree/v1.2.0/...`, `releases/tag/v1.2.0`, etc.) against `grevalyn/youtube-analyzer-skill`.
2. Diff root `README.md` against `skills/youtube-analyzer-skill/README.md` at `upstream/main` (`35b0116`) and classify every delta as intentional (relative paths) vs drift (missing website/sample section, mismatched headings).
3. Verify the external sample site URL (`youtube-analyzer-grevalyn.grevalyn.chatgpt.site`) and Watch links (`bradautomates/claude-video`) return healthy responses.
4. Prepare a clean, focused patch (and optional upstream PR) updating URLs to `grevalyn/youtube-analyzer-skill` and reconciling README parity.
