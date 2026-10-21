---
name: workflow-guide
description: Scorecard rules, memory layout and report template for Weekly Accountability Partner.
---

# Weekly accountability check-in

The agent instructions say what to do each run. This guide fixes how to score commitments, what to keep in memory and the report layout.

## Scoring
- Done: the user says it is finished.
- Partly done: the user names some progress but not the finish.
- Not done: the user says it did not happen.
- Unknown: the user did not mention it. Never score silence as not done.
- Score only from the user's words in this session. Quote the phrase you scored from.

## Repeating obstacles
- An obstacle repeats when the user names the same cause in this run and in at least one earlier dated snapshot. Cite the snapshot dates.
- Without a previous snapshot, list this week's obstacles and say there is no baseline yet.
- Name the obstacle in the user's words. Do not guess a cause the user did not give.

## Next commitments
- At most three. Each one is a single action with a finish line the user can check next week.
- If fewer than half of this week's commitments were done, propose fewer or smaller ones, not more.

## Memory
- `profile.md`: the latest inputs and the date they changed.
- `snapshots/<yyyy-mm-dd>.md`: commitments, scores, obstacles and next commitments for that run. Append; never rewrite an old snapshot.
- Leave out passwords, money details, health details and anything the user marks private.

## Report layout
```text
# Check-in, week ending <yyyy-mm-dd>

## Scorecard
| Commitment | Score | From your update |
| --- | --- | --- |
| <commitment> | done / partly done / not done / unknown | "<quote>" |

## Obstacles
- <obstacle>: this week; also on <snapshot dates>, or "first time"

## Next week
1. <commitment>: done when <check>

## Memory
- <what was written, or "no memory store attached">
```
