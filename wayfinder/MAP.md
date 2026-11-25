# Wayfinder Map — YouTube Analyzer Skill

## Destination

A portable instruction skill, published from `grevalyn/youtube-analyzer-skill`, that a skill host installs from a pinned tag and runs to deliver a full YouTube assessment in chat: caption provenance, the expanded description, checked links, a bounded read of linked GitHub repositories, optional Watch visual review, and saved evidence files.

Upstream `main` is already that product at v1.2.0: opt-in comparison with prior work, local frame-and-caption review, and an explicit auto-dub language check. The next stretch is to land the evidence-rule hardening that is written and still unmerged, bring this fork's `main` up to that upstream line, and decide whether the machine-local Hermes v1.2.1 overlay (extra references, Obsidian mirror, watcher) ever becomes a public release.

## Notes

- This checkout, branch `tpsp5f5-dev/yt-grok` at `5a7c851`, matches `origin/main`. It is the v1.1.0 release plus the website blurb in the root README. `git log upstream/main..HEAD` is empty. `git log HEAD..upstream/main` is four commits, ending at `35b0116` ("Publish v1.2.0 installation and download links"). Upstream tags are `v1.1.0` and `v1.2.0`. This fork has no GitHub releases, and issues are disabled.
- Remotes: `origin` is `tpsp5f5-dev/youtube-analyzer-skill` (fork of grevalyn). `upstream` is `grevalyn/youtube-analyzer-skill`. `gh repo view GB525/youtube-analyzer-skill` resolves to `grevalyn/youtube-analyzer-skill`. The v1.2.0 README install links still spell `github.com/GB525/youtube-analyzer-skill`.
- The published tree is Markdown plus `skills/youtube-analyzer-skill/agents/openai.yaml`. Procedure lives in `SKILL.md` and `references/evidence-workflow.md`. There is no application code, test suite, or CI.
- On upstream, `SKILL.md` metadata `version` is `"1.2.0"`. The root README and the skill README both pin the installer to `tree/v1.2.0` and the zip `youtube-analyzer-skill-v1.2.0.zip`. The same files on this branch still pin v1.1.0.
- The v1.2.0 README records structural validation, plus one exercise of local caption retrieval, frame extraction, and host-agent inspection on a 30-second Windows interval. It also records that a full fresh-account installation and every provider/platform combination remain untested. Auto-dubbed caption selection needed an explicit English track; the published skill now requires a language check before analysis.
- Open against grevalyn, all one commit past `35b0116`, opened 2026-11-17:
  - PR #3 adds a `yt-dlp` HTTP 429 caption fallback (`youtube-transcript-api`, written as VTT) in `SKILL.md`.
  - PR #4 keeps HTTP 403, 429, and 503 distinct from a broken link in `references/evidence-workflow.md`.
  - PR #5 records a named resource with no standalone URL as an evidence gap.
  - PR #6 requires Markdown links in saved artifacts and valid YAML frontmatter.
  - PRs #4, #5, and #6 edit the same region of `evidence-workflow.md`.
- Closed PR #2 (`90dc28b` on `tpsp5f5-dev/yt-analyzer-upstream-pr`) already contains those four edits in one diff and was not merged.
- The copy installed at `~/.agents/skills/youtube-analyzer-skill` is a different text. Its frontmatter says `version: 1.2.1` and `author: Hermes`. It cites `references/procedure.md`, `verification.md`, `watcher-operations.md`, `mirror-report-format.md`, `link-check-troubleshooting.md`, and `scripts/watch_youtube_analyzer.sh`. Those files exist in that install directory. They do not exist on `upstream/main` or on this branch. The installed `SKILL.md` also names `/Users/toddsutton/.hermes/scripts/watch_youtube_analyzer.sh` and the vault directory `/Users/toddsutton/Local/Obsidian/Work-Zachry/AgentOS/Memory_Layer/10_Processed_Memory/`.
- Watch stays a separate install from `bradautomates/claude-video`. This repo ships no Watch code and no credentials. v1.2.0 defaults analyzer visual checks to local frame-and-caption review through `visual_review_engine`, and tells the agent to pass `--engine local` and, when captions already exist, `--no-whisper`.
- The website `https://youtube-analyzer-grevalyn.grevalyn.chatgpt.site/` and the sample assessment YTA5a (Matt Pocock Skills Repo) are linked from the README. Their source is not in this repo.
- Artifact names in the published workflow: `analysis.md`, `source-notes.md`, `link-checks.md`, `watch-report-N.md`, and for local review `visual-observations.md`, under `outputs/<video-specific-subfolder>/`. Run-folder naming and the Obsidian mirror are specified only in the Hermes overlay.

