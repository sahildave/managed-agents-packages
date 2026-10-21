# Niche Digest — Claude Managed Agent native package

Drafts a ready-to-send newsletter issue each week from the last seven days in your niche. It checks the sources you trust first, then searches for what they missed. Each item has a dated link to its primary source, a two-sentence summary, a line on why it matters to your readers and a note on the kind of source (primary, opinion, vendor marketing, news report). The issue comes with a subject line and an intro in your voice. With memory attached, it skips links from past issues. It never sends anything.

Niche Digest is not Research Reading Digest. Research Reading Digest picks papers and long reads for you to learn from. Niche Digest writes an issue for your readers to receive.

## Resources
- `agents/niche-digest.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web search and fetch. The shell is disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.
- `deployments/scheduled.md`: runs every Thursday (cron `0 9 * * 4`), attaches memory read/write, holds your inputs, and stops each run at $2.00.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web search and web fetch can reach public pages. With `limited` networking and no `allowed_hosts`, web search and web fetch return nothing.
- Tools: web search, web fetch and the file tools. The shell (`bash`) is disabled in `agents/niche-digest.md`, so the agent cannot run commands.
- Workflows are enabled so the agent can check three or more source families in parallel. Parallel runs can cost more; with fewer sources it works in one thread.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private exports or customer data into a session.
- It never sends the issue or loads it into your email platform. You copy it into your newsletter tool yourself.

## First-run setup
1. Set `schedule.timezone` in `deployments/scheduled.md` to your IANA timezone (for example `Europe/London` or `America/New_York`). It defaults to `UTC`, so the run happens at 9:00 UTC until you change it.
2. Fill in the "Your inputs" block in `deployments/scheduled.md`. Replace every `<placeholder>`. While any placeholder is left, each run returns only a setup checklist.
3. Check the budget in `deployments/scheduled.md`: each run stops at $2.00 (`budget.max_list_cost.amount` is in US cents). No run cost has been measured yet.
4. Run `ant apply --dry-run .` and inspect the resource plan.
5. To install the agent, environment, skill and memory **without scheduling**, run:

   `ant apply agents/niche-digest.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

6. For scheduled runs, run `ant apply .`. **This creates the deployment, which starts a billed session on every scheduled run.** Scheduled sessions receive the memory store.
7. For an interactive session in Console, attach the memory store yourself with `read_write` access and paste your "Your inputs" block into the first message. Use such a session to tell the agent which items or topics your readers liked or skipped, so later issues pick better.

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every item links to a source dated within the last seven days and carries a source note.
4. In a deployment-created session, ask it to write a dated note to memory. Launch a second session and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
