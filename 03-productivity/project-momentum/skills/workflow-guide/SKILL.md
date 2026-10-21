---
name: workflow-guide
description: Status rules and momentum-table template for Project Momentum Tracker.
---

# Project momentum

The agent instructions say what to do each run. This guide fixes how to judge each project and the table layout.

## Status rules
- Moving: the update names a finished step toward the next milestone.
- Slowing: the update names work but no finished step, or the milestone date has moved.
- Stalled: the update says nothing moved, and the last snapshot in memory said the same. Without a snapshot, one "nothing" is "slowing (no baseline)".
- Judge only from the user's update and memory. If an update is unclear, mark the project "unclear" and ask one question.
- Blocker: name one only if the user's update states it. Otherwise write "not stated".
- Next action: one physical step under two hours that the user can start today ("email the designer the three logo files"), not a goal ("finish branding").
- If a milestone date has passed, say so with the date.

## Memory
- Save a dated line per project: status, milestone, target date, blocker.
- Count consecutive runs a project has been stalled and show the count.

## Table layout
```text
# Project momentum, <yyyy-mm-dd>

| Project | Status | Since | Next milestone (date) | Blocker |
| --- | --- | --- | --- | --- |
| <name> | stalled | <n> runs | <milestone> (<date>) | <stated blocker or not stated> |

## Next actions
- <project>: <one step under two hours>

## Questions for you
- <project>: <what you need to know>
```
