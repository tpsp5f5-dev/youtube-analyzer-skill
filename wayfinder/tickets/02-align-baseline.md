---
type: task
mode: AFK
status: open
blocked_by:
  - 01-baseline-policy.md
---

# Does the package consistently implement the approved baseline?

## Evidence

Five tracked files differ between the local v1.1.0 baseline and upstream main: both READMEs, SKILL.md, agents/openai.yaml and references/evidence-workflow.md. Upstream [v1.2.0](https://github.com/grevalyn/youtube-analyzer-skill/releases/tag/v1.2.0) is already published, so creating that upstream release is not remaining work.

## Work

Apply the approved source changes, or explicitly document the intentional v1.1.0 hold. Check version metadata, installation tag and release links, launch prompt, intake behavior, caption language handling, engine precedence and saved-setting boundaries together. Preserve the root-only website introduction and license/attribution. Fix the introductory reference to seven analysis sections if the actual eight-section structure is retained.

## Done when

- A bounded diff or documented hold is tied to ticket 01's selected revision.
- Both installation instructions resolve to the approved real release/tag and name the correct archive.
- A behavior table makes stack research, explicit preferences, engine defaults and failure handling consistent across package files.
- References exist and metadata parses. No private preference file is added, no release is published and no provider setting is changed.
