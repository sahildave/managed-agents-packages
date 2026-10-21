# Decision Journal Reviewer — Claude Managed Agent native package

Log the decisions you make with your reasoning, your prediction and a date to check. When the date comes, paste what actually happened and you get each decision reviewed: the prediction next to the outcome, which assumptions held, and whether the reasoning was sound on what you knew at the time. It works only from what you paste and keeps the log in memory.

## Resources
- `agents/decision-journal-reviewer.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the log format, review rules and report template for this task.
- `environments/cloud.yaml`: Cloud sandbox with no outbound network. The shell, web search and web fetch are disabled in the agent.
- `memory_stores/history.yaml`: private memory for the decision log and dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `limited` with no allowed hosts and `allow_package_managers: false`, so the sandbox reaches nothing. The agent needs no web: it works only from your notes.
- Tools: the file tools, for memory. The shell (`bash`), web search and web fetch are disabled in `agents/decision-journal-reviewer.md`.
- Memory is the main value. The decision log lives in the memory store, so a decision logged today can be reviewed months later. Without the store attached, it can only review decisions you paste in the same session.
- Risk: do not paste passwords, card numbers, bank details, medical records or other secrets. The agent does not store them in memory.

## First-run setup
1. This package has no schedule. Run it when you make a decision worth logging, or when a check date comes up. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/decision-journal-reviewer.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access; without it, nothing you log is kept.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a review:

   Your inputs
   - New decisions: <for each: what you decided, why, what you expect to happen, when to check; or "none">
   - Outcomes seen: <what happened on earlier decisions; or "none">

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Log one decision with a check date. In a later session, report an outcome and check that the review quotes your original prediction unchanged.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured yet.
