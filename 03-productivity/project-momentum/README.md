# Project Momentum Tracker — Claude Managed Agent native package

An independent package for `ant apply`. It uses Anthropic-native resources only.

## Resources
- `agents/project-momentum.md` — primary agent, built-in tools, linked skill, selective multiagent capabilities.
- `skills/workflow-guide/SKILL.md` — local, self-contained task guide (no GitHub rate limits).
- `environments/cloud.yaml` — default minimal cloud sandbox; no extra CLI or packages.
- `memory_stores/history.yaml` — persistent memory resource. It does **not** attach automatically to arbitrary interactive sessions.
- `deployments/scheduled.md` — scheduled execution; explicitly attaches memory read/write.

## First-run setup
1. Run `ant apply --dry-run .` and inspect the resource plan.
2. Edit `deployments/scheduled.md` to choose your actual timezone and schedule. **Do not apply the deployment until you want recurring billed runs.**
3. To install the agent, environment, skill and memory **without scheduling**, run:

   `ant apply agents/project-momentum.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

4. For scheduled automation, run `ant apply .` after reviewing the deployment. Scheduled sessions created by this deployment will receive the memory store.
5. If you create an interactive session in Console, attach the existing memory store yourself at creation with `read_write` access. Merely installing it does not mount it in an interactive session.
6. At first run, provide your context, preferred cadence, data sources, and desired output. The agent will not make up missing inputs.

## Tools, orchestration, and MCP
- Native agent toolset is configured. There are no third-party CLI dependencies or authenticated MCP servers bundled.
- Multiagent capabilities are explicitly configured according to task complexity; consult `agents/project-momentum.md`. Parallel runs can cost more.
- Authenticated APIs such as Google Search Console, Stripe, GitHub, or social platforms are **not connected automatically**. Use exports where possible, or manually add an authenticated MCP integration where needed. Do not put personal API tokens in downloadable files.
- The skill is bundled locally to avoid GitHub API rate limiting during installation.

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run a representative task using real user-provided data.
3. In a deployment-created session, ask it to write a dated note to memory. Launch a second deployment session and verify it can read that note.
4. If multiagent is enabled, request an appropriate broad task and inspect session events for real subagent/workflow activity.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.**
