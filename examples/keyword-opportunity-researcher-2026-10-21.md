# Example run, 2026-10-21

One live session with this package at commit `48bef95`, applied without a deployment. The session was created through the API with a $2.00 budget and an empty memory store attached read_write, and the inputs below were sent as the first message. The inputs describe the publisher's own product.

- Model: claude-opus-5-5
- Measured list cost: **$1.17** (`session.usage`, budget $2.00)
- Active time: 115 seconds
- Stop reason: end of turn

## Inputs sent

```text
Your inputs
- Product: The Managed Agents catalog at coduo.co/managed-agents, ready-to-apply Claude Managed Agent packages for solo devs and indie hackers.
- Audience: Solo devs and indie hackers.
- Site URL: https://www.coduo.co
- Country and language: US English
- Topics you already cover: none
```

## Final agent message

The report is copied unedited. It describes the sites as they were on 2026-10-21.

I found six groups of search queries your buyers type that coduo.co doesn't answer yet. The best one to start with is "Claude Managed Agents templates", where several results are about a different product. Volumes are unknown because I had no keyword tool. My evidence is the titles and headings of pages that showed up in web search on 2026-10-21; I had no autocomplete or "People also ask" data.

**Starting point:** a search of `site:coduo.co` found guides for your other products (Shareling, Futari) but nothing about Managed Agents. Your catalog home lists seven packages and an install flow: Inspect the package, then run `ant apply`. So nothing was dropped as already covered.

## 1. Templates and examples (transactional): best opening
- **Queries:** claude managed agents templates; claude managed agents examples; ant apply agent examples
- **Who shows up:**
  - Vercel's repo, an internal knowledge agent built with Claude Managed Agents (CMA)
  - A Buildcamp guide noting that there are nine quickstart templates in total
  - Template sites for Claude Code, which is a different product: aitmpl.com and a Claude MPM agent library
- **Gap (my judgment):** there's no catalog of ready-to-apply packages, which is exactly what you have.
- **Suggested page:** a "Claude Managed Agents templates" landing page.
- **Difficulty:** low to medium.

## 2. Pricing and cost (transactional)
- **Queries:** claude managed agents pricing; cost per month; cost of an always-on agent
- **Who shows up:** at least seven dedicated pricing explainers (TrueFoundry, Agent37, Verdent, imisofts and others). They aim at teams and fleets; for example, TrueFoundry says this is for engineering and platform teams sizing out what a Claude Managed Agents deployment will actually cost.
- **Gap (my judgment):** nobody prices the small weekly or on-demand runs a solo dev actually does.
- **Suggested page:** a guide on what a Managed Agent costs a solo dev, using costs you measure from real package runs.
- **Difficulty:** high for the main term, medium for longer variants.
- **Watch out:** one ranking page claims the first 50 session-hours per day across all your sessions are free. No other source I saw says this, so check Anthropic's pricing page before repeating it.

## 3. Comparisons (commercial)
- **Queries:** managed agents vs agent sdk; claude code routines vs managed agents
- **Who shows up:** many pages compare against the Agent SDK (HatchWorks, Apidog, WaveSpeed, TrueFoundry, plus the official docs). For Routines, Developers Digest explains that Routines are subscription-side… Managed Agents scheduled deployments are API-side.
- **Suggested page:** "Routines vs Managed Agents for solo devs".
- **Difficulty:** high for the SDK comparison, medium for the Routines angle.

## 4. Setup how-to (informational)
- **Queries:** ant apply tutorial; scheduled deployment cron; memory store
- **Who shows up:** Anthropic's own docs come first, then tutorials from Nerd Level Tech, Julian Goldie and Get Claude Skills.
- **Gap (my judgment):** all of them teach you to write your own agent. None shows how to install, review and schedule someone else's package.
- **Suggested page:** a guide to installing a prebuilt package with ant apply.
- **Difficulty:** medium to high, because the official docs hold the top spots.

## 5. Build in public from commits (transactional, tool)
- **Queries:** turn git commits into tweets; build in public post generator
- **Who shows up:** a Show HN thread, a few small SaaS tools (CommitLore, buildinpublic.now) and an open-source repo. Another tool, TweetGit, shut down; its founder wrote too late, I have found out that other indie builders are not a good target market.
- **Gap (my judgment):** a forum thread and a repo rank, so the results look beatable.
- **Suggested page:** expand the Ship Log to Posts package page to target these queries.
- **Difficulty:** medium.

## 6. Competitor change monitoring (transactional, tool)
- **Queries:** ai agent to track competitor pricing changes; automate competitor analysis
- **Who shows up:** funded tools (Competely, Gumloop, Browse AI) and an article from Parallel.
- **Suggested page:** expand the Competitor Change Tracker page, with a sample weekly report.
- **Difficulty:** high for the general term, medium for the solo-founder angle.

## Next actions
1. Build the "Claude Managed Agents templates" landing page (group 1).
2. Write the guide to installing a package with ant apply (group 4), using your own install flow.
3. Add explanatory copy and sample output to the Ship Log to Posts and Competitor Change Tracker pages (groups 5 and 6).

**Assumptions:**
- The order results appeared in this search tool stands in for Google rankings; it isn't rank tracking.
- Difficulty is my judgment from the kinds of sites that rank.
- When I asked for www.coduo.co/managed-agents, the fetch tool returned the coduo.co/managed-agents page (2026-10-21); its canonical URL is the www version.

**Memory (first run, store was empty):** I created `profile.md` (your inputs, dated 2026-10-21, plus what I saw on the site), `suggested-queries.md` (every suggested query, dated) and `snapshots/2026-10-21.md` (who ranked for each group, the pricing conflict, and my guesses marked as unverified). The next run will skip these queries and compare against this snapshot.

Files are in /mnt/session/outputs:
- keyword-opportunities-2026-10-21.md
