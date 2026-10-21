# Ship Log to Posts — Claude Managed Agent native package

Reads the last seven days of commits and merged pull requests from your public GitHub repository and drafts build-in-public posts for X and Bluesky, plus one short thread. Every post links to the commit or pull request it describes. It never posts anything.

## Resources
- `agents/ship-log-posts.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox that reaches only GitHub and package registries, so the agent can clone a public repository. Web search and web fetch are disabled in the agent.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.
- `deployments/scheduled.md`: runs every Friday (cron `0 16 * * 5`), attaches memory read/write, holds your inputs, and stops each run at $1.00.

## Network and tools
- Network: `limited` with `allow_package_managers: true`. That opens package registries and GitHub (`github.com`, `api.github.com`, `codeload.github.com`, `raw.githubusercontent.com`) and nothing else.
- Tools: the shell (`bash`) for git and curl, plus the file tools. Web search and web fetch are disabled in `agents/ship-log-posts.md`; they would return nothing on this network anyway.
- Private repositories: when you create a session, attach a `github_repository` resource with your own GitHub token. Never put a token in any file of this package, in the deployment message or in memory.
- It never posts. You copy the drafts you like into X or Bluesky yourself.

## First-run setup
1. Set `schedule.timezone` in `deployments/scheduled.md` to your IANA timezone (for example `Europe/London` or `America/New_York`). It defaults to `UTC`, so the run happens at 16:00 UTC until you change it.
2. Fill in the "Your inputs" block in `deployments/scheduled.md`. Replace every `<placeholder>`. While any placeholder is left, each run returns only a setup checklist.
3. Check the budget in `deployments/scheduled.md`: each run stops at $1.00 (`budget.max_list_cost.amount` is in US cents). No run cost has been measured yet.
4. Run `ant apply --dry-run .` and inspect the resource plan.
5. To install the agent, environment, skill and memory **without scheduling**, run:

   `ant apply agents/ship-log-posts.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

6. For scheduled runs, run `ant apply .`. **This creates the deployment, which starts a billed session on every scheduled run.** Scheduled sessions receive the memory store.
7. For an interactive session in Console, attach the memory store yourself with `read_write` access and paste your "Your inputs" block into the first message.

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every claim in the report links to a source.
4. In a deployment-created session, ask it to write a dated note to memory. Launch a second session and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
