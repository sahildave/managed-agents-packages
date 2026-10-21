---
name: Ship Log to Posts scheduled
agent: ../agents/ship-log-posts.md
environment_id: ../environments/cloud.yaml
resources:
- path: ../memory_stores/history.yaml
  access: read_write
  instructions: Read prior dated snapshots and preferences before working; record the current evidence,
    changes, and agreed next steps in the writable memory store. Do not invent missing history.
schedule:
  type: cron
  expression: 0 16 * * 5
  timezone: UTC # Set this to your IANA timezone, for example Europe/London or America/New_York.
budget:
  type: limit
  max_list_cost:
    amount: "100" # US cents per run: 100 = $1.00. The run stops at this cap.
    currency: USD
---

Draft this week's ship-log posts.

## Your inputs
Replace every <placeholder> below before you apply this deployment. While any placeholder is left, the agent returns only a setup checklist.

- Repository: <https://github.com/your-name/your-repo>
- Product name: <your-product-name>
- Voice: <e.g. plain and a bit dry, no emoji, no hype words>

## Instructions for this run
Read memory for the profile, the last dated snapshot and pending actions first. Follow the report template in the workflow-guide skill. Do not take external write actions. Save dated verified observations and summarize the next actions.
