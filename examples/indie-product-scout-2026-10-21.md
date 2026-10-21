# Example run, 2026-10-21

One live session with this package at commit `48bef95`, applied without a deployment. The session was created through the API with a $2.00 budget and an empty memory store attached read_write, and the inputs below were sent as the first message. The inputs describe the publisher's own product.

- Model: claude-opus-5-5
- Measured list cost: **$1.89** (`session.usage`, budget $2.00)
- Active time: 162 seconds
- Stop reason: end of turn

## Inputs sent

```text
Your inputs
- Niche: AI agents for solo devs, launched in the last 7 days
- Your product URL: https://www.coduo.co/managed-agents
- Leave out: none
```

## Final agent message

The report is copied unedited. It describes the sites as they were on 2026-10-21.

I found five launches from the past week (Oct 14–21) that are worth a look. Two of them, AskDoozy and Backdrop, pitch something close to your package catalog. Most of the other new agent launches this week manage coding agents, so they sit next to you rather than against you. Product Hunt was the only source I covered well. I didn't get a dated list of this week's Show HN posts, and I didn't search Indie Hackers or Reddit.

On Product Hunt I couldn't open the daily launch pages directly. Dates marked "~" come from dated Product Hunt digests posted on GitHub or from "X days ago" timestamps, not from a date on the launch post. All pages were fetched 2026-10-21.

## Worth a look

**AskDoozy** (Product Hunt, launching today, 2026-10-21): the closest overlap
- Site: askdoozy.com · Launch post: producthunt.com/products/askdoozy
- What it says: "Doozy is the coworker in your Slack." It runs scheduled jobs, keeps notes in Markdown, and uses procedures that you write yourself.
- Pricing: one price per workspace. 14 days free, no card. Starter is $20/month; the plans go up to $999.
- Usage the founder published: 13 people at Spur have used it daily since August, about 2,000 requests a month.
- Versus you (my reading): it has the same recurring-work idea and the same safety language (sandbox, an action log). But users write the procedures themselves inside a hosted Slack bot. You offer packages that are already built and tested, and they run in the buyer's own workspace. Its pricing page compares itself to Viktor, Lindy and OpenClaw, so those are the prices buyers will see next to yours.

**Backdrop** (Product Hunt, ~Oct 16, its second launch)
- Site: backdropagent.com · Launch post: producthunt.com/products/backdrop
- What it says: "Build the AI team your work needs." It is backed by Y Combinator.
- Pricing: one free AI "coworker", then $100, $250 or $550 per coworker per month.
- Versus you (my reading): it sells to teams and charges per coworker. Its research and marketing use cases overlap your SEO, research and content packages, but it costs much more and has no "inspect before you install" step.

**Harness by Autonomous** (~Oct 17)
- It calls itself "the open-source command center for coding agents". The app is free; desk hardware for it costs $149–$299.
- Versus you: adjacent. It manages coding agents people already run; it doesn't supply agents for business tasks.

**Tetriz Harness** (~Oct 17)
- An open-source tool that finds what's broken in a team's coding-agent setup and pushes approved fixes out to the team.
- Versus you: it also bundles agent setups into something you hand out. But it's for engineering teams, not one-person businesses.

**BOSS Console** (~Oct 16, exact date not shown)
- It calls itself "a tiny OS for your always-on agents", is open source and free.
- Its site wouldn't load beyond that one-line description. It's a place for agents to run, so it could be a channel for your packages rather than a rival.

**Lower relevance:** Harness², Composio Instant, BAND for Developers, Nimbalyst Wiki, Mouse-1, ilha, Agent Pets, Beam.win and Shrine. These are coding-agent tools or agent plumbing, and I didn't open their sites.

## Next actions
1. **Add one line to your hero copy** contrasting pre-built, tested packages with "skills you write yourself" and per-seat pricing. AskDoozy and Backdrop both leave the writing of procedures to the user.
2. **Publish a comparison row or page,** the way AskDoozy does. Show what a buyer can inspect before installing and the cost per run, next to AskDoozy and Backdrop.
3. **Approach BOSS Console and Harness by Autonomous** about listing your packages as installable add-ons. I've only flagged this; I haven't contacted anyone.

## Assumptions
- I read "solo devs" broadly to include solo founders and operators, because your catalog covers SEO, research and content rather than coding.
- Your catalog page shows no pricing, so the price comparisons only show their side.

## Memory updated
This was the first run, so there was nothing earlier to compare against. In `/mnt/memory/indie-product-scout-memory/` I created:
- `profile.md`: your inputs (dated 2026-10-21), a summary of your product from your page, and a current summary.
- `seen-products.md`: every product above with its URLs and launch date, so the next run skips them.
- `snapshots.md`: dated notes for this run, keeping what I saw on the pages separate from my guesses, plus the sources I couldn't reach.

Files are in `/mnt/session/outputs`:
- indie-launch-brief-2026-10-21.md
