---
name: workflow-guide
description: Verdict template and evidence rules for Growth Experiment Reviewer.
---

# Growth experiment review

The agent instructions say what to do each run. This guide fixes how to read the numbers, what you can claim and the report layout.

## Reading each experiment
- Take the change, metric, dates and numbers from the user's log. If one is missing, say which and review what is there.
- Rate = events divided by visitors (or sessions, sign-ups, whatever base the user gave). Show the division, for example "18 / 640 = 2.8%". Never compute a rate without a base.
- Compare the test period with the period before it, or with the control if the user ran one. Say which comparison you used.
- Check for things that blur the result: two tests on the same page at the same time, a launch or holiday inside the window, a metric defined differently before and after, a test period shorter than one full week.

## Evidence rules
- Use only the numbers the user pasted. Never fill in a baseline, a traffic figure or an industry benchmark.
- Never state statistical significance, a p-value or a confidence level unless the user's log includes it. When a difference rests on a few dozen events or fewer, say it could be noise.
- A before-and-after comparison without a control shows a change, not its cause. Say so.
- Mark every reason as from the log or as your judgment.

## Verdicts
- Keep: the metric moved the way the hypothesis said, nothing blurs it, and the change is cheap to keep.
- Stop: the metric did not move or moved the wrong way over a full test window.
- Rerun: too few events, a blurred window or a missing baseline. Say what to change in the rerun.

## Report layout
```text
# Experiment review, <yyyy-mm-dd>

Goal: <goal from the inputs>

## <experiment name>: <keep, stop, rerun>
- Change: <what was changed>
- Metric: <metric>, <before> -> <during> (<arithmetic>)
- What blurs it: <issues, or none found>
- What the numbers cannot show: <one line>
- Reason: <one or two lines>

## Next test
- Change: <one change>
- Why: <which result it follows from>
- Metric and base: <metric, the base to divide by>
- Stop date: <date, at least one full week out>

## Next actions
1. <action>
```
Save each verdict and the proposed next test to memory with the date, so the next review can check whether it ran.
