---
name: workflow-guide
description: Topic-gap template and evidence rules for Competitor SEO Gap Scout.
---

# Competitor topic gaps

The agent instructions say what to do each run. This guide fixes how to read coverage, what you can claim and the report layout.

## Reading coverage
- Sources, in order: `/sitemap.xml` (or the sitemap named in `/robots.txt`), the blog, docs or guides index, the main navigation, then `site:<domain> <topic>` searches.
- A topic is a subject a reader would search for, such as "invoice late fees" or "Stripe vs Paddle". Group pages that answer the same question under one topic.
- Name the competitor pages you saw for each topic. Two or three URLs are enough.
- If a competitor blocks fetching or has no sitemap, say which sources you could read and treat its list as partial.
- Split the work by competitor when there are three or more, one strand each, then merge the topic lists in the primary thread.

## Evidence rules
- You have no keyword or rank tool. Never state search volume, keyword difficulty, traffic or rankings. Say "volume unknown".
- "Your site covers it" needs one of your URLs. "Gap" means you searched your sitemap and `site:` and found none; say "not found", never "you have nothing on this" when a source was blocked.
- Priority is a judgment. Base it on how many competitors cover the topic and how close it is to what the user sells, and say which.
- Skip topics memory says were already suggested unless a competitor added a page since.

## Report layout
```text
# Competitor topic gaps, <yyyy-mm-dd>

Read: <competitor>: <sources read>; <competitor>: <sources read>

| Topic | Covered by | Your site | Priority |
| --- | --- | --- | --- |
| <topic> | <competitor> (<URL>), <competitor> (<URL>) | not found | high: <reason> |

## Topics you cover that they do not
- <topic>: <your URL>

## Partial coverage
- <competitor>: <what could not be read and why>

## Next actions
1. <action>
```
Return five to fifteen gap topics, highest priority first. Save every gap topic to memory with the date.
