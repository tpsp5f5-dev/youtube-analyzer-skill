---
type: grilling
mode: HITL
status: open
blocked_by: none
---

# Which upstream baseline and divergence policy should this fork adopt?

## Why this needs a decision

The workspace ships v1.1.0 at `5a7c851`, but upstream main `35b0116` and published v1.2.0 include opt-in project research and a different visual-review default. Blindly updating only version strings would misrepresent behavior. See [merged upstream PR #1](https://github.com/grevalyn/youtube-analyzer-skill/pull/1).

## Options

- Follow upstream v1.2.0 and maintain a small, reviewed patch set. Recommended because privacy and engine choices already have upstream rationale and limited test evidence.
- Retain v1.1.0 deliberately and document which newer behavior is deferred.
- Maintain an independent fork with explicit ownership of intake, preferences, engine defaults and release maintenance.

## Decision record required

Record the selected commit/tag, allowed divergence, maintainer responsible for future syncs and whether installation should point at upstream or fork releases. Explicitly accept or reject v1.2.0's opt-in stack research and local-engine default as part of that one baseline decision. Do not imply fork releases exist today.

## Done when

A maintainer records the baseline policy in MAP.md and provides the approved source revision and distribution target for ticket 02. No merge or release is authorized by this question alone.
