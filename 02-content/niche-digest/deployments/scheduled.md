---
name: Niche Digest scheduled
agent: ../agents/niche-digest.md
environment_id: ../environments/cloud.yaml
resources:
- path: ../memory_stores/history.yaml
  access: read_write
  instructions: Read prior dated snapshots and preferences before working; record the current evidence,
    changes, and agreed next steps in the writable memory store. Do not invent missing history.
schedule:
  type: cron
  expression: 0 9 * * 4
  timezone: UTC # Set this to your IANA timezone, for example Europe/London or America/New_York.
budget:
  type: limit
  max_list_cost:
    amount: "200" # US cents per run: 200 = $2.00. The run stops at this cap.
    currency: USD
---

Draft this week's newsletter issue.

## Your inputs
Replace every <placeholder> below before you apply this deployment. While any placeholder is left, the agent returns only a setup checklist.

- Niche: <the three to five topics your newsletter covers>
- Readers: <who reads your newsletter, one sentence>
- Sources: <blogs, changelogs, subreddits, Hacker News or arXiv categories you trust, one per line>
- Leave out: <sources or sites to skip, or none>
- Items: <how many items per issue, 5 to 8>
- Voice: <e.g. plain and a bit dry, no emoji, no hype words>

## Instructions for this run
Read memory for the profile, the last dated snapshot and pending actions first. Follow the report template in the workflow-guide skill. Do not take external write actions. Save dated verified observations and summarize the next actions.
