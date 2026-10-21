# Post Repurposer — Claude Managed Agent native package

Give it a link to something you already published, such as a blog post, a changelog entry or a talk page, and it drafts native posts for X, Bluesky, LinkedIn and your newsletter. Every draft links back to the source and names the paragraph it came from. With memory attached, it remembers your voice and the angles it already used, so a second run on the same piece gives new angles. It never posts anything. For posts about this week's commits, use Ship Log to Posts; for what to write next, use Content Idea Hunter.

## Resources
- `agents/post-repurposer.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access so web fetch can read the pieces you published. The shell and web search are disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web fetch can read your published pages. With `limited` networking and no `allowed_hosts`, web fetch returns nothing.
- Tools: web fetch and the file tools. The shell (`bash`) and web search are disabled in `agents/post-repurposer.md`, so the agent cannot run commands or search the web.
- Pages behind a login, and most X posts, do not load in web fetch. Paste the text instead.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private drafts or customer data into a session.
- It never posts. You copy the drafts you like into each channel yourself.

## First-run setup
1. This package has no schedule. Run it after you publish something you want on other channels. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/post-repurposer.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to remember your voice and the angles it already used.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of drafts:

   Your inputs
   - Sources: <up to three public links to pieces you published, or the full text pasted>
   - Platforms: <e.g. X, Bluesky, LinkedIn, newsletter>
   - Voice: <a few notes on how you sound, or two or three links to past posts you liked>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every claim in each draft appears in the source paragraph it names.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
