# YouTube Analyzer wayfinder

Planning snapshot: 2026-11-25 UTC. This map proposes work, not an approved release roadmap. All tickets are open. No product behavior is changed by this branch.

## Destination

Deliver a portable, evidence-based YouTube assessment skill whose complete answer is useful in chat, whose claims can be traced to captions, checked resources and scoped visual observations, and whose missing evidence is explicit. The next practical milestone is a deliberately chosen fork baseline with reproducible installation and evidence-quality checks, not a new application. Upstream has already moved toward opt-in personal-context research and host-agent frame review, while this workspace still ships the older instructions.

## Notes

### What is actually here

- Inspected workspace baseline: `5a7c8514a2d1b73c16943ec338e90d33ecf42f3b`, skill version **1.1.0**. [Root README](../README.md), [packaged README](../skills/youtube-analyzer-skill/README.md), [SKILL.md](../skills/youtube-analyzer-skill/SKILL.md), [evidence workflow](../skills/youtube-analyzer-skill/references/evidence-workflow.md), [interface metadata](../skills/youtube-analyzer-skill/agents/openai.yaml), licenses and attribution were read.
- This is an instruction package, not executable analyzer code. Its package contains six files: SKILL, README, LICENSE, ATTRIBUTION, one evidence reference and one agent YAML. There are no tracked tests, dependency manifest, build scripts or CI workflows at this baseline.
- Root README additionally links a hosted website/sample. Website source is not in this repository. Both READMEs install a pinned v1.1.0 tag through the historical `GB525` URL.
- `outputs/`, `work/`, ZIPs and environment files are ignored. Public fixtures must live outside those ignored evidence directories and exclude private material, tokens and redistributed full captions.
- Watch is optional, separately installed and separately licensed. Its API credentials, local dependencies and provider behavior are not delivered here. Structural validation and a predecessor run are documented, but fresh-account installation and the platform/provider matrix are explicitly untested.

### Remote evidence inspected

GitHub metadata, all-state issue/PR lists, upstream PR bodies/diffs and v1.2.0 release notes were checked on the snapshot date. These are dated observations, not guarantees of future remote state.

| Source | Finding | Implication |
| --- | --- | --- |
| [Fork](https://github.com/tpsp5f5-dev/youtube-analyzer-skill) | Issues disabled, no PRs returned, no releases returned | No fork issue roadmap could be inferred |
| [Upstream](https://github.com/grevalyn/youtube-analyzer-skill) | No issues returned; fetched main is `35b011656655560053be8b8eaa698d7503c86ad2`, four commits beyond this workspace | Do not describe local v1.1.0 as current upstream |
| [Merged PR #1](https://github.com/grevalyn/youtube-analyzer-skill/pull/1) and [v1.2.0 release](https://github.com/grevalyn/youtube-analyzer-skill/releases/tag/v1.2.0) | Opt-in stack comparison, local extraction/host-agent review default, private preferences, caption-language verification, browser playback precautions; release ZIP and checksum published | Decide fork alignment before porting changes; release publication is already done upstream |
| [Closed PR #2](https://github.com/grevalyn/youtube-analyzer-skill/pull/2) | Combined evidence-hardening proposal, subsequently split | Context, not an additional implementation ticket |
| [Open PR #3](https://github.com/grevalyn/youtube-analyzer-skill/pull/3) | Caption fallback after HTTP 429 | Review and verify against chosen baseline |
| [Open PR #4](https://github.com/grevalyn/youtube-analyzer-skill/pull/4) | Distinguish restriction/rate limits from broken URLs | Preserve observed status without overclaiming cause |
| [Open PR #5](https://github.com/grevalyn/youtube-analyzer-skill/pull/5) | Named resource without URL remains an evidence gap | Never fabricate a substitute source |
| [Open PR #6](https://github.com/grevalyn/youtube-analyzer-skill/pull/6) | Clickable artifact links, valid optional YAML, exact-path verification | Add output acceptance examples |

Upstream reports a successful Windows local Watch check on eight frames in a 30-second interval, with an initially incorrect auto-dub caption language corrected explicitly. That is upstream-reported evidence, not a run performed for this map, and not full cross-platform validation.

## Decisions so far

Established by the existing package, not newly invented here:

- Deliver the full substantive assessment in chat. Save matching evidence when file tools exist, and disclose inability to save.
- Separate spoken claims, visual observations, checked external facts and interpretation. Do not treat a model report as a verbatim transcript or a security audit.
- Gather the expanded description and record every distinct linked resource's access outcome. Inspect repositories without executing their code.
- Preserve source timestamps and use focused visual questions. Roughly 10–15-minute sections are practical broad-review defaults, not provider guarantees.
- Watch remains optional and unbundled. Do not silently switch providers or infer readiness from an attempted call.
- Research does not authorize installing linked software, publishing, purchases, contacting others or changing adopted standards.

Upstream has additionally decided on opt-in stack research and analyzer-local visual review by default. Those decisions have **not** yet been adopted by this fork's checked-out version. Ticket 01 is the explicit adoption gate.

## Not yet specified (the fog)

The fork's long-term relationship to upstream, supported host/platform combinations, release authority and acceptable validation evidence are not documented. There is no in-repo repeatable acceptance suite. Open PR descriptions report real-world checks but do not supply a maintained local regression suite. The following questions turn those gaps into bounded work.

| Ticket | Kind / mode | One question | Depends on |
| --- | --- | --- | --- |
| [01 Baseline policy](tickets/01-baseline-policy.md) | grilling / HITL | Which upstream baseline and divergence policy should this fork adopt? | none |
| [02 Align baseline](tickets/02-align-baseline.md) | task / AFK | Does the package consistently implement the approved baseline? | 01 |
| [03 Caption resilience](tickets/03-caption-resilience.md) | task / AFK | Can caption failures preserve language and timing without falsely declaring captions absent? | 02 |
| [04 Link evidence](tickets/04-link-evidence.md) | task / AFK | Can the link ledger distinguish failed access from absent or broken resources? | 02 |
| [05 Artifact integrity](tickets/05-artifact-integrity.md) | task / AFK | Can saved artifacts remain readable, safe and verifiable by exact path? | 02 |
| [06 Validation target](tickets/06-validation-target.md) | grilling / HITL | Which minimal host/platform/engine matrix is required before claiming support? | 01 |
| [07 Fresh install](tickets/07-fresh-install.md) | task / HITL | Can a fresh recipient complete the approved install-to-assessment workflow? | 02, 06 |
| [08 Repeatable checks](tickets/08-repeatable-checks.md) | task / AFK | Can a clean checkout repeat the package's structural and evidence-contract checks? | 03, 04, 05 |

Start with 01. After 02, run 03–05 independently. Resolve 06 before the human-assisted 07. Ticket 08 consolidates regression checks, but does not substitute for 07. `blocked_by` uses exact sibling ticket filenames; `none` means runnable now. AFK tickets require no new account, installation permission or paid provider call. HITL tickets require an explicit decision or supervised environment access.

## Out of scope

- Building a hosted analyzer, video player, crawler, autonomous downloader service or new UI.
- Bundling Watch, provisioning provider accounts, installing models or spending on API calls as part of this planning task.
- Merging upstream PRs, changing skill behavior, publishing a release or opening a PR from this map branch.
- Treating an upstream claim as independently reproduced, promising every provider/platform works, or claiming full evidence coverage after a failed modality.
- Committing private preferences, personal project records, credentials, browser sessions or copyrighted full-media fixtures.
- Editing the externally hosted website without its source and explicit scope.
