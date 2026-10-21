---
name: Get Listed scheduled
agent: ../agents/get-listed.md
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
    amount: "200" # US cents per run: 200 = $2.00. The run stops at this cap.
    currency: USD
---

Run this week's listing check.

## Your inputs
Replace every <placeholder> below before you apply this deployment. While any placeholder is left, the agent returns only a setup checklist.

- Product: <product name and URL>
- Category: <what a buyer would search, e.g. invoice app for freelancers>
- Competitors: <3 to 5 competitor names and URLs, one per line>
- Domains to skip: <comma-separated, or none>
- Pitch angle: <one sentence on why a list's readers should know about you>

## Instructions for this run
Read memory for the profile, the prospect statuses and the last dated snapshot first. Report only pages first seen since that snapshot. Follow the report template in the workflow-guide skill. Do not take external write actions. Save dated verified observations and summarize the next actions.
