# Wayfinder map — YouTube Analyzer Skill

Planning artifact for this fork (`tpsp5f5-dev/youtube-analyzer-skill`) of Grevalyn LLC's portable YouTube Analyzer Skill. Tickets live in [`tickets/`](tickets/).

## Destination

Ship a trustworthy, installable agent skill that turns a YouTube URL into a complete in-chat assessment: captions + expanded description + checked links/repos + optional Watch visuals — with honest evidence coverage and no invented gaps filled.

For this fork specifically: absorb upstream **v1.2.0**, land the open evidence-hardening doc PRs without fragmenting history, keep install pins accurate, and decide how much of the fork's fieldwork (429 caption fallback, link-status discipline, artifact formatting) should be proposed back to `grevalyn/youtube-analyzer-skill`.

## Notes

- **What it is:** Instruction workflow under `skills/youtube-analyzer-skill/` (`SKILL.md`, `references/evidence-workflow.md`, `agents/openai.yaml`, READMEs). Not an app; agents execute the skill with their own tools.
- **Maintainer / license:** Grevalyn LLC, MIT. Optional Watch dependency is separate (`bradautomates/claude-video`); no Watch code is bundled.
- **Public surface:** Website + sample assessment (YTA5a: Matt Pocock Skills Repo) linked from README; install via Codex `$skill-installer` or zip from Releases.
- **Version skew on this checkout:** Working tree and `SKILL.md` metadata still say **1.1.0** and pin install URLs to `v1.1.0`, while `upstream/main` and GitHub Releases already publish **v1.2.0** (stack comparison opt-in, host-agent visual defaults, auto-dubbed caption language checks, updated install links).
- **Open fork PRs (docs-only, each exercised on real analyses):**
  - #3 caption fallback when `yt-dlp` returns HTTP 429
  - #4 distinguish restricted/rate-limited/bot-protected links from *broken*
  - #5 missing standalone URLs → evidence gaps (no fake substitute links)
  - #6 clickable Markdown links + valid YAML frontmatter in saved artifacts
- **Consolidated sibling branch:** `tpsp5f5-dev/yt-analyzer-upstream-pr` merges the evidence rules; sibling agent worktrees (`yt-claude`, `yt-codex`, `yt-hermes`, etc.) exist for multi-agent packaging experiments.
- **Stated validation gap (upstream README):** structurally validated; predecessor exercised on a real video; full fresh-account install and every provider/platform combo **not** tested.
- **Hard boundaries already decided in skill text:** do not install/run linked repos to “verify”; do not publish/message/change standards from an analysis; Watch optional — transcript-only must still be useful; chat is the deliverable, files are archival.

## Decisions so far

- Analysis belongs **in chat**; Markdown under `outputs/` is supporting evidence, not a substitute for the answer.
- Prefer **targeted Watch clips** over whole-video processing; ~10–15 minute sections when broad review is justified (practical default, not a provider guarantee).
- Caption preference order: original-language human → original-language auto → flag translations; never call a summary or Gemini report a verbatim transcript.
- Upstream v1.2.0 direction: **stack comparison is opt-in**; default visual checks lean on host-agent review rather than assuming Gemini.
- Fork strategy so far: small documentation PRs that encode lessons from live analyses, rather than shipping retrieval code inside the skill.

## Not yet specified

- Whether this fork's four evidence PRs should merge as-is, squash into one upstream contribution, or wait until the tree is rebased onto v1.2.0.
- Whether caption **429 fallback** stays documentation-only (“try another endpoint”) or needs a canonical tool/script recommendation agents can share.
- Fresh-account install matrix: which agents (Codex, Claude Code, Cursor, Hermes, …), which OS shells, and what counts as pass/fail.
- How aggressively to support non-Codex install paths (Cursor skills folders, Claude skills sync, zip-only) in the primary README.
- Policy for when Watch is unavailable vs when the host agent can do local frame review — especially after v1.2.0's host-agent default.
- Release ownership on the fork: keep tracking Grevalyn tags only, or cut fork tags when evidence rules diverge.
- Whether the marketing site / sample assessment needs a companion update when evidence rules change.

## Out of scope

- Bundling Watch, Gemini keys, or any provider credentials in this repository.
- Building a standalone GUI, API server, or scheduled crawler around the skill.
- Executing or installing third-party repos discovered in video descriptions as part of “analysis.”
- Bypassing login walls, CAPTCHAs, or TLS checks to force caption/link retrieval.
- Replacing Grevalyn's product identity or claiming affiliation with YouTube/GitHub/Gemini/Codex.
- Opening a pull request for this wayfinder branch (artifact only; coordinator owns PR timing).
