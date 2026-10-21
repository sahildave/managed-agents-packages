---
name: workflow-guide
description: Channel shortlist, channel-rule sources, proof rules and launch kit template for Launch Kit.
---

# Launch kit

The agent instructions say what to do each run. This guide fixes how to pick channels, where channel rules come from, how to use proof and the kit layout.

## Channel shortlist
- If the user wrote "suggest", consider Product Hunt, Show HN, Indie Hackers, three to five named subreddits where the audience gathers, directories that list products like this one, and newsletters that take submissions. Otherwise check the channels the user named, and add others only as suggestions.
- Give each channel a fit of high, medium or low, with one line on why: audience match, whether the channel accepts this kind of launch, and what its rules demand.
- Leave out a channel whose rules forbid this launch, and say why.

## Channel rules
- Read each channel's rules from its own page, not from a blog post about it. Examples: Hacker News `https://news.ycombinator.com/showhn.html`, Product Hunt's launch guide on `producthunt.com`, a subreddit's sidebar or wiki rules page, a directory's submission page.
- Give the link and the fetch date for every rule you state. If you could not reach the page, say so and leave the rule out.
- Note limits that shape the copy: title length, whether links are allowed, self-promotion rules, the best day only if the platform itself says so.
- On a later run, fetch the rules again and say which ones changed since the saved fetch date.

## Assets per channel
- Product Hunt: tagline (60 characters at most), description, maker's first comment.
- Show HN: title in the `Show HN:` format and the first comment.
- Reddit: one post per subreddit, written to that subreddit's rules.
- X or Bluesky: one thread.
- Email to your list, if you have one.
- Directories and newsletters: the short description and fields each submission page asks for.

Draft only for channels on the shortlist.

## Proof rules
- Proof is only what the user gave in "Proof": numbers, quotes, user names, a demo video, pricing. If it says `none`, write copy that makes no claims of traction.
- Wording about the product comes from the product page or the "What's new" input. Quote the page where you reuse a phrase.
- Never invent launch-day numbers, upvote targets, press coverage or expected results.

## Checklist
- Dates run from T-7 to T+3, computed from the launch date. If T-7 has passed, start from today.
- One task per row, tied to a channel where it has one.

## Kit layout
```text
# Launch kit: <product>, launch day <yyyy-mm-dd>

## Channels
| Channel | Fit | Why | Rules (link, fetched) |
|---|---|---|---|
| <channel> | high/medium/low | <one line> | <limits> (<link>, <yyyy-mm-dd>) |

## Assets
### <Channel>
<draft>

## Checklist
| Date | Day | Task | Channel | Done |
|---|---|---|---|---|
| <yyyy-mm-dd> | T-7 | <task> | <channel> | [ ] |

## Risks
- <risk, e.g. a draft that could break a rule, no demo video, a clashing launch that week>: <what to do about it>

## Sources I could not reach
- <site>: <reason>
```

## Memory
- Save the launch profile, the shortlist, each channel's rules with the fetch date, and the checklist.
- On a later run, show which checklist dates have passed and ask the user which tasks are done; do not mark anything done yourself. Record only the status the user reports.
- After the launch, if the user says which channels worked, append it in their words to a dated launch log. Read that log at the start of the next launch.
