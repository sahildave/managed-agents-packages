# Growth Experiment Reviewer — Claude Managed Agent native package

Reads the growth experiments you paste, checks each result against the numbers before it, and tells you which tests to keep, stop or rerun and why. You also get one next test with its metric and stop date. It works only from what you paste: it does not browse or connect to your analytics.

## Resources
- `agents/growth-experiment-reviewer.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with no network access. The shell, web search and web fetch are disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `limited` with no `allowed_hosts` and no package registries, so the sandbox reaches nothing. The job needs no network: everything comes from your message.
- Tools: the file tools only. The shell (`bash`), web search and web fetch are disabled in `agents/growth-experiment-reviewer.md`.
- The advisor is enabled for close keep-or-stop calls. It can add cost to a run.
- It does not connect to analytics, payment or experiment tools. Copy the numbers from them into your message yourself. Paste counts, not raw customer records.

## First-run setup
1. This package has no schedule. Run it when an experiment ends or before you plan the next one. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/growth-experiment-reviewer.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to check whether the test it suggested last time ran.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a review:

   Your inputs
   - Goal: <the one number you are trying to move, e.g. trial sign-ups per week>
   - Experiments: <one line per test: what you changed, the metric, start and end dates, the numbers before and during>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every number in the review comes from your message and every rate shows its arithmetic.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
