# SEO Content Refresh — Claude Managed Agent native package

Checks your older posts for facts that went stale, outbound links that fail and questions the pages ranking now answer that yours don't. It also compares each title and meta description with the top results. Give it up to 15 post URLs, or let it pick up to 10 of the oldest posts from your sitemap. You get a fix list per post, each fix with a quote, the evidence and the effort, and a refresh backlog. With memory attached, a rerun re-checks only the fixes you marked done and posts it has not seen.

It does not suggest internal links. Internal Link Advisor does that job; run it separately.

## Resources
- `agents/seo-content-refresh.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access and a shell, so the agent can run curl against your sitemap and outbound links. Nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for a refresh log per post. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so curl, web search and web fetch can reach your site and the sources it links to.
- Tools: the full built-in toolset, including the shell (`bash`), which the agent uses for curl. Bash runs without asking for approval.
- It has no analytics or Search Console access, so it cannot tell you which posts lost traffic. The backlog order is a hypothesis.
- Risk: the agent can run any command and anything in the sandbox can leave over the open network. Do not put secrets, private exports or tokens in a session. The agent sends only GET and HEAD requests.

## First-run setup
1. This package has no schedule. Run it when you pick posts to update, or about once a month. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/seo-content-refresh.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to keep a refresh log between runs.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a report:

   Your inputs
   - Site: <your site URL or sitemap URL>
   - Posts: <up to 15 post URLs, one per line, or none to let the agent pick from the sitemap>
   - Target queries: <the query each post should rank for, one per post, or unknown>
   - Audience: <who reads the posts, one sentence>

6. When you fix something, tell the agent in a session with the memory store attached (for example "fixed the pricing line in <post URL>"). The next run re-checks it.

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every stale fact quotes your post and links to the current source, and that every failing link shows its curl status.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
