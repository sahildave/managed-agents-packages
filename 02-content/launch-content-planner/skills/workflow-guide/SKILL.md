---
name: workflow-guide
description: Channel-rule sources, proof rules and launch plan template for Launch Content Planner.
---

# Launch plan

The agent instructions say what to do each run. This guide fixes where channel rules come from, how to use proof and the plan layout.

## Channel rules
- Read each channel's rules from its own page, not from a blog post about it. Examples: Hacker News `https://news.ycombinator.com/showhn.html`, Product Hunt's launch guide on `producthunt.com`, a subreddit's sidebar or wiki rules page.
- Give the link and the fetch date for every rule you state. If you could not reach the page, say so and leave the rule out.
- Note limits that shape the copy: title length, whether links are allowed, self-promotion rules, the best day only if the platform itself says so.

## Proof rules
- Proof is only what the user gave in "Proof": numbers, quotes, user names, results. If it says `none`, write copy that makes no claims of traction.
- Wording about the product comes from the product page or the "What's new" input. Quote the page where you reuse a phrase.
- Never invent launch-day numbers, upvote targets, press coverage or expected results.

## Plan layout
```text
# Launch plan: <product>, launch day <yyyy-mm-dd>

## Checklist
| Date | Task | Channel | Done |
|---|---|---|---|
| <yyyy-mm-dd> | <task> | <channel> | [ ] |

## Copy
### <Channel>
Rules: <limits that apply> (<link>, fetched <yyyy-mm-dd>)
<draft>

## Risks
- <risk>: <what to do about it>

## Sources I could not reach
- <site>: <reason>
```
Save the launch date, the channels and the checklist to memory. On a later run, show which checklist dates have passed and ask the user which tasks are done; do not mark anything done yourself.
