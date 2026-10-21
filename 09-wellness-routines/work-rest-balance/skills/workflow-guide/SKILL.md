---
name: workflow-guide
description: Log reading rules, rest-block rules and report template for Work-Rest Balance Reviewer.
---

# Work and rest review

The agent instructions say what to do each run. This guide fixes how to read the log, how to check rest goals, what to keep in memory and the report layout.

## Reading the log
- Take hours only from what the user wrote. "Worked late" with no time is "late, hours not given", not a number you estimate.
- A day the log does not mention is "not logged", never a day off.
- Totals cover only the days with hours. Say how many days that is.

## Checking rest goals
- Each goal the user gave gets one line: met, missed or unknown, with the log text that decides it.
- A pattern repeats when the same goal is missed in this week and at least one earlier snapshot. Cite the dates. Without a previous snapshot, say there is no baseline yet.

## Rest blocks for next week
- Two or three blocks, each with a day and a time range.
- Place them around the fixed commitments the user gave; never on top of one.
- Prefer the goal missed most often. Keep each block small enough to keep: an evening, a morning, one day off.
- Every block is a suggestion. The user puts it in their own calendar.

## Stop rules
- Exhaustion, low mood, poor sleep, pain or any health concern: do not analyse it. Say this agent is not the right help and suggest a doctor or qualified professional.
- No medical, sleep or mental health advice.

## Memory
- `profile.md`: rest goals and the date they changed.
- `snapshots/<yyyy-mm-dd>.md`: hours per logged day, goal results and the blocks suggested. No health details.

## Report layout
```text
# Work and rest, week ending <yyyy-mm-dd>

## Last week
| Day | Work hours | Note from your log |
| --- | --- | --- |

<total> hours over <n> logged days.

## Rest goals
- <goal>: met / missed / unknown. "<log text>". Also missed on <dates>, or "no baseline yet".

## Protect next week
1. <day>, <start>-<end>: <goal it serves>

## Memory
- <what was written, or "no memory store attached">
```
