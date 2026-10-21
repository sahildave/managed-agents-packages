# Thread Watch — Claude Managed Agent native package

Searches the communities you name each week for threads where people ask for a tool like yours, complain about a competitor or mention your product. It reports only threads it has not shown you before, each linked and dated, and drafts a reply for the five best ones that answers the question first and says you make the product. It never posts.

Thread Watch is not [Content Idea Hunter](https://github.com/sahildave/managed-agents-packages/tree/main/02-content/content-idea-hunter). Content Idea Hunter turns your audience's unanswered questions into post ideas you write later. Thread Watch finds the live threads where your product, your competitors or your category come up, so you can reply this week.

## Resources
- `agents/thread-watch.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web search and fetch. The shell is disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.
- `deployments/scheduled.md`: runs every Monday (cron `0 9 * * 1`), attaches memory read/write, holds your inputs, and stops each run at $2.00.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web search and web fetch can reach public pages. With `limited` networking and no `allowed_hosts`, web search and web fetch return nothing.
- Tools: web search, web fetch and the file tools. The shell (`bash`) is disabled in `agents/thread-watch.md`, so the agent cannot run commands.
- Workflows are enabled so the agent can search three or more communities in parallel. Parallel runs can cost more; with fewer communities it works in one thread.
- Coverage: search results for X and other sites behind a login are thin. The report lists them under "Not covered" instead of claiming it checked them.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private exports or customer data into a session.
- It never posts, replies, votes or messages. You post the drafts you like yourself.

## First-run setup
1. Set `schedule.timezone` in `deployments/scheduled.md` to your IANA timezone (for example `Europe/London` or `America/New_York`). It defaults to `UTC`, so the run happens at 9:00 UTC until you change it.
2. Fill in the "Your inputs" block in `deployments/scheduled.md`. Replace every `<placeholder>`. While any placeholder is left, each run returns only a setup checklist.
3. Check the budget in `deployments/scheduled.md`: each run stops at $2.00 (`budget.max_list_cost.amount` is in US cents). No run cost has been measured yet.
4. Run `ant apply --dry-run .` and inspect the resource plan.
5. To install the agent, environment, skill and memory **without scheduling**, run:

   `ant apply agents/thread-watch.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

6. For scheduled runs, run `ant apply .`. **This creates the deployment, which starts a billed session on every scheduled run.** Scheduled sessions receive the memory store.
7. For an interactive session in Console, attach the memory store yourself with `read_write` access and paste your "Your inputs" block into the first message. Use such a session to tell the agent which drafted replies you posted, so it records them.

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every thread links to a page dated within the last seven days, and that every drafted reply answers the question first and follows your reply rule.
4. In a deployment-created session, ask it to write a dated note to memory. Launch a second session and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
