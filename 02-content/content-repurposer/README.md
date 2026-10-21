# Content Repurposing Editor — Claude Managed Agent native package

Takes one piece you already wrote, such as an article, a post or release notes, and drafts a native version for each channel you post on: an X thread, a LinkedIn post, a newsletter section. Every claim in a draft traces back to a sentence in your source, and you get a list of facts to check before you post. It never posts anything.

## Resources
- `agents/content-repurposer.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with no outside network access. The agent works only from the text you paste; the shell, web search and web fetch are disabled in the agent.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `limited` with no `allowed_hosts` and no package managers, so the sandbox reaches nothing outside. The task needs no web access: the agent works only from the text you paste.
- Tools: the file tools only. The shell (`bash`), web search and web fetch are disabled in `agents/content-repurposer.md`, so the agent cannot run commands or read your linked page.
- What you paste stays in the session and, if you attach it, the memory store. Do not paste secrets or customer data.
- It never posts. You copy the drafts you like into each channel yourself.

## First-run setup
1. This package has no schedule. Run it after you publish something you want on other channels. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/content-repurposer.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to remember your voice and what it already repurposed.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of drafts:

   Your inputs
   - Source text: <paste the full article, post or release notes>
   - Source link: <public URL of the original, or none>
   - Channels: <e.g. X, Bluesky, LinkedIn, newsletter>
   - Voice: <e.g. plain and a bit dry, no emoji, no hype words>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every claim in each draft appears in your source text.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