## Decisions so far

- The complete assessment is delivered in chat. Saved Markdown is the archive. A Word or PDF copy is produced only when someone asks for one.
- The skill stays an instruction workflow under the MIT license, copyright Grevalyn LLC, adapted from that company's YouTube Transcript Analyzer. It does not require the original plugin.
- Watch is optional, unbundled, and attributed to Bradley Bonanno / bradautomates. An assessment built from captions and checked links must still be useful when Watch is absent.
- v1.2.0 made comparison with prior work opt-in. Standalone recommendations are the default when no project history was provided.
- v1.2.0 defaulted analyzer visual review to local frame-and-caption inspection by the host agent. Gemini runs on an explicit choice. The skill does not silently switch engines, and it does not rewrite Watch's own saved settings. `setup.py --engine local` is avoided because it changes Watch's saved engine.
- Caption selection prefers original-language human captions, then original-language automatic captions. The selected track's language is checked against the source. An `*-orig` suffix is not treated as proof of the source language. A known track is selected with Watch's `--sub-lang`.
- Install instructions pin a tag and a release zip. An existing install stays put until someone asks the agent to update it.
- Visual review prefers the shortest interval that answers the recorded question. A justified broad review uses sections of about 10–15 minutes. Those figures are practical defaults, not a provider cap.
- Linked repositories are inspected read-only. An analysis does not install them, run their code, publish, message people, or adopt products.
- The website introduces the skill. The assessment runs in the agent after installation.

## Not yet specified

- Whether `origin/main` should fast-forward to `upstream/main` at `35b0116`. The fork has no commits of its own ahead of upstream, and it still advertises v1.1.0.
- How evidence-rule hardening lands: reopen combined PR #2, merge PRs #3–#6 in an order that keeps `evidence-workflow.md` coherent, or open one new PR. No maintainer review is recorded on the open PRs.
- Whether Hermes v1.2.1 is a private operating layer for this machine or the draft of the next public release. A public version needs a portable form of the vault path, the Hermes script path, the cron watcher, and the Hermes frontmatter. That form is unwritten.
- The next public version number. The latest upstream tag is v1.2.0. The only text that says 1.2.1 is the unpublished Hermes install.
- Which hosts belong in the fresh-install matrix the README still marks untested. Codex is the documented installer. Hermes is how this machine runs a newer copy. The repo has no Claude Code or Grok manifest.
- Who updates the external website and the YTA5a sample when the pinned tag changes, and where that site's source lives.
- What "done" means for quality of an instruction-only skill: a structural check that cited files exist, a repeated real video, or continued reliance on doc fixes found during sessions.
- Whether the next README edit should spell install URLs as `grevalyn` rather than `GB525`. GitHub already redirects the old owner to grevalyn.

## Out of scope

- A standalone application, API, or hosted analyzer. The product is the skill text.
- Watch development, provider credentials, and account setup that belongs to the Watch skill.
- Executing, installing, or security-auditing repositories linked from a video.
- Publishing assessments, contacting creators, or changing the user's other projects as part of an analysis.
- Authoring the marketing website or the YTA5a sample inside this repo.
- Replacing the eight-section chat structure (trust, commercial intent, summary, takeaways, stack, workflow, gear, fit) or the Grevalyn transcript-analyzer lineage.
- Opening a pull request for this map. The map lives on a branch of the fork.
