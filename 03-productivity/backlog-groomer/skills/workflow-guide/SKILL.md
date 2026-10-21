---
name: workflow-guide
description: Grooming rules and board template for Personal Backlog Groomer.
---

# Backlog grooming

The agent instructions say what to do each run. This guide fixes how to sort the backlog and the board layout.

## Grooming rules
- Duplicates: two lines that would be closed by the same piece of work. Keep the clearer wording and list the merged lines under it.
- Vague task: no verb, or no way to tell when it is done ("marketing", "fix onboarding"). Rewrite it as a first step of under two hours and keep the original wording in brackets.
- Now holds only what fits the user's weekly hours. Estimate each Now task in hours and show the total against the hours given. If you cannot estimate a task, say so instead of guessing.
- Next is the following two to four weeks. Later is everything else that still serves a goal.
- A task tied to no goal goes under "Suggested deletions" with the reason. Never drop a line silently: every pasted line ends up on the board, merged, or in a suggested deletion.
- Hand-off suggestions name the kind of help (contractor, tool, automation), never a person or company.

## Memory
- Save the dated board: each task, its column and its estimate.
- On the next run, flag tasks that sat in Now on the previous board and are still open. Without a previous board, say "no earlier board" and flag nothing.

## Board layout
```text
# Backlog board, <yyyy-mm-dd>
Weekly hours: <n>. Now totals <n> hours.

## Now
- <task> (<est> h, goal: <goal>) <"in Now since <date>" if memory shows it>

## Next
- <task> (goal: <goal>)

## Later
- <task> (goal: <goal>)

## Merged duplicates
- "<kept wording>" ← "<merged line>", "<merged line>"

## Suggested deletions or hand-offs
- <task>: <reason: no goal, outdated, someone else's job>

## Questions for you
- <what you need to know to place a task>
```
