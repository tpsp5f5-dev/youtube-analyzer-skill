---
type: task
mode: AFK
status: open
blocked_by: none
---

# Which instructions in the installed v1.2.1 skill fail on a machine without this vault and Hermes cron?

The decision about publishing the overlay needs an inventory. The installed tree is `SKILL.md`, six files under `references/`, and `scripts/watch_youtube_analyzer.sh`. The published tree cites only `references/evidence-workflow.md`.

**The question:** For each file in `~/.agents/skills/youtube-analyzer-skill`, which instructions are portable skill text, and which are pinned to this machine?

Known pins to classify, not a complete list:

- Vault root `/Users/toddsutton/Local/Obsidian/Work-Zachry/AgentOS/Memory_Layer/10_Processed_Memory/`
- Watcher `/Users/toddsutton/.hermes/scripts/watch_youtube_analyzer.sh` and the copy under the skill's `scripts/`
- Hermes frontmatter (`author: Hermes`, `metadata.hermes.tags`)
- Run-folder and mirror filename rules that assume that vault

**Done when:** A short table exists listing every cited path as portable, machine-local, or duplicated between the skill directory and `~/.hermes`. That table is the input to `private-hermes-overlay`.
