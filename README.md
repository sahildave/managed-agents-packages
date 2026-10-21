# Managed agent packages

Seven Claude Managed Agent packages for indie hackers and solo devs. Each folder is a self-contained package for the `ant` CLI: an agent, a cloud environment, a skill, a memory store and, for the scheduled ones, a deployment.

| Package | What it does | Runs |
|---|---|---|
| `02-content/ship-log-posts` | Turns the last seven days of commits into X and Bluesky drafts | On demand |
| `01-seo-growth/site-seo-watch` | Checks your site's SEO and technical health, reports what changed | Weekly schedule |
| `01-seo-growth/keyword-opportunity-researcher` | Finds search queries your site doesn't answer yet | On demand |
| `01-seo-growth/landing-page-critic` | Reviews a landing page for clarity and conversion | On demand |
| `02-content/content-idea-hunter` | Finds questions your audience is asking | On demand |
| `04-competitive-research/competitor-change-tracker` | Reports what changed on competitor pages since last week | Weekly schedule |
| `04-competitive-research/indie-product-scout` | Finds new launches in your niche | On demand |

## Use one

1. Install the [`ant` CLI](https://platform.claude.com/docs/en/managed-agents/quickstart) and set `ANTHROPIC_API_KEY`.
2. `cd` into a package and read its `README.md`.
3. Run `ant apply --dry-run .` to see what it would create.
4. For an on-demand package, run `ant apply .`, start a session in Console and send the "Your inputs" block from its README as the first message.
5. For a scheduled package, fill in the "Your inputs" block and the timezone in `deployments/scheduled.md` first. Then `ant apply .` also creates the schedule, which starts billed runs. Each run stops at the budget set in the deployment file. The package README shows how to install it without the schedule.

Nothing here posts or emails on your behalf, and only the two scheduled packages start runs by themselves. Agents draft; you decide.

Browse them with examples at https://www.coduo.co/managed-agents.

## Licence

MIT. See `LICENSE`.
