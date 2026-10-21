---
name: workflow-guide
description: Planning rules and week-plan template for Plan My Week.
---

# Week plan

The agent instructions say what to do each run. This guide fixes how to fill the hours and the plan layout.

## Planning rules
- Free hours per day = focus hours given minus fixed commitments that fall in them. Show the arithmetic per day.
- Plan at most four fifths of the free hours. The rest absorbs what overruns.
- Use the user's estimates. Where a task has none, give one and mark it "(est.)". Round to half hours.
- Order: tasks with a deadline this week first, then tasks that serve a goal, then the rest.
- Put the hardest task of each day first, unless the user's notes say otherwise.
- A carried task comes from last week's plan in memory and was not reported done. Mark it "(carried from <date>)". Without an earlier plan, carry nothing.
- Never move a fixed commitment. If the commitments alone exceed the hours, say so and plan nothing that day.

## Memory
- Save the dated plan: each task, its day and its estimate.
- If the user says which tasks they finished, record that against last week's plan. Otherwise mark them "status unknown"; do not assume they were done.

## Plan layout
```text
# Week of <yyyy-mm-dd>
Goals: <goal 1>; <goal 2>

## Monday <date>: <free> h free, <planned> h planned
- <task> (<h> h) <goal or deadline>
- Fixed: <commitment, time>

## Tuesday ...

## Did not fit
- <task> (<h> h): <why it lost out>

## Questions for you
- <anything that changes the plan if answered>
```
