# Evergreen Posts — Claude Managed Agent native package

Paste your past X or Bluesky posts with the numbers your analytics show, and it picks the ones that worked best by the number you care about and drafts a fresh version of each: a new hook, a follow-up or a short thread. Every draft links to the original post and shows its numbers exactly as you pasted them. With memory attached, it keeps an archive of the posts you pasted and a log of what it already brought back, so a post does not come back too soon. It never posts anything. For posts about this week's commits, use Ship Log to Posts; for drafts from a long piece you published, use Post Repurposer; for new topics, use Content Idea Hunter.

## Resources
- `agents/evergreen-posts.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with no outside network access. The agent works only from the posts you paste and its memory; the shell, web search and web fetch are disabled in the agent.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `limited` with no `allowed_hosts` and no package managers, so the sandbox reaches nothing outside. The task needs no web access: the agent works only from the posts you paste.
- Tools: the file tools only. The shell (`bash`), web search and web fetch are disabled in `agents/evergreen-posts.md`, so the agent cannot run commands, read your account or open the links you paste.
- What you paste stays in the session and, if you attach it, the memory store. Do not paste secrets or customer data.
- It never posts. You copy the drafts you like into X or Bluesky yourself.

## First-run setup
1. This package has no schedule. Run it when you want posts and have nothing new to say, for example every few weeks. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/evergreen-posts.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to keep the archive and the reuse log.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of drafts:

   Your inputs
   - Past posts: <ten to fifty of your posts, each with its date, link and the numbers your analytics show>
   - What counts as worked: <the one number you care about, e.g. replies, reposts or link clicks>
   - What changed since: <facts in old posts that are no longer true, e.g. new pricing or a renamed feature, or none>
   - Voice: <e.g. plain and a bit dry, no emoji, no hype words>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that each pick's numbers match what you pasted and that every claim in a draft appears in the original post or in your list of what changed.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
