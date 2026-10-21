---
name: workflow-guide
description: Link-suggestion template and evidence rules for Internal Link Advisor.
---

# Internal link suggestions

The agent instructions say what to do each run. This guide fixes which pages to read, what counts as a good link and the report layout.

## Reading the site
- Start from the sitemap the user gave (or `/sitemap.xml`, or the one named in `/robots.txt`). If none loads, use `site:<domain>` searches and say so.
- Read every target page first, then other pages up to the user's page limit. Count every fetch against the limit.
- Pick pages to read by how likely they are to mention a target topic: title and URL first, then `site:<domain> <topic>` searches.
- Keep a list of the pages you read. Every page you did not read goes in "Not read", so the user knows the report is partial.

## What counts as a good link
- The source sentence already talks about the target page's topic. Never suggest rewriting a paragraph to fit a link.
- Anchor text is three to six words copied from that sentence, describing the target. Never "click here" or "read more".
- At most three new links per source page, and never a second link to a target the page already links to.
- Never suggest a link from a page to itself or to a page that redirects or failed to load.

## Evidence rules
- Quote the source sentence exactly as fetched. Never suggest a link from a sentence you did not read.
- You have no crawler, analytics or Search Console. Never claim a page is "orphaned", gets traffic, or ranks; say "inbound links unknown beyond the pages read".
- If a target page has no good source sentence among the pages read, say so instead of forcing one.

## Report layout
```text
# Internal links for <domain>, <yyyy-mm-dd>

Read <n> of <page limit> pages. Targets: <URL>, <URL>

## Links to <target URL>
1. On <source URL>
   - Sentence: "<exact sentence>"
   - Anchor: "<anchor text>"

## Targets with no good source yet
- <target URL>: <what kind of page should link to it>

## Not read
- <URL or "the rest of the sitemap">: <page limit, blocked, failed>

## Next actions
1. <action>
```
Save every suggested link to memory with the date.
