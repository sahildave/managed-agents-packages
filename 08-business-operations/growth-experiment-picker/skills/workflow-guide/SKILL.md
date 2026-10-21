---
name: workflow-guide
description: Source rules, verdict rules, evidence rules and report template for Growth Experiment Picker.
---

# Growth experiment picker

The agent instructions say what to do each run. This guide fixes where examples come from, how to read the numbers, what you can claim and the report layout.

## Finding examples
- Sources: founder interviews and posts on Indie Hackers, founders' own blogs, podcast episode pages and public build-in-public threads. Record which ones you could reach.
- An example counts only if you opened the page and it names the product, what the founder tried and when. Cite the URL and the date on the page; if no date is shown, say "date not shown".
- Comparable means a similar stage, audience or price point to the user's product. Say which of these matches.
- Report another product's results only as the founder published them, quoted and linked. Never fill in a number they did not give.
- Skip channels the user already tried, unless the example shows a fixable reason theirs failed. Skip experiments already in the memory log.
- If subagents are enabled, give each one a separate channel or source to search, then check every link they return before you cite it.

## Sizing
- Each experiment must run in one week within the user's weekly hours. Give the hours it needs.
- The smallest version is the one that can show whether the idea works, not the full rollout.
- The success bar is a number the user can count themselves, with its base, for example "10 trial sign-ups from 300 visitors".

## Reading the last experiment
- Take the change, metric, dates and numbers from the user's input. If one is missing, say which and review what is there.
- Rate = events divided by visitors (or sessions, sign-ups, whatever base the user gave). Show the division, for example "18 / 640 = 2.8%". Never compute a rate without a base.
- Compare against the success bar saved in memory. If memory has no bar for it, compare the test period with the period before it, and say which comparison you used.
- Check for things that blur the result: two tests on the same page at the same time, a launch or holiday inside the window, a metric defined differently before and after, a test period shorter than one full week.

## Evidence rules
- Use only the numbers the user pasted for their own product. Never fill in a baseline, a traffic figure or an industry benchmark.
- Never state statistical significance, a p-value or a confidence level unless the user's log includes it. When a difference rests on a few dozen events or fewer, say it could be noise.
- A before-and-after comparison without a control shows a change, not its cause. Say so.
- An example from another product shows that it was tried, not that it will work for the user. Mark every reason as from a source, from the user's input or as your judgment.

## Verdicts
- Keep: the metric met the bar, nothing blurs it, and the change is cheap to keep.
- Stop: the metric missed the bar or moved the wrong way over a full test window.
- Rerun: too few events, a blurred window or a missing baseline. Say what to change in the rerun.

## Report layout
```text
# Growth experiments, <yyyy-mm-dd>

Goal: <goal from the inputs>

## Last experiment: <name>: <keep, stop, rerun, or "none reported">
- Bar: <bar from memory, or "no bar saved">
- Result: <before> -> <during> (<arithmetic>)
- What blurs it: <issues, or none found>
- What the numbers cannot show: <one line>

## Experiment 1: <name>
- Example: <product> (<URL>, <date>): <what they tried, and results only as published>
- Why it fits you: <stage, audience or price match>
- Hypothesis: <if we do X, Y will happen>
- One-week version: <smallest version>, about <h> hours
- Metric and bar: <metric, base, the number that counts as "worked">

## Experiment 2 ...

## Sources I could not reach
- <source>: <reason>

## Next actions
1. <action>
```
Save each picked experiment to memory with the date: hypothesis, metric, success bar and source URL. Save each verdict with the reported result, so the next run can check it against the bar. Keep the list of channels tried.
