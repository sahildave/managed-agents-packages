---
name: workflow-guide
description: Change-report template and evidence rules for Competitor Change Tracker.
---

# Competitor change report

The agent instructions say what to do each run. This guide fixes what counts as a change and the report layout.

## What counts as a change
- A change needs two dated observations of the same URL: the snapshot in memory and this run's fetch. Without a snapshot, record a baseline and call it a baseline, never "new".
- Count: a price or plan change, a feature added to or removed from a pricing or feature page, a changelog entry dated inside the period, a new homepage headline or main call to action, an integration added or removed.
- Ignore: rotating testimonials, cookie banners, footer dates, reordered lists with the same items, an A/B variant seen once.
- A changelog or blog post is the competitor's own claim. Report it as "announced", not as shipped.
- Third-party coverage (news, Product Hunt, Reddit) is context. Link it, but never use it as the before or after evidence.

## Snapshot to save per URL
`competitors/<domain>/<yyyy-mm-dd>.md`: URL, fetch time in UTC, whether the fetch worked, headline, plan names and prices as shown, and the 5 to 10 lines that matter. Keep excerpts short; never store whole pages.

## Report layout
```text
# Competitor changes, week of <yyyy-mm-dd>

## Changes that matter
### <Competitor>: <one-line change>
- Page: <URL>
- Before (<snapshot date>): "<short excerpt>"
- After (<fetch date>): "<short excerpt>"
- What it means for you: <one or two sentences, marked as inference>

## Baselines recorded (nothing to compare yet)
- <Competitor>: <URL>

## Could not check
- <URL>: <blocked, login wall, timeout>

## Next actions
1. <action>
```
If nothing changed, say "No meaningful changes" in one line and list what was checked.
