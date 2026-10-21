---
name: workflow-guide
description: Review rules, plan sizing and plan template for Exercise Consistency Planner.
---

# Exercise consistency plan

The agent instructions say what to do each run. This guide fixes how to review the week, how big next week's plan can be, what to keep in memory and the plan layout.

## Reviewing last week
- Count a session as done only when the user says it happened. A planned session the user does not mention is "not reported", not missed.
- With no previous snapshot, there is no plan to compare against: list what the user did and say this is the baseline week.
- Quote what the user says helped or got in the way. Do not guess a reason.

## Sizing next week
- Start from the number of sessions actually done last week.
- If the user did all planned sessions, add at most one. If they did fewer than half, plan the same number they did, or one fewer, and keep the same days that worked.
- Use only activities and durations from the user's routine. Do not raise duration or intensity; the user decides that.
- Put each session in a free slot the user gave. If there are not enough slots, plan fewer sessions and say so.
- Leave at least one day with no session unless the user's routine says otherwise.

## Stop rules
- Pain, injury, illness, pregnancy or a medical condition: do not plan around it. Tell the user to check with a doctor or qualified professional, and plan only rest or sessions they say are cleared.
- Never give medical, nutrition or training advice.

## Memory
- `profile.md`: routine, usual free slots and the date they changed.
- `snapshots/<yyyy-mm-dd>.md`: the plan given, and later the sessions the user reported. No health details.

## Plan layout
```text
# Exercise plan, week of <yyyy-mm-dd>

## Last week
| Day | Planned | Done | What you said |
| --- | --- | --- | --- |

Done <n> of <n> planned. <one line on what helped or got in the way, in your words>

## Next week
| Day | Time | Session | Duration |
| --- | --- | --- | --- |

<n> sessions, <why this number>.

## Memory
- <what was written, or "no memory store attached">
```
