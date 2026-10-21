# Research Reading Digest — Claude Managed Agent native package

Finds five recent papers, reports or long-form posts on the subjects you name and tells you what each one says in plain words. Each pick comes with a dated link to the original, a credibility note that says what kind of source it is and what its claims rest on, and one thing you could try. With memory attached, it does not repeat earlier picks.

## Resources
- `agents/research-reading-digest.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web search and fetch. The shell is disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web search and web fetch can reach public pages. With `limited` networking and no `allowed_hosts`, web search and web fetch return nothing.
- Tools: web search, web fetch and the file tools. The shell (`bash`) is disabled in `agents/research-reading-digest.md`, so the agent cannot run commands.
- Paywalled papers: the agent cannot log in to journals. It reads what is public and marks a pick "abstract only" when that is all it could open.
- Workflows are enabled so the agent can research three or more subjects in parallel. Parallel runs can cost more; with fewer subjects it works in one thread.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private exports or customer data into a session.

## First-run setup
1. This package has no schedule. Run it when you want something new to read. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/research-reading-digest.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to skip earlier picks.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a digest:

   Your inputs
   - Subjects: <one to three subjects, as specific as you can>
   - Depth: <e.g. practitioner, technical, academic>
   - Time window: <e.g. last 30 days, last 90 days>
   - Sources: <sources to prefer or leave out, or none>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every pick links to an original source dated inside your time window.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
