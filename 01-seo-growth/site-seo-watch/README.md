# Site SEO Watch — Claude Managed Agent native package

Checks your public site every week with curl (robots.txt, sitemap, status codes, redirects, titles, meta descriptions, canonicals) and reports only what broke or changed since the last run. It replaces Weekly SEO Auditor and Technical SEO Watch.

## Resources
- `agents/site-seo-watch.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access and a shell, so the agent can run curl against your public site. Nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.
- `deployments/scheduled.md`: runs every Monday (cron `0 8 * * 1`), attaches memory read/write, holds your inputs, and stops each run at $1.00.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so curl and web fetch can reach your site.
- Tools: the full built-in toolset, including the shell (`bash`), which the agent uses for curl. Bash runs without asking for approval.
- Risk: the agent can run any command and anything in the sandbox can leave over the open network. Do not put secrets, private exports or tokens in a session. The agent sends only GET and HEAD requests to your site.

## First-run setup
1. Set `schedule.timezone` in `deployments/scheduled.md` to your IANA timezone (for example `Europe/London` or `America/New_York`). It defaults to `UTC`, so the run happens at 8:00 UTC until you change it.
2. Fill in the "Your inputs" block in `deployments/scheduled.md`. Replace every `<placeholder>`. While any placeholder is left, each run returns only a setup checklist.
3. Check the budget in `deployments/scheduled.md`: each run stops at $1.00 (`budget.max_list_cost.amount` is in US cents). One measured run cost $0.31 ([example run](https://github.com/sahildave/managed-agents-packages/blob/main/examples/site-seo-watch-2026-10-21.md)).
4. Run `ant apply --dry-run .` and inspect the resource plan.
5. To install the agent, environment, skill and memory **without scheduling**, run:

   `ant apply agents/site-seo-watch.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

6. For scheduled runs, run `ant apply .`. **This creates the deployment, which starts a billed session on every scheduled run.** Scheduled sessions receive the memory store.
7. For an interactive session in Console, attach the memory store yourself with `read_write` access and paste your "Your inputs" block into the first message.

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every claim in the report links to a source.
4. In a deployment-created session, ask it to write a dated note to memory. Launch a second session and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. Ran once live on 2026-10-21 with real inputs: see [the example run](https://github.com/sahildave/managed-agents-packages/blob/main/examples/site-seo-watch-2026-10-21.md) (list cost $0.31). Not tested as a scheduled deployment.
