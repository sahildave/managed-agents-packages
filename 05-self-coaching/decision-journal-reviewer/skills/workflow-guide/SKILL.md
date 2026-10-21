---
name: workflow-guide
description: Decision log format, review rules and report template for Decision Journal Reviewer.
---

# Decision journal review

The agent instructions say what to do each run. This guide fixes the log format, how to judge a decision and the report layout.

## Logging a decision
Each new decision gets one file, `decisions/<yyyy-mm-dd>-<short-name>.md`, written once:
```text
Decided: <yyyy-mm-dd>
Decision: <what was chosen, and what was not>
Reasoning: <the user's words>
Assumptions: <each one on its own line>
Prediction: <what the user expects to happen, and by when>
Check on: <yyyy-mm-dd>
```
If the user gives no check date, propose one and mark it as proposed. If the user gives no prediction, ask for one in the report; a decision with no prediction cannot be reviewed.

## Reviewing a decision
- A decision is due when its check date has passed or the user reports an outcome for it.
- Outcome: only what the user reported. With no report, the decision stays open; never guess an outcome.
- For each assumption: held, did not hold, or not yet known. Quote the outcome text that decides it.
- Keep two questions apart: was the reasoning sound on what was known at the time, and did it turn out well. A good outcome does not prove good reasoning.
- Append the review to the decision file under `Review <yyyy-mm-dd>:`. Never edit the original lines.

## Report layout
```text
# Decision review, <yyyy-mm-dd>

## Logged today
- <decision>: check on <date>

## Due for review
### <decision> (decided <date>)
- Predicted: <prediction>
- Happened: "<user's outcome text>"
- Assumptions: <assumption>: held / did not hold / not yet known
- Reasoning at the time: <sound / weak, and why, using only what was known then>
- Next check: <date, or "closed">

## Still open
- <decision>: check on <date>, no outcome reported

## Memory
- <what was written, or "no memory store attached">
```
