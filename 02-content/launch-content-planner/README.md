# Launch Content Planner — Claude Managed Agent native package

Gives you a dated launch checklist that runs from today to a week after launch day, plus ready-to-edit copy for each channel you picked, such as Show HN, Product Hunt, X or your newsletter. It reads your product page so the copy matches it, and it checks each channel's current posting rules and links where they are stated. It never posts anything.

## Resources
- `agents/launch-content-planner.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web search and fetch. The shell is disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web search and web fetch can reach public pages. With `limited` networking and no `allowed_hosts`, web search and web fetch return nothing.
- Tools: web search, web fetch and the file tools. The shell (`bash`) is disabled in `agents/launch-content-planner.md`, so the agent cannot run commands.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private exports or customer data into a session.
- It never posts. You copy the drafts you like into each channel yourself.

## First-run setup
1. This package has no schedule. Run it two to four weeks before a launch, and again if the date or channels change. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/launch-content-planner.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want a later run to pick up the same plan.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a plan:

   Your inputs
   - Product: <name and URL>
   - Launch date: <yyyy-mm-dd>
   - What's new: <one paragraph on what you are launching and who it is for>
   - Proof: <real numbers, quotes or users you can cite, or none>
   - Channels: <e.g. Show HN, Product Hunt, X, Bluesky, your newsletter, a subreddit>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every channel rule in the plan links to a source, and that the copy uses no proof you did not give.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
