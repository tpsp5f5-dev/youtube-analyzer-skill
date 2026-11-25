---
type: grilling
mode: HITL
status: open
blocked_by: land-upstream-prs
---

# What's the versioning and changelog policy?

The skill is at v1.1.0 with a tagged release. The README pins installations to that tag. But there's no CHANGELOG, no documented versioning policy, and no definition of what constitutes a breaking change for an instruction skill.

**The question:** Should we establish a versioning policy before the next release?

**Things to decide:**
- Is semver appropriate for instruction-only skills? A "patch" that changes link-check wording could change agent behavior significantly.
- Should there be a CHANGELOG.md tracking what changed between versions?
- When the four open PRs land, does that warrant a version bump (v1.1.1 or v1.2.0)?
- Should the README's install command auto-update to the latest tag, or is pinning to a specific version the right default?
