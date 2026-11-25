---
type: task
mode: AFK
status: open
blocked_by:
  - 03-caption-resilience.md
  - 04-link-evidence.md
  - 05-artifact-integrity.md
---

# Can a clean checkout repeat the package's structural and evidence-contract checks?

## Evidence

The baseline contains no test scripts or CI definition despite documentation saying it was structurally validated. The new evidence rules need repeatable checks rather than another untraceable claim of validation.

## Work

Add one documented, non-network local check command with minimal declared dependencies. Check SKILL frontmatter, agent YAML, required package files, internal references, version/install-target consistency and the synthetic fixtures from tickets 03–05. Include an explicit human review rubric for semantic requirements that a parser cannot establish. Add a package-content allowlist check to exclude outputs, work files, environment files and private preferences from any future archive.

## Done when

- A clean checkout can run the documented command and report individual checks with actionable failures.
- Deliberately invalid metadata, missing references, unsafe package entries and malformed artifact examples fail the appropriate checks.
- The eight analysis sections and the no-Watch/no-files paths have explicit review criteria.
- Documentation distinguishes syntax/fixture validation from real host-agent acceptance and points to ticket 07 for the latter.
- The command needs no provider credentials, paid calls, linked-project execution or publication. Wiring into hosted CI is optional follow-up, not a prerequisite for a reproducible local check.
