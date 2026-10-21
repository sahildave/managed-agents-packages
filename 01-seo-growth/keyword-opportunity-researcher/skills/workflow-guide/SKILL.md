---
name: workflow-guide
description: Keyword-cluster template and evidence rules for Keyword Opportunity Researcher.
---

# Keyword clusters

The agent instructions say what to do each run. This guide fixes what you can and cannot claim, and the report layout.

## Evidence rules
- You have no keyword tool. Never state a search volume, keyword difficulty score or CPC. Say "volume unknown".
- Evidence a query is real: it appears in search suggestions, "People also ask", forum titles or the headings of ranking pages. Name which.
- Difficulty is a judgment from the ranking pages: big brands and dedicated tools ranking means hard; forum threads and thin pages ranking means a gap. Say which pages you saw.
- Intent: informational (how/what/why), commercial (best/vs/alternatives/reviews), transactional (pricing/buy/template/tool). One intent per cluster.
- Drop a query when the user's site already has a page that answers it (check with web_search `site:<domain> <query>`), or when memory lists it.

## Report layout
```text
# Keyword opportunities, <yyyy-mm-dd>

## Cluster: <name> (<intent>)
- Queries: <query 1>; <query 2>; <query 3>
- Evidence they are searched: <source per query>
- Who ranks now: <URL> (<type: tool, blog, forum>), <URL>
- Gap: <why a new page could compete, marked as judgment>
- Suggested page: <guide, comparison, template, landing page>
- Difficulty: <low, medium, high> because <reason>

## Already covered or already suggested
- <query>: <your URL or memory date>

## Next actions
1. <action>
```
Return three to six clusters. Save every suggested query to memory with the date.
