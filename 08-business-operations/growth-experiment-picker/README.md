# Growth Experiment Picker — Claude Managed Agent native package

Tell it your product, stage and the channels you have tried, and get three growth experiments that comparable indie products have run, each with a link to the founder's own write-up, sized to run in one week with the hours you have, and with a metric and a bar for "worked". When an experiment ends, paste its numbers: it checks them against the bar you set, shows the arithmetic and calls it keep, stop or rerun. It does not connect to your analytics.

## Resources
- `agents/growth-experiment-picker.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web search and fetch. The shell is disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web search and web fetch can reach public pages. With `limited` networking and no `allowed_hosts`, web search and web fetch return nothing.
- Tools: web search, web fetch and the file tools. The shell (`bash`) is disabled in `agents/growth-experiment-picker.md`, so the agent cannot run commands.
- Subagents are enabled to search several channels in parallel, and the advisor is enabled for close keep-or-stop calls. Both can add cost to a run.
- It does not connect to analytics, payment or experiment tools. Copy the numbers from them into your message yourself. Paste counts, not raw customer records.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private exports or customer data into a session.

## First-run setup
1. This package has no schedule. Run it before you plan an experiment and again when one ends. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/growth-experiment-picker.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access so it can check your results against the bar it saved and skip experiments it already suggested.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a report:

   Your inputs
   - Goal: <the one number you are trying to move, e.g. trial sign-ups per week>
   - Product: <what it does and its URL>
   - Stage: <e.g. pre-launch, under 1k USD MRR>
   - Channels tried: <each channel and what happened, or "none">
   - Hours a week: <hours you can give experiments>
   - Last experiment: <what you changed, the metric, start and end dates, the numbers before and during, or "none">

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every example links to a page that names the product, every number about your product comes from your message, and every rate shows its arithmetic.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
