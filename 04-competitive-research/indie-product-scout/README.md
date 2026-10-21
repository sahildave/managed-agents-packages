# Indie Product Scout — Claude Managed Agent native package

Scans public launch sources for new products in your niche, opens their sites, and briefs you on how each one positions itself next to your product.

## Resources
- `agents/indie-product-scout.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the report template and evidence rules for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web search and fetch. The shell is disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web search and web fetch can reach public pages. With `limited` networking and no `allowed_hosts`, web search and web fetch return nothing.
- Tools: web search, web fetch and the file tools. The shell (`bash`) is disabled in `agents/indie-product-scout.md`, so the agent cannot run commands.
- Risk: anything in the sandbox can leave over the open network. Do not paste secrets, private exports or customer data into a session.

## First-run setup
1. This package has no schedule. Run it when you want a fresh look at your niche. Set a session budget in Console when you start a run; no run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/indie-product-scout.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to compare against past runs.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a report:

   Your inputs
   - Niche: <one sentence, e.g. invoicing tools for freelance designers>
   - Your product URL: <your-product-url>
   - Leave out: <product names to skip, or none>

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that every claim in the report links to a source.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured.
