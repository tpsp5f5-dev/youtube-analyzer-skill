---
type: task
mode: AFK
status: open
blocked_by: canonical-trunk
---

# Do the README install pins and SKILL.md version match the trunk, and do they spell the GitHub owner as grevalyn?

On this branch, `README.md` and `skills/youtube-analyzer-skill/README.md` both tell Codex to install `https://github.com/GB525/youtube-analyzer-skill/tree/v1.1.0/skills/youtube-analyzer-skill`, and `SKILL.md` says `version: "1.1.0"`. On `upstream/main` those three say v1.2.0 and the URLs still spell `GB525`. `gh repo view GB525/youtube-analyzer-skill` returns `grevalyn/youtube-analyzer-skill`.

**The question:** After the fork is on the chosen trunk, do the root README, the skill README, and `metadata.version` name one version, and do the install URLs and the release link spell `grevalyn`?

**Done when:** A diff (or a note that no diff is required) shows one version string across those three places and one owner spelling in every install URL. The release zip filename matches that version.
