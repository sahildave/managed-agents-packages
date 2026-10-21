# Exercise Consistency Planner — Claude Managed Agent native package

Tell it the routine you chose, when you are free next week and what you actually did last week. You get a short review of last week against its plan and a day-by-day plan for next week, placed in your free slots and sized to what you really managed, so the plan gets easier to keep rather than harder. It plans only the activities you chose and gives general habit planning, not medical or training advice.

## Resources
- `agents/exercise-consistency.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the review rules, plan sizing and plan template for this task.
- `environments/cloud.yaml`: Cloud sandbox with no outbound network. The shell, web search and web fetch are disabled in the agent.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `limited` with no allowed hosts and `allow_package_managers: false`, so the sandbox reaches nothing. The agent needs no web: it works only from what you tell it.
- Tools: the file tools, for memory. The shell (`bash`), web search and web fetch are disabled in `agents/exercise-consistency.md`.
- Memory is the main value. With the store attached, each run saves the plan it gave, so the next run can compare what you did against it. Without it, each run sees only that session's message.
- Not medical advice: if you mention pain, injury, illness or a medical condition, it tells you to check with a doctor or qualified professional and does not plan around it.
- Risk: do not paste medical records, diagnoses, medication details or other secrets. The agent does not store health details in memory.

## First-run setup
1. This package has no schedule. Run it at the end of your week. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/exercise-consistency.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to compare against past weeks.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a plan:

   Your inputs
   - Routine: <the activities you chose and how long each takes, e.g. 30-minute run, 20-minute bodyweight circuit>
   - Free next week: <days and times you can exercise>
   - Last week: <what you actually did, or "first week">

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every session sits in a free slot you gave and uses only activities from your routine.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured yet.
