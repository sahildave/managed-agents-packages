---
name: workflow-guide
description: Picking rules, rest periods, draft types and report template for Evergreen Posts.
---

# Evergreen posts

The agent instructions say what to do each run. This guide fixes how to rank past posts, when a post may come back, the draft types and the report layout.

## Ranking
- Rank only by the number the user named as "worked" (for example replies, reposts or link clicks), exactly as pasted. Break ties by the more recent post.
- Show each pick's numbers as pasted, with the date they were pasted. Never estimate a missing number, never compute an average or a benchmark the user did not give, and never say how a draft will perform.
- If fewer than ten posts carry the named number, say so and rank only those.

## When a post may come back
- Not before it is 30 days old.
- Not if the reuse log shows it was reused in the last 90 days.
- Not if it depends on a fact the user listed under "what changed", unless the draft states the new fact instead. Name the changed fact in the report.
- Not if it replies to, quotes or depends on someone else's post. Those make no sense on their own.

## Draft types
Pick one per original and say which:
- **New hook:** the same point with a new opening line and new wording. Never a copy with a word swapped.
- **Follow-up:** builds on the original and links to it ("A while ago I wrote ... Here is what I would add").
- **Short thread:** 3 to 5 posts that expand the original, the first one standing on its own.

## Post rules
- Every claim, number and name in a draft must appear in the original post or in the user's "what changed" list.
- X: 280 characters, and any link counts as 23. Bluesky: 300 characters; count the full URL. Draft for the platform the original was on.
- Follow the voice notes. No "excited to announce", no engagement bait ("Agree?", "Thoughts?"), no hashtags unless the voice notes ask for them.

## Report layout
```text
# Evergreen posts, <yyyy-mm-dd>

Posts considered: <n pasted this run> + <n from the archive>. Ranked by: <the user's number>.

## Pick 1: <original's point in a few words>
Original: <link>, posted <yyyy-mm-dd>, <number named>: <value as pasted> (pasted <yyyy-mm-dd>)
Why picked: <rank and rule passed, e.g. "2nd by replies, 140 days old, never reused">
Draft type: <new hook / follow-up / short thread>
<X or Bluesky> (<n>/<limit>):
<draft>

## Left out
- <link>: <reason: younger than 30 days, reused on <date>, depends on changed fact "<fact>", a reply to someone else>
```

## Memory
- Archive: each pasted post's text, link, post date, the numbers as pasted and the paste date. Add new posts; update numbers only with a new dated entry.
- Reuse log: for each pick, the original's link, the run date and the draft type.
