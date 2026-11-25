---
type: grilling
mode: HITL
status: open
blocked_by: none
---

# Is the installed Hermes v1.2.1 a private operating layer or the next public skill?

`~/.agents/skills/youtube-analyzer-skill` says `version: 1.2.1`, `author: Hermes`. It adds a 13-step procedure, a verification gate, an Obsidian mirror under `10_Processed_Memory/`, a watcher, and link-check troubleshooting. The published grevalyn tree at v1.2.0 has none of those files. The installed skill hardcodes this machine's vault (`/Users/toddsutton/Local/Obsidian/Work-Zachry/AgentOS/Memory_Layer/10_Processed_Memory/`) and Hermes script (`/Users/toddsutton/.hermes/scripts/watch_youtube_analyzer.sh`).

Publishing that text as-is would put a personal vault path into an MIT skill whose readers are arbitrary Codex installs. Keeping it private leaves two skills in circulation under one name, with the local one a version number ahead of the latest tag.

**The question:** Should Hermes v1.2.1 stay off the public repo, or be rewritten into a portable release?

**Done when:** One of those two is chosen. "Publish as-is" is a third answer only if the personal paths are accepted on purpose.
