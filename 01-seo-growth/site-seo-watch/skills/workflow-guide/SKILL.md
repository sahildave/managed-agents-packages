---
name: workflow-guide
description: Check commands, severity rules and change-report template for Site SEO Watch.
---

# Site SEO checks

The agent instructions say what to do each run. This guide gives the exact checks, how to grade them, and the report layout.

## Checks (GET and HEAD only, at most 50 URLs a run)
- robots.txt: `curl -sS -o robots.txt -w '%{http_code}' <site>/robots.txt`. Flag `Disallow: /` for all agents, and a missing `Sitemap:` line.
- Sitemap: fetch the sitemap URL from robots.txt (or `<site>/sitemap.xml`). Count `<loc>` entries. Check the status of the key pages and up to 20 other listed URLs.
- Status and redirects: `curl -sS -o /dev/null -L --max-redirs 5 -w '%{http_code} %{num_redirects} %{url_effective}' <url>`.
- Head tags: `curl -sSL <url>` and read `<title>`, `<meta name="description">`, `<link rel="canonical">`, `<meta name="robots">` and the `X-Robots-Tag` header (`curl -sSI`).
- Use a normal browser User-Agent with `-A`. If the site blocks curl (403 or a challenge page), say so and try web_fetch for that page.

## Severity
- High: a key page returns 4xx or 5xx; `noindex` on a key page; robots.txt blocks the whole site; a canonical points to another domain; the sitemap is gone.
- Medium: a redirect chain longer than one hop; a key page lost its title or meta description; sitemap URLs return 404; a canonical points to a redirecting URL.
- Low: a title longer than about 60 characters or a meta description longer than about 160; duplicate titles across key pages.

## Snapshot to save
`seo/<yyyy-mm-dd>.md`: per URL, the status, final URL, title, meta description, canonical and robots tag; plus the sitemap URL count. The next run diffs against this.

## Report layout
```text
# Site SEO watch, <site>, <yyyy-mm-dd>

## Changed since <last snapshot date>
### <High | Medium | Low>: <one-line problem>
- URL: <URL>
- Evidence: `<curl command>` returned `<output>`
- Last week: <value from snapshot>
- Fix: <one concrete step>

## Unchanged problems (still open)
- <problem>: first seen <date>

## Checked
- <n> URLs, robots.txt <status>, sitemap <status> with <n> URLs

## Next actions
1. <action>
```
On the first run there is no snapshot: report current problems under "Baseline" and save the snapshot.
