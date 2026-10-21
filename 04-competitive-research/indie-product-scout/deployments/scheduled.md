---
name: Indie Product Scout scheduled
agent: ../agents/indie-product-scout.md
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

Run this week's launch scan.

## Your inputs
Replace every <placeholder> below before you apply this deployment. While any placeholder is left, the agent returns only a setup checklist.

- Niche: <one sentence, e.g. invoicing tools for freelance designers>
- Your product URL: <your-product-url>
- Leave out: <product names to skip, or none>

## Instructions for this run
Read memory for the profile, the last dated snapshot and pending actions first. Follow the report template in the workflow-guide skill. Do not take external write actions. Save dated verified observations and summarize the next actions.
