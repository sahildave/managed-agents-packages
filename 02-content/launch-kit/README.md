# Launch Kit — Claude Managed Agent native package

Picks the launch channels that fit your product, such as Product Hunt, Show HN, named subreddits, Indie Hackers, directories and newsletters that take submissions. For each one it reads the current rules on the channel's own page and links them, then drafts every asset to those rules: the Product Hunt tagline and maker comment, the Show HN title and first comment, a post per subreddit, a thread, an email to your list. It adds a dated checklist from a week before launch to three days after, and the risks. It never posts anything.

## Resources
- `agents/launch-kit.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web search and fetch. The shell is disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web search and web fetch can reach public pages. With `limited` networking and no `allowed_hosts`, web search and web fetch return nothing.
- Tools: web search, web fetch and the file tools. The shell (`bash`) is disabled in `agents/launch-kit.md`, so the agent cannot run commands.
- Workflows are enabled so the agent can check the rules of three or more channels in parallel. Parallel runs can cost more; with fewer channels it works in one thread.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private exports or customer data into a session.
- It never posts or submits. You copy the drafts you like into each channel yourself.

## First-run setup
1. This package has no schedule. Run it once to plan the launch, again two days before launch day to refresh the rules and the checklist, and once three days after to log which channels worked for your next launch. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/launch-kit.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want a later run to pick up the same launch and reuse what you learned from the last one.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a launch kit:

   Your inputs
   - Product: <name, URL and one-line pitch>
   - Launch date: <yyyy-mm-dd>
   - Audience: <who the product is for, one sentence>
   - What's new: <first launch, relaunch or major feature, and what it does>
   - Channels: <the channels you are open to, e.g. Product Hunt, Show HN, r/SaaS, your newsletter; or suggest>
   - Proof: <real users, numbers, quotes, a demo video or pricing you can show, or none>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every channel rule links to the channel's own page with a fetch date, that each draft fits the limits stated for its channel, and that the copy uses no proof you did not give.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
