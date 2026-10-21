# Plan My Week — Claude Managed Agent native package

Paste your goals, tasks and fixed commitments for the week, and get back a day-by-day plan that fits the focus hours you said you have, with a fifth of them left unplanned for what goes wrong. Tasks that do not fit are listed, not squeezed in. With memory attached, it reads last week's plan and carries forward what you did not finish. It never touches your calendar.

## Resources
- `agents/plan-my-week.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with no outbound network. The shell, web search and web fetch are disabled in the agent, which works only from your inputs and memory.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `limited` with no `allowed_hosts` and `allow_package_managers: false`, so the sandbox reaches nothing outside itself.
- Tools: the file tools, for memory. The shell (`bash`), web search and web fetch are disabled in `agents/plan-my-week.md`; on this network web search and web fetch would return nothing anyway.
- It cannot read your calendar or task manager. You paste your commitments and tasks into "Your inputs" each run.
- Memory is what makes a second run worth more than the first. With the store attached, each run saves the dated plan and the next run carries forward the tasks you did not finish. Without the memory store attached, every run starts from nothing.

## First-run setup
1. This package has no schedule. Run it at the start of your week. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/plan-my-week.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access, so it can compare this run against the last one.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a report:

   Your inputs
   - Week starting: <yyyy-mm-dd>
   - Goals this week: <one to three outcomes>
   - Tasks: <paste your tasks, one per line, with an estimate in hours if you have one>
   - Fixed commitments: <meetings, deadlines and time off, with days, or none>
   - Hours available: <focus hours per day, e.g. Mon-Thu 4, Fri 2>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every item in the report traces back to a line you pasted or to a dated memory note.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
