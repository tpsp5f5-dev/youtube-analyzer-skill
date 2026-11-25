# Wayfinder Map — YouTube Analyzer Skill

## Destination

Ship a robust, well-tested YouTube Analyzer Skill that any Claude/Codex user can install and trust for thorough, evidence-backed video assessments. The fork (tpsp5f5-dev) stays current with upstream (grevalyn), lands the four open documentation PRs, and extends the skill toward broader agent-platform support, automated testing, and a smoother installation experience.

## Notes

- **What it is:** A Claude skill (instruction workflow, not an application) that analyzes YouTube videos using captions, description links, GitHub repo inspection, and optional Watch visual review. Maintained by Grevalyn LLC, MIT licensed.
- **Current state:** v1.1.0 released. Two commits on main. The skill works in Codex with the `$skill-installer` flow. A companion website exists at `youtube-analyzer-grevalyn.grevalyn.chatgpt.site`.
- **Fork relationship:** `origin` is `tpsp5f5-dev/youtube-analyzer-skill`, `upstream` is `grevalyn/youtube-analyzer-skill`. Four open PRs from this fork target upstream — all documentation-only improvements drawn from real analysis sessions (caption fallback for 429, link-status semantics, evidence gaps for missing URLs, artifact frontmatter validation).
- **Key files:** `skills/youtube-analyzer-skill/SKILL.md` (main skill instructions), `references/evidence-workflow.md` (link/repo/artifact procedures), `agents/openai.yaml` (Codex agent config).
- **Dependencies:** Watch (optional, separately installed from bradautomates/claude-video), yt-dlp or equivalent for captions, web access for link checking, Gemini API key if using Watch's Gemini engine.
- **No runtime code:** The repo contains only Markdown instructions, YAML config, and documentation. There is no application code, no tests, no CI.

## Decisions so far

1. **Fork from upstream** to propose improvements via PRs rather than direct push.
2. **v1.1.0 tagged release** as the portable, pinned installation target.
3. **Watch remains optional** — the skill must produce a useful assessment without it.
4. **Targeted clips preferred** over whole-video Watch processing (10–15 min sections).
5. **Documentation PRs from real usage** — all four open PRs came from actual video analysis sessions encountering real edge cases.
6. **Codex as primary platform** — the `agents/openai.yaml` and `$skill-installer` flow target Codex/OpenAI agents.

## Not yet specified

- **Claude Code / Orca integration:** The skill targets Codex via `agents/openai.yaml` and `$skill-installer`. No equivalent Claude Code skill manifest or installation path exists. Whether to add one (and what it looks like) is undecided.
- **Automated testing:** There is no way to validate that a skill change doesn't break analysis quality. No test harness, no example inputs/outputs, no CI pipeline.
- **Upstream PR merge strategy:** The four open PRs are sitting unreviewed. No process exists for following up, rebasing, or handling divergence if upstream evolves independently.
- **Version management:** How to bump versions, what constitutes a breaking change to a skill (instruction changes can alter behavior), and whether to maintain a changelog.
- **Multi-platform support:** Whether to support other agent platforms beyond Codex (Claude Code, custom agent frameworks, etc.) and what that means for the skill format.
- **Caption retrieval resilience:** The skill mentions yt-dlp and fallback, but the actual toolchain for caption retrieval across different agent environments is unspecified.
- **Website maintenance:** The companion website's relationship to the repo (generated? manual? synced?) and its update process.

## Out of scope

- Building a standalone application or API — this is an instruction skill, not software.
- Watch development or maintenance — that's bradautomates' project.
- YouTube API quota management or proxy infrastructure.
- Monetization, billing, or commercial licensing beyond MIT.
- Upstream repository governance — we propose PRs but don't control merge decisions.
