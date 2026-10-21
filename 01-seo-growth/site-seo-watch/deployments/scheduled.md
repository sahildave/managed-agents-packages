---
name: Site SEO Watch scheduled
agent: ../agents/site-seo-watch.md
environment_id: ../environments/cloud.yaml
resources:
- path: ../memory_stores/history.yaml
  access: read_write
  instructions: Read prior dated snapshots and preferences before working; record the current evidence,
    changes, and agreed next steps in the writable memory store. Do not invent missing history.
schedule:
  type: cron
  expression: 0 8 * * 1
  timezone: UTC # Set this to your IANA timezone, for example Europe/London or America/New_York.
budget:
  type: limit
  max_list_cost:
    amount: "100" # US cents per run: 100 = $1.00. The run stops at this cap.
    currency: USD
---

Run this week's site SEO check.

## Your inputs
Replace every <placeholder> below before you apply this deployment. While any placeholder is left, the agent returns only a setup checklist.

- Site URL: <your-site-url>
- Key pages: <up to 10 full URLs, one per line>
- Target market: <country and language, e.g. US English>

## Instructions for this run
Read memory for the profile, the last dated snapshot and pending actions first. Follow the report template in the workflow-guide skill. Do not take external write actions. Save dated verified observations and summarize the next actions.
