---
name: workflow-guide
description: Source rules, channel limits and draft template for Post Repurposer.
---

# Repurposed posts

The agent instructions say what to do each run. This guide fixes how to read the source, the channel limits and the draft layout.

## Source rules
- Number the source's paragraphs (P1, P2, ...) once you have its text. Every draft names the paragraph it came from.
- Every claim, number, name and example in a draft must appear in that paragraph. If the source does not say why something happened, do not add a reason.
- Do not add statistics, customer names, quotes, testimonials or results the source does not contain.
- Link the source's public URL in each draft. For pasted text with no URL, leave the link out and say so.
- If web fetch fails or returns a login page, say which URL and when, and ask the user to paste the text. Never draft from the title alone.
- If a source is too short to fill a platform, draft less and say why. Never pad.
- Skip an angle that memory lists as already used for the same source. Say how many were skipped.

## Voice
- Follow the voice notes from the inputs. If the user linked past posts, read them for sentence length, tone and formatting; do not copy their topics or wording.
- Save the voice notes to memory, plus one line on what you took from any linked posts.

## Channel rules
- X: 280 characters per post, and any link counts as 23. A thread is 3 to 6 posts; the first one stands on its own.
- Bluesky: 300 characters per post; count the full URL.
- LinkedIn: up to 3,000 characters. The first two lines show before "see more", so put the point there. Short paragraphs, no hashtag blocks.
- Newsletter blurb: a heading, 100 to 250 words, and one link back to the source.
- Any other platform: say which length you chose and why.
- No "excited to announce", no engagement bait ("Agree?", "Thoughts?"), no hashtags unless the voice notes ask for them.

## Draft layout
```text
# Repurposed posts: <source title>, <yyyy-mm-dd>

Sources: <URL or "pasted text">, fetched <yyyy-mm-dd>

## <Platform>
### Draft 1 (<n> characters): <angle in a few words>
<draft>
Source: P<n>, "<short quote from that paragraph>"

### Draft 2 ...

## Thread (<n> posts, X limits)
1/ <text>  [P<n>]
2/ <text>  [P<n>]

## Newsletter blurb
<heading>
<text>
Source: P<n> to P<n>

## Suggested order
- <day of the week>: <platform, draft>, <one-line reason: e.g. the thread first, the LinkedIn post after it has replies>

## Check before you post
- <fact, number or name to confirm>

## Left out
- P<n>: <why: already used, too long for the platform, unclear, needs a source>
```
The suggested order is a sequence across one week, not a calendar with times. Save each source URL, the date and the angles used to memory.
