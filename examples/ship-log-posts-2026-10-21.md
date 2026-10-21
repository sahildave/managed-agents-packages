# Example run, 2026-10-21

One live session with this package at commit `48bef95`, applied without a deployment. The session was created through the API with a $1.00 budget and an empty memory store attached read_write, and the inputs below were sent as the first message. The inputs describe the publisher's own product.

- Model: claude-opus-5-5
- Measured list cost: **$0.25** (`session.usage`, budget $1.00)
- Active time: 77 seconds
- Stop reason: end of turn

## Inputs sent

```text
Your inputs
- Repository: https://github.com/sahildave/managed-agents-packages
- Product name: Managed Agents
- Voice: plain, a bit dry, no emoji, no hype words
```

## Final agent message

The report is copied unedited. It describes the sites as they were on 2026-10-21.

I've written three posts for both X and Bluesky and a four-post thread, covering 14 to 21 October 2026 in sahildave/managed-agents-packages. There were four commits in that window, all on 21 October and all made straight to the main branch, so every draft links to a commit rather than a pull request. I checked that all three commit links open. Character counts follow the platform rules: on X a link counts as 23 characters, and on Bluesky the full link counts.

## Post 1: First release, seven packages
Source: https://github.com/sahildave/managed-agents-packages/commit/0de37cf

**X (272/280)**
Put up Managed Agents: seven agent packages for solo founders, each a folder you install with the ant CLI. SEO checks, landing page review, content ideas, competitor tracking, launch scouting, and turning commits into posts. They draft. You decide.
https://github.com/sahildave/managed-agents-packages/commit/0de37cf

**Bluesky (295/300)**
Put up Managed Agents: seven agent packages for solo founders, each a folder you install with the ant CLI. SEO checks, page review, content ideas, competitor tracking, launch scouting, commits into posts. Nothing posts for you.
https://github.com/sahildave/managed-agents-packages/commit/0de37cf

## Post 2: Five packages now on demand
Source: https://github.com/sahildave/managed-agents-packages/commit/83cf946

**X (239/280)**
Five of the seven Managed Agents packages now run on demand: install, then send your inputs as the first message. Only the two watchers keep a weekly schedule, because comparing against last week is their whole job.
https://github.com/sahildave/managed-agents-packages/commit/83cf946

**Bluesky (290/300)**
Five of the seven Managed Agents packages now run on demand: install, then send your inputs as the first message. The SEO watcher and competitor tracker keep a weekly schedule, since comparing against last week is the job.
https://github.com/sahildave/managed-agents-packages/commit/83cf946

## Post 3: Console sessions have no cost cap
Source: https://github.com/sahildave/managed-agents-packages/commit/48bef95

**X (256/280)**
Fixed five READMEs that implied you could set a budget in Console. You can't. A Console session has no cost cap. To cap a run, create the session through the API with a budget, and do it at creation, because it can't be added later.
https://github.com/sahildave/managed-agents-packages/commit/48bef95

**Bluesky (286/300)**
Fixed five READMEs that implied you could set a budget in Console. You can't. A Console session has no cost cap. To cap a run, create the session through the API with a budget, set at creation. It can't be added later.
https://github.com/sahildave/managed-agents-packages/commit/48bef95

## Thread (4 posts, each within the X limit)
1/ Shipped Managed Agents this week: seven agent packages for solo founders, installed with the ant CLI. A few notes on what changed after the first commit.
https://github.com/sahildave/managed-agents-packages/commit/0de37cf
2/ Most of them don't need a schedule. Five now run on demand: install, send your inputs as the first message, read the drafts.
https://github.com/sahildave/managed-agents-packages/commit/83cf946
3/ Two keep a weekly schedule: the SEO watcher and the competitor change tracker. Comparing against last week is what they're for, so running them on demand would miss the point.
4/ Also corrected the READMEs on cost. A Console session has no cost cap. If you want one, set a budget through the API when you create the session. It can't be added afterwards.
https://github.com/sahildave/managed-agents-packages/commit/48bef95

## Left out
- **9f25a78:** a one-line wording change inside the content-idea-hunter instructions ("this week" became "last seven days"). A reader wouldn't notice it.

## Next actions
1. Check the "Five" count in Post 2 before posting. The commit took the schedule off four packages, and landing-page-critic already ran on demand, which makes five. But the README you published first still lists six packages as weekly, so make sure the current README agrees.
2. Choose between Post 1 and thread post 1 as your launch post. They cover the same commit, so posting both on the same day would repeat yourself.
3. Think about linking to https://www.coduo.co/managed-agents (from the README) instead of the commit in Post 1. A commit page is a weak landing spot for people who haven't seen the project. The Bluesky version has 5 characters spare, so a different link may need a shorter sentence.

## Assumptions
- **Commit links instead of PR links:** the GitHub request for pull request titles was refused because the anonymous request limit was used up. None of the commit messages mention a pull request either.
- **Short links:** I used 7-character commit IDs to save space on Bluesky.
- **"Put up" and "Shipped":** these are based only on the commit dates. I don't know whether you've announced anything elsewhere yet.
- **No "why" added:** I didn't give reasons the commits don't state, except in Post 2 and thread post 3, where the commit message itself says it.

## Memory
This was the first run, and memory was empty. I created two files in the Ship Log to Posts store:
- **`profile.md`:** your inputs, dated 2026-10-21, plus a note that the anonymous GitHub request failed here.
- **`snapshots.md`:** a dated record of what this run drafted (0de37cf, 83cf946, 48bef95) and what it skipped (9f25a78), so next week's run won't repeat them.

Files are in /mnt/session/outputs:
- ship-log-2026-10-21.md
