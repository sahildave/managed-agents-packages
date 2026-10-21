# Work-Rest Balance Reviewer — Claude Managed Agent native package

Paste a rough log of last week's work and the rest goals you set yourself. You get your hours per day, each rest goal marked met, missed or unknown, the goals you keep missing week after week, and two or three rest blocks to put in next week's calendar around your fixed commitments. It works only from what you paste and gives scheduling help, not medical advice.

## Resources
- `agents/work-rest-balance.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the log rules, rest-block rules and report template for this task.
- `environments/cloud.yaml`: Cloud sandbox with no outbound network. The shell, web search and web fetch are disabled in the agent.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `limited` with no allowed hosts and `allow_package_managers: false`, so the sandbox reaches nothing. The agent needs no web: it works only from your log.
- Tools: the file tools, for memory. The shell (`bash`), web search and web fetch are disabled in `agents/work-rest-balance.md`.
- Memory is the main value. With the store attached, each run saves your hours and goal results, so later runs can show which goals you keep missing. Without it, each run sees only that session's log.
- Not medical advice: if you mention exhaustion, low mood, poor sleep or another health concern, it suggests a doctor or qualified professional and does not analyse it.
- Risk: do not paste medical records, diagnoses, medication details or other secrets. The agent does not store health details in memory.

## First-run setup
1. This package has no schedule. Run it at the end of your week. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/work-rest-balance.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to compare against past weeks.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a review:

   Your inputs
   - Last week's work: <rough log, e.g. Mon 9-19, Tue 9-23, Sat off>
   - Rest goals: <e.g. one full day off, stop by 19:00>
   - Next week's fixed commitments: <deadlines, travel, events, or "none">

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every hour total matches your log, and that no rest block overlaps a fixed commitment.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured yet.
