---
name: workflow-guide
description: Prospect types, pitch rules, memory layout and report template for Get Listed.
---

# Get listed

The agent instructions say what to do each run. This guide fixes what counts as a prospect, what you can claim, what to save and the report layout.

## Where to look
- For the category: `best <category>`, `best <category> <current year>`, `top <category> tools`, `<category> directory`.
- For each competitor: `<competitor> alternatives`, `<competitor> vs`, `<competitor> competitors`, and pages that list it next to others.
- Newsletters and podcasts only when a public issue or episode page names a competitor.

## What counts as a prospect
- A page you fetched on this run that names at least one of the user's competitors and does not name the user's product. A page you only saw in search results is not a prospect yet.
- Types: listicle ("best X"), alternatives page, directory, resource page, newsletter or podcast.
- Skip, with the reason: pay-to-play or sponsored-only placements, spam directories (hundreds of unrelated listings, no editorial text), pages not updated in two years, the user's domains to skip, and domains memory marks as drafted, sent, listed or declined.

## Evidence rules
- You have no backlink or SEO tool. Never state domain authority, domain rating, traffic or rankings. Say "authority unknown".
- Last updated: copy the date the page shows. If it shows none, write "no date shown"; never guess.
- Competitors named: list the ones you saw on the page.
- How to get on it: copy the route only if the page or its site shows it: a submit form, the author's contact page, a comment section. Otherwise write "none found". Never guess an email address or its pattern.
- A page that says placements are paid is marked "paid". Keep it in the skip list unless the user asked for paid options.
- If a page is blocked or needs a login, list it under "Could not check" instead of guessing.

## Pitch rules
- 60 to 90 words. Plain text, no flattery, no emoji.
- Name the exact page and where the product would fit on it.
- Use the user's pitch angle in one sentence about what the product does for that page's readers.
- Promise nothing the user did not offer: no link back, no payment.

## Effort to reward
Pick the 5 best by judgment and give the reason for each: a submit form is low effort; a page that names several competitors and was updated recently is high reward. Say it is a judgment.

## Memory layout
- `prospects/<domain>.md`: the page URL, type, the date you first suggested it, and the status the user reported (drafted, sent, listed, declined) with its date. Write a status only when the user reports it.
- `mentions/<yyyy-mm-dd>.md`: every page you fetched that names a competitor, with the competitors named. The next run diffs against this to mark pages as new.

## Report layout
```text
# Get listed, <product>, <yyyy-mm-dd>

New since <last snapshot date, or "first run">: <n> pages

## Listicles
### <site name>: <page title> [new]
- Page: <URL> (fetched <yyyy-mm-dd>, last updated <date or "no date shown">)
- Names: <competitor A>, <competitor B>
- How to get on it: <submit form URL, author contact page, comment, none found>
- Pitch draft (unsent):
  <pitch>

## Alternatives pages
## Directories
## Resource pages
## Newsletters and podcasts

## Skipped
- <URL>: <paid, spam directory, not updated since <date>, domain to skip, already <status>>

## Could not check
- <URL>: <blocked, login, gone>

## Best 5 by effort to reward
1. <URL>: <reason>

## Next actions
1. <action>
```
Leave out a type heading that has no pages. On a scheduled run with a snapshot, list only pages new since that snapshot; if there are none, say "No new pages since <date>" and still list open prospects the user has not reported on.
