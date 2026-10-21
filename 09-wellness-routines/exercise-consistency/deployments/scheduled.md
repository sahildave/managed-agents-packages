---
name: Exercise Consistency Planner scheduled
agent: ../agents/exercise-consistency.md
environment_id: ../environments/cloud.yaml
resources:
- path: ../memory_stores/history.yaml
  access: read_write
  instructions: Read prior dated snapshots and preferences before working; record the current evidence,
    changes, and agreed next steps in the writable memory store. Do not invent missing history.
schedule:
  type: cron
  expression: 0 9 * * 1
  timezone: UTC
---

Run the Exercise Consistency Planner recurring workflow. Consult memory for the latest scope, previous findings, and pending actions. If no initial profile or necessary inputs exist, produce a short setup checklist rather than fabricate a report. Do not take external write actions. Save dated verified observations and summarize the next actions.
