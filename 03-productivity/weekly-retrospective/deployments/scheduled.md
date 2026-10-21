---
name: Weekly Retrospective Facilitator scheduled
agent: ../agents/weekly-retrospective.md
environment_id: ../environments/cloud.yaml
resources:
- path: ../memory_stores/history.yaml
  access: read_write
  instructions: Read prior dated snapshots and preferences before working; record the current evidence,
    changes, and agreed next steps in the writable memory store. Do not invent missing history.
schedule:
  type: cron
  expression: 0 17 * * 5
  timezone: UTC
---

Run the Weekly Retrospective Facilitator recurring workflow. Consult memory for the latest scope, previous findings, and pending actions. If no initial profile or necessary inputs exist, produce a short setup checklist rather than fabricate a report. Do not take external write actions. Save dated verified observations and summarize the next actions.
