# Ship Log to Posts — Claude Managed Agent native package

Reads the last seven days of commits and merged pull requests from your public GitHub repository and drafts build-in-public posts for X and Bluesky, plus one short thread. Every post links to the commit or pull request it describes. It never posts anything.

## Resources
- `agents/ship-log-posts.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox that reaches only GitHub and package registries, so the agent can clone a public repository. Web search and web fetch are disabled in the agent.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `limited` with `allow_package_managers: true`. That opens package registries and GitHub (`github.com`, `api.github.com`, `codeload.github.com`, `raw.githubusercontent.com`) and nothing else.
- Tools: the shell (`bash`) for git and curl, plus the file tools. Web search and web fetch are disabled in `agents/ship-log-posts.md`; they would return nothing on this network anyway.
- Private repositories: when you create a session, attach a `github_repository` resource with your own GitHub token. Never put a token in any file of this package, in a session message or in memory.
- It never posts. You copy the drafts you like into X or Bluesky yourself.

## First-run setup
1. This package has no schedule. Run it after you ship, usually once a week. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/ship-log-posts.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to compare against past runs.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a report:

   Your inputs
   - Repository: <https://github.com/your-name/your-repo>
   - Product name: <your-product-name>
   - Voice: <e.g. plain and a bit dry, no emoji, no hype words>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every claim in the report links to a source.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
