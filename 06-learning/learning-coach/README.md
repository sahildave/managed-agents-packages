# Personal Learning Coach — Claude Managed Agent native package

Name what you are learning, how much time you have and what you study from, and get back a one-week plan: short sessions that fit your hours, a practice task for each, and checkpoint questions to answer before the next run. Paste your answers next time and it marks them, then builds the next week around what you got wrong. It does not search the web for courses; it works from the materials you name and from what it already knows.

## Resources
- `agents/learning-coach.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with no outbound network. The shell, web search and web fetch are disabled in the agent, which works only from your inputs and memory.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `limited` with no `allowed_hosts` and `allow_package_managers: false`, so the sandbox reaches nothing outside itself.
- Tools: the file tools, for memory. The shell (`bash`), web search and web fetch are disabled in `agents/learning-coach.md`; on this network web search and web fetch would return nothing anyway.
- It cannot search the web, open a course or read your notes app. It points only at the books, courses or docs you list in "Your inputs".
- Memory is what makes a second run worth more than the first. With the store attached, each run saves the dated plan, the checkpoint questions and your weak areas; the next run marks your answers against those questions. Without the memory store attached, every run starts from nothing.

## First-run setup
1. This package has no schedule. Run it once a week, after you answer the last checkpoint questions. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/learning-coach.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access, so it can compare this run against the last one.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a report:

   Your inputs
   - Topic: <what you are learning, e.g. SQL window functions>
   - Current level: <what you can already do with it>
   - Hours per week: <e.g. 3>
   - Goal: <what you want to build or do with it>
   - Materials: <the books, courses or docs you study from>
   - Last week's answers: <your answers to last week's checkpoint questions, or none>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every item in the report traces back to a line you pasted or to a dated memory note.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
