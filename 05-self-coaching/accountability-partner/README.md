# Weekly Accountability Partner — Claude Managed Agent native package

Paste the commitments you set for the week and what actually happened. You get a scorecard (done, partly done, not done, or unknown when you did not say), the obstacles that keep coming back across weeks, and at most three commitments for next week, sized to what you managed. It works only from what you paste and keeps a dated history in memory.

## Resources
- `agents/accountability-partner.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the scoring rules, memory layout and report template for this task.
- `environments/cloud.yaml`: Cloud sandbox with no outbound network. The shell, web search and web fetch are disabled in the agent.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `limited` with no allowed hosts and `allow_package_managers: false`, so the sandbox reaches nothing. The agent needs no web: it works only from your update.
- Tools: the file tools, for memory. The shell (`bash`), web search and web fetch are disabled in `agents/accountability-partner.md`.
- Memory is the main value. With the store attached, each run saves a dated snapshot, and later runs spot obstacles that repeat and can reuse last week's commitments. Without it, each run sees only that session's update.
- Risk: do not paste passwords, card numbers, bank details, medical records or other secrets. The agent does not store them in memory.

## First-run setup
1. This package has no schedule. Run it at the end of your week. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/accountability-partner.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to compare against past weeks.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a check-in:

   Your inputs
   - Commitments: <what you set out to do this week, one per line, or "same as last week">
   - What you did: <an honest account of the week>
   - What got in the way: <obstacles, or "nothing">

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every score quotes your own update, and that commitments you did not mention are marked unknown.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured yet.
