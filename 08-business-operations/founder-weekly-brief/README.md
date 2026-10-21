# Founder Weekly Brief — Claude Managed Agent native package

Turns the numbers and notes you paste in once a week into a one-page brief: how your numbers moved since the last brief, what changed this week at the competitors and in the topics you named (each with a link), the decisions you have due with options, and the risks. It reads public pages only. Your own numbers come from you, because it has no access to your analytics, payments or project tools.

## Resources
- `agents/founder-weekly-brief.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web search and fetch. The shell is disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web search and web fetch can reach public pages. With `limited` networking and no `allowed_hosts`, web search and web fetch return nothing.
- Tools: web search, web fetch and the file tools. The shell (`bash`) is disabled in `agents/founder-weekly-brief.md`, so the agent cannot run commands.
- Private data: the agent does not connect to Stripe, analytics, your bank or your project tracker. Copy the numbers you want in the brief into "This week's numbers". Paste totals, not customer records.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private exports or customer data into a session.

## First-run setup
1. This package has no schedule. Run it once a week, after you copy the week's numbers from your dashboards. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/founder-weekly-brief.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to compare against past briefs.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a brief:

   Your inputs
   - Product: <name and URL>
   - This week's numbers: <the figures you track, with dates, e.g. MRR, signups, churned customers; or none>
   - Shipped this week: <what you released or finished, or none>
   - Goals: <one to three goals for this quarter>
   - Open decisions: <decisions you need to make soon, or none>
   - Watch: <competitors and topics to check, with URLs where you have them>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every number in the brief is one you pasted, and every outside change links to a source.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
