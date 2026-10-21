# Landing Page Conversion Critic — Claude Managed Agent native package

Reads your landing page the way a first-time visitor would and tells you what gets in the way of signing up, with small copy tests to try. Run it when you change the page; it has no schedule.

## Resources
- `agents/landing-page-critic.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web search and fetch. The shell is disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web search and web fetch can reach public pages. With `limited` networking and no `allowed_hosts`, web search and web fetch return nothing.
- Tools: web search, web fetch and the file tools. The shell (`bash`) is disabled in `agents/landing-page-critic.md`, so the agent cannot run commands.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private exports or customer data into a session.

## First-run setup
1. This package has no schedule. Run it when you change your landing page. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. One measured run cost $0.18 ([example run](https://github.com/sahildave/managed-agents-packages/blob/main/examples/landing-page-critic-2026-10-21.md)).
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/landing-page-critic.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to remember past reviews.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a review:

   Your inputs
   - Landing page URL: <your-landing-page-url>
   - Ideal customer: <who should sign up, one sentence>
   - Goal: <the one action you want, e.g. start a free trial>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every claim in the report links to a source.
4. In a deployment-created session, ask it to write a dated note to memory. Launch a second session and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. Ran once live on 2026-10-21 with real inputs: see [the example run](https://github.com/sahildave/managed-agents-packages/blob/main/examples/landing-page-critic-2026-10-21.md) (list cost $0.18).
