# SEO Content Refresh Planner — Claude Managed Agent native package

Reads up to five of your older articles, checks their facts, prices and links against current sources, and compares them with the pages ranking for the same question today. You get a ranked fix list per article, each fix with the text to change, the evidence and the effort.

## Resources
- `agents/seo-content-refresh.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web search and fetch. The shell is disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web search and web fetch can reach public pages. With `limited` networking and no `allowed_hosts`, web search and web fetch return nothing.
- Tools: web search, web fetch and the file tools. The shell (`bash`) is disabled in `agents/seo-content-refresh.md`, so the agent cannot run commands.
- It has no analytics or Search Console access, so it cannot tell you which articles lost traffic. Pick the articles yourself.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private exports or customer data into a session.

## First-run setup
1. This package has no schedule. Run it when you pick articles to update. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/seo-content-refresh.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to compare against past runs.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a report:

   Your inputs
   - Articles: <up to five article URLs, comma-separated>
   - Audience: <who reads them, one sentence>
   - Last updated: <the date each was last updated, or unknown>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every fix quotes your article and links to the current source it relies on.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
