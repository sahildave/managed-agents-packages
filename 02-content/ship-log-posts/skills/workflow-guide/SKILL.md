---
name: workflow-guide
description: Post rules, character counting and draft template for Ship Log to Posts.
---

# Ship-log posts

The agent instructions say what to do each run. This guide fixes how to read the history, how to count characters and the draft layout.

## Reading the history
- `git clone --filter=blob:none --no-checkout <repo-url> repo` keeps the clone small. Then `git -C repo log --since='7 days ago' --date=short --pretty='%h %ad %s'` on the default branch.
- Merged pull requests: merge commits read `Merge pull request #<n> from ...`; squash merges end in `(#<n>)`. Link `https://github.com/<owner>/<repo>/pull/<n>`. Otherwise link the commit, `https://github.com/<owner>/<repo>/commit/<sha>`.
- Optional: `curl -sS 'https://api.github.com/repos/<owner>/<repo>/pulls?state=closed&per_page=30'` for pull request titles. It is unauthenticated and limited to 60 requests an hour; one call is enough.
- Skip dependency bumps, CI, formatting, lockfile and typo commits unless a user would notice the result.

## Post rules
- One change per post. Say what changed for the user, then link it.
- Never invent numbers, users, customers, revenue or quotes. If the commit does not say why, do not guess why.
- No "excited to announce", no hype words, no hashtags unless the user's voice notes ask for them.
- X: 280 characters, and any link counts as 23. Bluesky: 300 characters, and count the full URL.
- The thread: 3 to 5 posts, each within the X limit, the first one standing on its own.

## Draft layout
```text
# Ship log, <yyyy-mm-dd> to <yyyy-mm-dd>, <repo>

## Post 1: <change in a few words>
Source: <PR or commit URL>
X (<n>/280):
<text>
Bluesky (<n>/300):
<text>

## Thread (<n> posts)
1/ <text>
2/ <text>

## Left out
- <sha or #n>: <reason: internal, already drafted, not user-visible>
```
Save each drafted SHA or pull request number to memory with the date. If the week has nothing user-visible, say so and draft nothing.
