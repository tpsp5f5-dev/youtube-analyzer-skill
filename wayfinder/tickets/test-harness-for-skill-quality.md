---
type: grilling
mode: HITL
status: open
blocked_by: none
---

# How do we validate that skill changes don't degrade analysis quality?

The skill is pure Markdown instructions — there's no code to unit-test. But instruction changes can materially alter the analysis output (e.g., changing link-check wording could cause an agent to skip checks or misclassify status codes).

**The question:** What testing approach, if any, makes sense for an instruction-only skill?

**Options to consider:**
1. **Golden-output snapshots:** Run the skill against 2–3 known videos and diff the analysis structure (not exact wording) against a reference. Manual but catches regressions.
2. **Structural linting:** A script that validates SKILL.md frontmatter, checks that all 8 analysis sections are present, verifies internal links resolve, and confirms the evidence-workflow reference exists.
3. **CI on the Markdown:** GitHub Actions that lint markdown, validate YAML frontmatter, and check links in the repo itself (not the skill's runtime link-checking).
4. **Nothing formal:** Rely on the PR author's real-usage testing (as the current four PRs do) and treat the skill as documentation that's validated by use.

**Done when:** A decision is made and, if option 1–3, the first version is implemented.
