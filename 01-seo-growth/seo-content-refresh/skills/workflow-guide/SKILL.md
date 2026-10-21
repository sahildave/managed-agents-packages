---
name: workflow-guide
description: Refresh-list template and evidence rules for SEO Content Refresh Planner.
---

# Article refresh list

The agent instructions say what to do each run. This guide fixes what to check, what you can claim and the report layout.

## What to check in each article
1. Dated facts: prices, plan limits, version numbers, release dates, "as of" statements, statistics with a year.
2. Product steps: menu names, settings and screens the article tells the reader to use.
3. Outbound links: every link in the body.
4. Missing questions: what the pages ranking now for the article's main question cover that the article does not.
5. The article's own date: a "last updated" line or a year in the title.

## Evidence rules
- A fact is out of date only when a current primary source says otherwise: the vendor's pricing page, docs, changelog or the original study. Quote both sides and give the source URL and fetch date.
- If you could not find a current source, say "could not confirm" instead of calling the fact wrong.
- A link is dead only when the fetch fails or returns an error page. A blocked fetch or a login wall is "could not check". A link that now lands on an unrelated page (for example a homepage) is "redirected".
- You have no analytics or Search Console. Never claim the article lost traffic or rankings, or that a fix will win any back.
- Effort: small (a word or number), medium (a paragraph or a new section), large (a rewrite). Base it on the change, not a guess at hours.

## Report layout
```text
# Refresh list, <yyyy-mm-dd>

## <article title> (<URL>)
Last updated: <date from the page, the user, or "unknown">

1. <fix in one line> (<small, medium, large>)
   - Now says: "<quote>"
   - Evidence: <source URL>, fetched <yyyy-mm-dd>: "<quote>"
   - Change to: <suggested text or section>

### Links
- <link>: <dead, redirected to URL, could not check>

### Questions it does not answer
- <question>: covered by <ranking URL>

## Could not confirm
- <claim>: <why>

## Next actions
1. <action>
```
Rank fixes within each article by how wrong or incomplete the article is today, then by effort. Save each article's fix list to memory with the date.
