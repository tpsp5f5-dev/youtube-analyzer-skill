# Wayfinder Map — YouTube Analyzer Skill

## Destination

Ship YouTube Analyzer Skill v1.2 with the four open hardening PRs merged, broader agent-platform compatibility beyond Codex/OpenAI, and a reproducible test harness that proves the skill works end-to-end on a real video without manual verification. The project should be installable on at least two agent platforms, have its evidence workflow battle-tested against common failure modes (rate limits, missing captions, restricted links), and carry enough documentation that a new contributor can run a full assessment within 30 minutes of cloning.

## Notes

- **Current state:** v1.1.0 released. Two commits on main. The skill is a pure-instruction workflow (markdown files, no code) designed for Codex-compatible agents with web access.
- **Open PRs (4):** All are docs-category hardening changes on the `tpsp5f5-dev` fork:
  - PR #3 — caption fallback for HTTP 429
  - PR #4 — distinguish restricted links from broken links
  - PR #5 — record missing standalone URLs as evidence gaps
  - PR #6 — require clickable links and valid artifact frontmatter
- **Closed PR #2** was superseded by the four above (same author split the work).
- **Merged PR #1** added opt-in stack comparison and host-agent visual review (became v1.1.0).
- **No issues filed** on the repo. Feedback channel is GitHub Issues per README.
- **Watch dependency** is optional, third-party (bradautomates/claude-video), MIT-licensed. The skill works without it but must label visual gaps.
- **Agent config:** Only `agents/openai.yaml` exists. No Claude, Gemini, or generic agent config.
- **No tests or CI.** Validation is manual ("structurally validated; predecessor exercised on a real video").
- **Website** exists at a ChatGPT Sites domain (`youtube-analyzer-grevalyn.grevalyn.chatgpt.site`), hosting a sample assessment.

## Decisions so far

1. **Instruction-only architecture.** The skill is pure markdown instructions, not code. This keeps it portable but means agent compliance varies.
2. **Watch is optional.** Visual review depends on a separately installed third-party skill. The analyzer degrades gracefully without it.
3. **Tagged version installs.** README directs users to install from a specific git tag, not HEAD, to avoid unreviewed changes.
4. **Evidence saved to filesystem.** When file tools are available, analysis/source-notes/link-checks/watch-reports are saved. Otherwise chat-only.
5. **Hardening split into four PRs.** The original monolithic PR #2 was closed and split into PRs #3–6 for reviewability.
6. **MIT license.** Permissive, Grevalyn LLC copyright.

## Not yet specified

- **Multi-platform agent support.** Only OpenAI/Codex agent config exists. How should the skill adapt for Claude Code, Gemini agents, or other platforms? What differs per platform?
- **Testing strategy.** No automated or semi-automated way to verify the skill produces correct output on a known video. What does a "test" look like for a pure-instruction skill?
- **PR merge plan.** The four open PRs have been open since Nov 17. No review activity visible. Who reviews, what's the merge order, are there conflicts?
- **v1.2 scope.** PR #1's merge message mentions "v1.2 intake" but no roadmap or milestone defines what v1.2 includes beyond the open PRs.
- **Caption extraction reliability.** The skill mentions yt-dlp and various fallbacks but doesn't specify which extraction methods are tested or recommended per platform.
- **Rate limiting / API quotas.** PR #3 adds 429 fallback, but broader rate-limit strategy (YouTube API quotas, Watch/Gemini costs) is undocumented.
- **Community contribution model.** README says "open an issue" but there's no CONTRIBUTING.md, no issue templates, no branch protection visible.

## Out of scope

- Building a code-based application or API wrapper around the skill.
- Modifying the Watch dependency or forking claude-video.
- Hosting, deployment, or infrastructure for the ChatGPT Sites website.
- YouTube API key management or credential provisioning.
- Commercializing or monetizing the skill beyond its current open-source model.
