---
name: workflow-guide
description: Channel rules, claim tracing and draft template for Content Repurposing Editor.
---

# Repurposed drafts

The agent instructions say what to do each run. This guide fixes how to trace claims, the channel limits and the draft layout.

## Claim rules
- Every claim, number, name and example in a draft must appear in the source text. Quote the source sentence it came from in the claim map.
- If the source does not say why something happened, do not add a reason.
- Do not add statistics, customer names, quotes, testimonials or results the source does not contain.
- Link the source with the public link from the inputs. If the link is `none`, leave links out and say so.
- If the source is too short to fill a channel, draft less and say why. Never pad.

## Channel rules
- X: 280 characters per post, and any link counts as 23. A thread is 3 to 6 posts; the first one stands on its own.
- Bluesky: 300 characters per post; count the full URL.
- LinkedIn: up to 3,000 characters. The first two lines show before "see more", so put the point there. Short paragraphs, no hashtag blocks.
- Newsletter: a heading, 100 to 250 words, and one link back to the source.
- Any other channel: say which length you chose and why.
- No "excited to announce", no engagement bait ("Agree?", "Thoughts?"), no hashtags unless the voice input asks for them.

## Draft layout
```text
# Repurposed drafts: <source title or first line>, <yyyy-mm-dd>

## <Channel> (<n> characters)
<draft>

Claim map:
- "<claim in the draft>" <- "<source sentence>"

## Check before you post
- <fact, number or name to confirm>

## Left out
- <point from the source>: <why: too long for the channel, unclear, needs a source>
```
Save the source title, link and date to memory so a later run can say it was already repurposed.
