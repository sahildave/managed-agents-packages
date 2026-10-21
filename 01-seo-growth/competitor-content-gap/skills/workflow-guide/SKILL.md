---
name: workflow-guide
description: Sitemap commands, intent order, memory layout and gap report template for Competitor Content Gap.
---

# Competitor content gaps

The agent instructions say what to do each run. This guide gives the exact commands, how to classify and rank pages, what to save and the report layout.

## Reading a sitemap (GET and HEAD only)
- robots.txt: `curl -sS -A '<browser User-Agent>' -o robots.txt -w '%{http_code}' <site>/robots.txt`. Take every `Sitemap:` line.
- Sitemap: fetch each sitemap URL from robots.txt, or `<site>/sitemap.xml` and `<site>/sitemap_index.xml`. A sitemap index lists child sitemaps; fetch each child. Gzipped sitemaps: `curl -sS --compressed`, or pipe a `.xml.gz` through `gunzip`.
- Count `<loc>` entries. Keep the URL list for the snapshot.
- If there is no sitemap or the site blocks curl (403 or a challenge page), say so, read the blog, docs or guides index and the main navigation with web_fetch, and mark that competitor's inventory as partial.

## Page types
Classify by URL path first, then by title when the path is unclear:
- comparison: `/vs/`, `-vs-`, `/compare`
- alternatives: `/alternatives`, `-alternative`
- use case: `/use-cases/`, `/solutions/`, `/for-<audience>`
- integration: `/integrations/`, `/apps/`
- docs: `/docs/`, `/help/`, `/guides/` that explain the product
- blog: `/blog/`, `/articles/`, `/resources/`
- other: everything else (legal, careers, pricing, home). Count it, but leave it out of the gap matrix.

## Topic clusters and buyer intent
- A topic cluster is a subject a buyer would search for, such as "Stripe vs Paddle" or "invoicing for photographers". Group pages that answer the same question.
- Intent order, highest first: comparison and alternatives; use case and integration; educational (blog and docs).
- "You cover it" needs one of the user's URLs. "Gap" means the user's sitemap and a `site:` search found none; when the user's sitemap was partial, say "not found" and name what you could not read.

## Evidence rules
- You have no keyword or rank tool. Never state search volume, keyword difficulty, traffic or rankings. Say "volume unknown".
- Name two or three competitor URLs per gap.
- Rank is a judgment from intent and from how many competitors cover the topic. Say which.
- "New since <date>" needs a snapshot from that date. On the first run there is no baseline: say so.

## Snapshot to save
`sitemaps/<domain>/<yyyy-mm-dd>.md`: the sitemap URLs read, the page count by type, and the full URL list. The next run diffs against the latest one for each domain.

## Report layout
```text
# Competitor content gap, <your site>, <yyyy-mm-dd>

## Inventory
| Site | Sitemap | blog | comparison | alternatives | use case | integration | docs | other |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <domain> | <read, partial: reason> | <n> | <n> | <n> | <n> | <n> | <n> | <n> |

## Gap matrix
| Topic cluster | Intent | <competitor A> | <competitor B> | You |
| --- | --- | --- | --- | --- |
| <topic> | comparison | yes | no | not found |

## Top 5 gaps
### 1. <topic> (<intent>)
- Covered by: <competitor> (<URL>), <competitor> (<URL>)
- Suggested page: <comparison, alternatives, use case, integration, guide>
- Why it ranks here: <intent and coverage>

## New competitor pages since <last snapshot date>
- <competitor>: <URL> (<type>)

## Topics you cover that they do not
- <topic>: <your URL>

## Next actions
1. <action>
```
Close the next actions with: "Next, run Keyword Opportunity Researcher on the top gap to see the queries buyers type for it."
