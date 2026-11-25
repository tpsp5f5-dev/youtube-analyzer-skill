---
type: grilling
mode: HITL
status: open
blocked_by: none
---

# Decide on a caption extraction strategy across platforms

SKILL.md mentions yt-dlp, connectors, web access, and browser fallback but doesn't rank them or say which are tested. PR #3 adds a 429 fallback but the broader strategy is implicit. Different agent platforms have different tool availability (yt-dlp may not be installed, browser may not exist).

**Question:** Which caption extraction methods are officially supported, in what priority order, and per which agent platform? Should the skill document a decision tree so agents don't guess?
