---
name: workflow-guide
description: Post checks, curl commands, refresh log and report template for SEO Content Refresh.
---

# Post refresh list

The agent instructions say what to do each run. This guide gives the exact checks, what you can claim, what to save and the report layout.

## Picking posts
- If the user gave post URLs, check those, at most 15.
- If not, read the sitemap (`curl -sS -A '<browser User-Agent>' <sitemap URL>`, or the `Sitemap:` line in `<site>/robots.txt`). Keep blog or article URLs. Take up to 10 with the oldest `<lastmod>`; if the sitemap has no `<lastmod>`, take 10 spread across the list and say so.
- Skip posts the refresh log checked with no open issue, unless the user named them.

## Checks per post
1. Stale facts: prices, plan limits, version numbers, release dates, "as of" lines, statistics with a year, discontinued tools, product steps (menu names, settings, screens). Quote each one.
2. Outbound links: every link in the body to another domain. Check each with `curl -sS -o /dev/null -L --max-redirs 5 -A '<browser User-Agent>' -w '%{http_code} %{url_effective}' <url>`.
3. Questions it does not answer: search the target query (or, if none was given, the post's title as a reader would type it) and read the top 3 results. List what they cover that the post does not.
4. Title and meta: the post's `<title>` and `<meta name="description">` beside those of the top 3 results.
5. The post's own date: a "last updated" line or a year in the title.

Internal links are not checked here. Internal Link Advisor finds them; say so if the user asks.

## Evidence rules
- A fact is stale only when a current primary source says otherwise: the vendor's pricing page, docs, changelog or the original study. Quote both sides and give the source URL and fetch date. If you found no current source, write "could not confirm".
- A link fails when curl returns 4xx or 5xx, or cannot connect. 401, 403 or a challenge page is "could not check". A link that now lands on an unrelated page (for example a homepage) is "redirected".
- You have no analytics or Search Console. Never claim a post lost traffic or rankings, or that a fix will win any back. Label every backlog order as a hypothesis.
- Effort: small (a word or number), medium (a paragraph or a new section), large (a rewrite).

## Refresh log to save
`refresh/<post-slug>.md`: the post URL; each dated check with the issues found; and each issue the user reports as fixed, with the date. On a rerun, re-check only the issues marked fixed, plus posts not in the log.

## Report layout
```text
# Refresh list, <site>, <yyyy-mm-dd>

## <post title> (<URL>)
Last updated: <date from the page, the sitemap, or "unknown">
Target query: <query, or "title used">

### Stale facts
1. <fact in one line> (<small, medium, large>)
   - Now says: "<quote>"
   - Evidence: <source URL>, fetched <yyyy-mm-dd>: "<quote>"
   - Change to: <suggested text>

### Links
- <link>: <status code, redirected to URL, could not check>

### Questions it does not answer
- <question>: covered by <result URL>

### Title and meta
- Yours: "<title>" / "<meta>"
- Top results: "<title>" (<URL>); ...
- Suggestion: <one line>

## Could not confirm
- <claim>: <why>

## Refresh backlog (hypotheses, no analytics)
1. <post>: <fix> (<effort>, <why it may matter>)

## Next actions
1. <action>
```
Save each post's refresh log to memory with the date.
