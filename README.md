# Managed agent packages

28 Claude Managed Agent packages for indie hackers and solo devs. Each folder is a self-contained package for the `ant` CLI: an agent, a cloud environment, a skill, a memory store and, for the scheduled ones, a deployment.

| Package | What it does | Runs |
|---|---|---|
| `01-seo-growth/keyword-opportunity-researcher` | Finds search queries your site doesn't answer yet | On demand |
| `01-seo-growth/competitor-content-gap` | Finds topics your competitors have pages for and you don't | On demand |
| `01-seo-growth/get-listed` | Finds "best X" lists and directories that name competitors but not you | Weekly schedule |
| `01-seo-growth/seo-content-refresh` | Lists stale facts, failing links and missing answers in older posts | On demand |
| `01-seo-growth/internal-link-advisor` | Suggests internal links to add, with the sentence and anchor | On demand |
| `01-seo-growth/landing-page-critic` | Reviews a landing page for clarity and conversion | On demand |
| `01-seo-growth/site-seo-watch` | Checks your site's SEO and technical health, reports what changed | Weekly schedule |
| `02-content/content-idea-hunter` | Finds questions your audience is asking | On demand |
| `02-content/ship-log-posts` | Turns the last seven days of commits into X and Bluesky drafts | On demand |
| `02-content/post-repurposer` | Turns something you published into drafts for each platform | On demand |
| `02-content/evergreen-posts` | Drafts fresh versions of your past posts that worked best | On demand |
| `02-content/launch-kit` | Picks launch channels, checks their rules and drafts every asset | On demand |
| `02-content/niche-digest` | Drafts a weekly newsletter issue from your niche's news | Weekly schedule |
| `08-business-operations/thread-watch` | Finds threads asking for a tool like yours, with drafted replies | Weekly schedule |
| `08-business-operations/growth-experiment-picker` | Suggests three growth experiments others ran, and judges your last one | On demand |
| `04-competitive-research/competitor-change-tracker` | Reports what changed on competitor pages since last week | Weekly schedule |
| `04-competitive-research/indie-product-scout` | Finds new launches in your niche | On demand |
| `03-productivity/plan-my-week` | Plans your week within the hours you have, with a daily focus line | On demand |
| `03-productivity/backlog-groomer` | Sorts your backlog into Now, Next and Later | On demand |
| `03-productivity/project-momentum` | Shows which projects stalled and one next action for each | On demand |
| `03-productivity/weekly-retrospective` | Runs a Keep, Stop, Start review of your week | On demand |
| `05-self-coaching/accountability-partner` | Scores the commitments you set for the week | On demand |
| `05-self-coaching/decision-journal-reviewer` | Checks past decisions against what happened | On demand |
| `06-learning/learning-coach` | Plans a study week from the materials you list | On demand |
| `06-learning/research-reading-digest` | Picks five recent reads on your subjects | On demand |
| `07-finance-admin/subscription-expense-reviewer` | Flags duplicate, rising and renewing subscriptions from charges you paste | On demand |
| `09-wellness-routines/exercise-consistency` | Plans next week's exercise from your routine and free time | On demand |
| `09-wellness-routines/work-rest-balance` | Compares last week's work and rest with your rest goals | On demand |

## Use one

1. Install the [`ant` CLI](https://platform.claude.com/docs/en/managed-agents/quickstart) and set `ANTHROPIC_API_KEY`.
2. `cd` into a package and read its `README.md`.
3. Run `ant apply --dry-run .` to see what it would create.
4. For an on-demand package, run `ant apply .`, start a session in Console and send the "Your inputs" block from its README as the first message.
5. For a scheduled package, fill in the "Your inputs" block and the timezone in `deployments/scheduled.md` first. Then `ant apply .` also creates the schedule, which starts billed runs. Each run stops at the budget set in the deployment file. The package README shows how to install it without the schedule.

Nothing here posts or emails on your behalf, and only the five scheduled packages start runs by themselves. Agents draft; you decide.

Browse them with examples at https://www.coduo.co/managed-agents.

## Licence

MIT. See `LICENSE`.
