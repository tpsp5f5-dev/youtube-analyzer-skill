# Wayfinder Map: youtube-analyzer-skill

> Fork `tpsp5f5-dev/youtube-analyzer-skill` of upstream `grevalyn/youtube-analyzer-skill` (maintained by Grevalyn LLC / `@GB525`, MIT licensed).

## Destination

Deliver a reliable, portable, instruction-only agent skill (`youtube-analyzer-skill`) that produces evidence-backed YouTube video assessments directly in chat — with verified captions, expanded descriptions, accurately classified resource/GitHub link checks, opt-in stack comparison, and targeted local or Gemini visual review via the optional Watch skill — while keeping this fork cleanly aligned with upstream `grevalyn/youtube-analyzer-skill` and landing field-tested evidence-hardening improvements (upstream PRs #3–#6) plus repeatable validation and cross-platform verification.

## Notes

- **Repository shape:** Pure documentation/instruction skill with zero runtime application code. Core files live under `skills/youtube-analyzer-skill/` (`SKILL.md`, `README.md`, `ATTRIBUTION.md`, `LICENSE`, `agents/openai.yaml`, `references/evidence-workflow.md`), alongside root `README.md`, `LICENSE`, `.gitignore`, and `.gitattributes` (LF endings for `*.md` and `*.yaml`).
- **Fork lag behind upstream:** `origin/main` is at `5a7c851` (**v1.1.0**, 2026-10-09), four commits behind `upstream/main` at `35b0116` (**v1.2.0**, 2026-10-10). Upstream v1.2.0 (PR #1, merged) shipped opt-in stack comparison intake, `~/.config/youtube-analyzer-skill/preferences.json`, default local host-agent frame-and-caption review (`--engine local --no-whisper`), hidden muted/paused browser rules, auto-dubbed caption language verification (`--sub-lang`), and `visual-observations.md`.
- **Open upstream PRs from this fork:** Four focused documentation PRs against `upstream/main` (`35b0116`), split from closed omnibus PR #2 (`tpsp5f5-dev/yt-analyzer-upstream-pr`, `90dc28b`), await maintainer `@GB525` review:
  - **PR #3** (`1997854`, `SKILL.md`): HTTP 429 caption fallback to alternate endpoint (e.g., `youtube-transcript-api` written as VTT cues) — encountered on 5 consecutive real analyses.
  - **PR #4** (`eacab8e`, `evidence-workflow.md`): Distinguish HTTP 403 (restricted/login), 429 (rate-limited), and 503 (bot protection) from genuinely broken links (404/410) — exercised on a 39-link description.
  - **PR #5** (`ca0e252`, `evidence-workflow.md`): Record named projects without a standalone description URL as evidence gaps instead of substituting unrelated repos/mirrors.
  - **PR #6** (`1311518`, `evidence-workflow.md`): Require Markdown `[label](url)` links in saved artifacts, plain-text escaped YAML frontmatter, and exact-path verification instead of broad globs.
  - Note: PRs #4, #5, and #6 all edit `skills/youtube-analyzer-skill/references/evidence-workflow.md`, so merging any one may require rebasing the others.
- **Documentation and URL drift:** Both root `README.md` and `skills/youtube-analyzer-skill/README.md` (including in upstream v1.2.0) still point install and release links to `github.com/GB525/youtube-analyzer-skill` rather than the canonical `github.com/grevalyn/youtube-analyzer-skill` org URL. Root `README.md` also includes `## Website and sample assessment` (linking to `youtube-analyzer-grevalyn.grevalyn.chatgpt.site` and sample `YTA5a`), which is missing from `skills/youtube-analyzer-skill/README.md`.
- **Validation and test coverage gaps:** There is no CI workflow, automated validator, or regression eval harness. PR #1 was validated manually (Codex skill validator, YAML parse, git whitespace check, and one 30-second Windows local Watch interval with portable binaries). Both READMEs explicitly note that fresh-account installations and other OS/agent/provider combinations remain untested.
- **Platform constraints:**
  - `origin` (`tpsp5f5-dev/youtube-analyzer-skill`) has GitHub Issues disabled; `upstream` has 0 issues and 6 stars (below CodeRabbit's 10-star auto-review threshold).
  - Watch (`bradautomates/claude-video`) is an external, separately installed MIT dependency; no Watch code, credentials, or installer is bundled here. Current Watch may download a full video even for a short interval.
  - Evidence boundaries are strict: analysis never authorizes executing linked repo code, installing linked tools, modifying saved Watch settings, mutating browser autoplay defaults, or exposing credentials/tokens.

## Decisions so far

- **Chat-first deliverable:** The complete 8-section analysis belongs in chat and must stand alone; Markdown artifacts under `outputs/` (`analysis.md`, `source-notes.md`, `link-checks.md`, `watch-report-N.md`, and `visual-observations.md` in v1.2.0) are archival evidence, not the required reading UI.
- **No bundled third-party code or secrets:** Watch remains separately installed; personal preferences (`~/.config/youtube-analyzer-skill/preferences.json`) and credentials stay outside the distributable skill package.
- **Opt-in stack comparison (upstream v1.2.0):** Personal project/prior-assessment research requires explicit opt-in at intake; default is standalone (`No, standalone (quicker)`), with an explicit `Never compare (remember this)` option.
- **Local host-agent visual review as default (upstream v1.2.0):** Analyzer visual checks default to `--engine local` (and `--no-whisper` when captions exist) via per-run override without overwriting standalone Watch settings or silently switching engines after failure.
- **Split upstream contributions:** Omnibus PR #2 was closed in favor of four atomic, reviewable PRs (#3–#6) scoped cleanly to documentation rules without version bumps.
- **Read-only static repo inspection:** Evaluating linked GitHub repositories inspects files/metadata only — never installs or runs repository code.

## Not yet specified

- **Fork branching model:** Whether `tpsp5f5-dev/youtube-analyzer-skill` should keep `origin/main` strictly synced to `upstream/main` or maintain a combined integration branch carrying PRs #3–#6 while upstream review is pending.
- **Target agent runtimes:** Whether the skill remains Codex-first (`$skill-installer`, `agents/openai.yaml`) or formally documents and validates installation/behavior across other Agent Skills runtimes (Claude Code, Cursor, Antigravity/Gemini CLI).
- **Preferences contract & cross-platform paths:** Whether `~/.config/youtube-analyzer-skill/preferences.json` should have a formal schema, explicit Windows path guidance (`%USERPROFILE%\.config` vs `%APPDATA%`), and a documented inspect/reset flow.
- **Automated quality bar:** What CI checks should gate PRs (YAML/frontmatter linting, README parity, version-tag alignment, release zip + `SHA256SUMS.txt` verification) and whether prompt-regression testing against a fixed public-video corpus should be maintained in-repo.
- **Release & versioning cadence:** Whether PRs #3–#6 (if merged upstream) trigger a `v1.2.1` patch release or roll into a larger `v1.3.0` release alongside README/URL fixes and CI.
- **Watch partial-download workaround:** Whether the skill should stay hands-off while Watch downloads full videos for short intervals, or document/test clip-bounded extraction options when Watch supports them.

## Out of scope

- **Bundling or forking Watch:** No `claude-video` code, `yt-dlp`/`ffmpeg` binaries, API keys, or automated Watch installers belong in this repository.
- **Turning the skill into a standalone CLI/web app:** This project is a portable agent instruction workflow, not a hosted service, scraper daemon, or standalone application.
- **Automated code execution on analyzed repos:** Installing, building, or running tests inside linked GitHub repositories during video assessment is explicitly disallowed.
- **Personal stack data or private assessments:** No personal project histories, private transcripts, cookies/authenticated browser sessions, or user-specific preferences may be committed or packaged.
- **Bypassing access controls or rate limits improperly:** Disabling TLS verification, rotating auth cookies, or scraping behind login walls to force caption/link retrieval is out of bounds.

## Ticket index

| Ticket | Type | Mode | Status | Blocked by |
| --- | --- | --- | --- | --- |
| [fork-sync-and-upstream-strategy](tickets/fork-sync-and-upstream-strategy.md) | grilling | HITL | open | none |
| [upstream-pr-shepherding](tickets/upstream-pr-shepherding.md) | task | HITL | open | none |
| [cross-agent-portability-scope](tickets/cross-agent-portability-scope.md) | grilling | HITL | open | none |
| [sync-origin-main-to-v1-2](tickets/sync-origin-main-to-v1-2.md) | task | AFK | open | fork-sync-and-upstream-strategy |
| [fix-canonical-repo-urls-and-readme-drift](tickets/fix-canonical-repo-urls-and-readme-drift.md) | task | AFK | open | sync-origin-main-to-v1-2 |
| [add-skill-validation-ci](tickets/add-skill-validation-ci.md) | task | AFK | open | sync-origin-main-to-v1-2 |
| [end-to-end-test-matrix-and-eval-corpus](tickets/end-to-end-test-matrix-and-eval-corpus.md) | task | HITL | open | sync-origin-main-to-v1-2 |
| [preferences-schema-and-cross-platform-paths](tickets/preferences-schema-and-cross-platform-paths.md) | grilling | HITL | open | cross-agent-portability-scope |
