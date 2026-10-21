---
name: workflow-guide
description: Source rules, date checks and issue template for Newsletter Curator.
---

# Newsletter issue

The agent instructions say what to do each run. This guide fixes what counts as a good item and the issue layout.

## Source rules
- Prefer the primary source: the company's changelog or blog, the paper, the release notes, the original post. Link a news write-up only when there is no primary source, and say so.
- Every item needs a publication date read from the page itself. If the page shows no date, or the date is older than seven days, leave the item out.
- Never use a source the user listed under "Leave out", and never reuse a link that memory shows in a past issue.
- Do not quote more than one short sentence from a source. Write the summary in your own words.
- "Why it matters" must be about the readers named in the inputs. If you cannot say why it matters to them, drop the item.
- If a topic had no news worth including this week, say so rather than filling the slot.

## Issue layout
```text
# <Issue title>, <yyyy-mm-dd>

<Two-sentence intro in the user's voice>

## 1. <Item headline>
<Two-sentence summary.>
Why it matters: <one sentence for these readers>
Source: <link> (published <yyyy-mm-dd>)

## 2. ...

## Topics with nothing this week
- <topic>

## Sources I could not reach
- <site>: <reason>
```
Save each included link and the issue date to memory so the next issue skips them.
