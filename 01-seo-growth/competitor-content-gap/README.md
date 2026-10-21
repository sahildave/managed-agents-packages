# Competitor Content Gap — Claude Managed Agent native package

Reads the sitemaps of up to five competitors with curl, counts their pages by type (blog, comparison, alternatives, use case, integration, docs) and shows the topics they have pages for and you don't. Gaps are ranked by buyer intent: comparison and alternatives pages first, then use cases, then educational posts. A rerun lists the pages each competitor published since the last run.

It starts from what competitors built. Keyword Opportunity Researcher starts from what buyers search; run it next on the top gap. Competitor Change Tracker watches known competitors' pricing and changelog pages for changes, and Indie Product Scout finds new entrants.

## Resources
- `agents/competitor-content-gap.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access and a shell, so the agent can run curl against public sitemaps. Nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated sitemap snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so curl and web fetch can reach the sites.
- Tools: the full built-in toolset, including the shell (`bash`), which the agent uses for curl. Bash runs without asking for approval.
- Subagents and workflows are enabled so it can read several competitors in parallel. That can cost more than a serial run.
- It has no keyword or rank tool, so it reports no search volumes or rankings.
- Risk: the agent can run any command and anything in the sandbox can leave over the open network. Do not put secrets, private exports or tokens in a session. The agent sends only GET and HEAD requests.

## First-run setup
1. This package has no schedule. Run it when you plan new content, or about once a month to see what competitors published. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/competitor-content-gap.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to report new competitor pages since the last run.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a report:

   Your inputs
   - Site URL: <your-site-url>
   - Competitors: <up to 5 competitor site URLs, comma-separated>
   - Country and language: <e.g. US English>
   - Topics to skip: <comma-separated, or none>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that each page count names the sitemap it came from, that every gap links to competitor pages, and that topics marked "not found" really have no page on your site.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
