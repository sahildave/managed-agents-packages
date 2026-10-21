# Get Listed — Claude Managed Agent native package

Finds the "best X" lists, alternatives pages and directories that name your competitors but not you. For each page you get the date it was last updated, the competitors it names, how to get on it and a pitch draft that names that page. After the first run, a weekly run reports only pages that are new since the last one. It never sends a pitch or fills in a form.

## Resources
- `agents/get-listed.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web search and fetch. The shell is disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots and the status of each prospect. It does **not** attach itself to interactive sessions.
- `deployments/scheduled.md`: runs every Monday (cron `0 8 * * 1`), attaches memory read/write, holds your inputs, and stops each run at $2.00.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web search and web fetch can reach public pages. With `limited` networking and no `allowed_hosts`, web search and web fetch return nothing.
- Tools: web search, web fetch and the file tools. The shell (`bash`) is disabled in `agents/get-listed.md`, so the agent cannot run commands.
- Subagents and workflows are enabled so the first run can search for each competitor in parallel. That can cost more than a serial run.
- It has no backlink tool, so it reports no domain authority or traffic figures. It never sends a pitch, fills in a submit form or pays for a listing; you do that yourself. It labels paid placements as paid.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private exports or customer data into a session.

## First-run setup
1. Set `schedule.timezone` in `deployments/scheduled.md` to your IANA timezone (for example `Europe/London` or `America/New_York`). It defaults to `UTC`, so the run happens at 8:00 UTC until you change it. Cron has no every-other-week form; for two runs a month, change the expression to `0 8 1,15 * *`.
2. Fill in the "Your inputs" block in `deployments/scheduled.md`. Replace every `<placeholder>`. While any placeholder is left, each run returns only a setup checklist.
3. Check the budget in `deployments/scheduled.md`: each run stops at $2.00 (`budget.max_list_cost.amount` is in US cents). No run cost has been measured yet.
4. Run `ant apply --dry-run .` and inspect the resource plan.
5. To install the agent, environment, skill and memory **without scheduling**, run:

   `ant apply agents/get-listed.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

6. Do the first, wider sweep in an interactive session in Console: attach the memory store yourself with `read_write` access and paste your "Your inputs" block into the first message. A session you start in Console has no cost cap.
7. For scheduled runs, run `ant apply .`. **This creates the deployment, which starts a billed session on every scheduled run.** Scheduled sessions receive the memory store.
8. When you send a pitch or get listed, tell the agent in an interactive session with the memory store attached (for example "example.com: sent"). It saves the status and never pitches that domain again.

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every prospect links to a page the agent fetched, that the page names a competitor and not you, and that no contact address is guessed.
4. In a deployment-created session, ask it to write a dated note to memory. Launch a second session and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured. Not tested as a scheduled deployment.
