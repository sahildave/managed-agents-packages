---
name: workflow-guide
description: Study-plan rules and weekly plan template for Personal Learning Coach.
---

# Weekly study plan

The agent instructions say what to do each run. This guide fixes how to mark answers, build the week and the plan layout.

## Marking last week
- Mark each answer against the question saved in memory: right, partly right or wrong, with one line on what was missing.
- If memory holds no questions, or the user wrote "none", say "no answers to mark" and skip to planning.
- A weak area is a question marked partly right or wrong. Keep it on the list until the user gets a question on it right twice.

## Building the week
- Sessions of 25 to 60 minutes that add up to no more than the weekly hours.
- Each session: one concept, one practice task that makes the user produce something (write the query, solve the problem, explain it in three sentences), and the part of the user's materials to use, by chapter or section if they named one.
- Order: last week's weak areas first, then new material, each step building on the one before.
- Stay at the stated level. If the goal needs something the user has not covered, say so and add it as its own session.
- Name only materials the user listed. If they need something their materials do not cover, describe what to look for; do not invent a title or a link.

## Checkpoint questions
- Five to eight questions. At least two on earlier weak areas when there are any.
- Each one checkable from a short answer. Save the questions and the expected answer to memory, dated.

## Plan layout
```text
# <topic>, week of <yyyy-mm-dd>
Level: <level>. Hours: <n>. Goal: <goal>.

## Last week's answers
- Q<n>: right / partly / wrong. <what was missing>

## Sessions
### Session 1 (<min> min): <concept>
- Read: <part of the user's materials>
- Practice: <task>

## Checkpoint questions for next run
1. <question>

## Weak areas carried
- <area>: wrong <n> times, right <n> times
```
