---
name: Thread Watch scheduled
agent: ../agents/thread-watch.md
environment_id: ../environments/cloud.yaml
resources:
- path: ../memory_stores/history.yaml
  access: read_write
  instructions: Read prior dated snapshots and preferences before working; record the current evidence,
    changes, and agreed next steps in the writable memory store. Do not invent missing history.
schedule:
  type: cron
  expression: 0 9 * * 1
  timezone: UTC # Set this to your IANA timezone, for example Europe/London or America/New_York.
budget:
  type: limit
  max_list_cost:
    amount: "200" # US cents per run: 200 = $2.00. The run stops at this cap.
    currency: USD
---

Run this week's thread watch.

## Your inputs
Replace every <placeholder> below before you apply this deployment. While any placeholder is left, the agent returns only a setup checklist.

- Product: <name and URL>
- Competitors: <3 to 5 competitor names, one per line>
- Problem phrases: <3 to 6 phrases your buyers use, e.g. track freelance invoices>
- Communities: <subreddits, Hacker News, Indie Hackers or a forum URL, one per line>
- Reply rule: <how you reply, e.g. answer first, disclose I'm the maker, no links unless asked>

## Instructions for this run
Read memory for the profile, the last dated snapshot and pending actions first. Follow the report template in the workflow-guide skill. Do not take external write actions. Save dated verified observations and summarize the next actions.
