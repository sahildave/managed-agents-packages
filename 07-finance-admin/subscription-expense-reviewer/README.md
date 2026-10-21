# Subscription Expense Reviewer — Claude Managed Agent native package

Paste the charges from a statement or expense export. You get every recurring charge in one table with its monthly and yearly cost, duplicates and price rises flagged, the tools you pay for but no longer use, each tool's current public price with any cheaper plan, the renewals due in the next 45 days, and a short list of charges to check or cancel yourself. It never cancels anything and never sees your bank; it works from the list you paste plus vendors' public pricing pages, and remembers past runs so it can spot price rises and upcoming renewals.

## Resources
- `agents/subscription-expense-reviewer.md`: the agent's instructions, tools and multiagent settings.
- `skills/workflow-guide/SKILL.md`: the recurrence rules, cost arithmetic and report template for this task.
- `environments/cloud.yaml`: Cloud sandbox with open web access for web fetch. The shell and web search are disabled in the agent, and nothing secret is stored here.
- `memory_stores/history.yaml`: private memory for dated snapshots. It does **not** attach itself to interactive sessions.

## Network and tools
- Network: `unrestricted` (open web access, minus Anthropic's safety blocklist), so web fetch can reach each vendor's public pricing page. With `limited` networking and no `allowed_hosts`, web fetch returns nothing.
- Tools: web fetch and the file tools. The shell (`bash`) and web search are disabled in `agents/subscription-expense-reviewer.md`, so the agent cannot run commands.
- Memory is the main value. With the store attached, each run saves merchant, amount, interval, renewal date and your keep or cancel decision, so the next run can flag a price rise, a charge that came back or a renewal coming up. Without it, each run sees only that session's paste.
- It never cancels, pauses or changes a subscription. You do that in each merchant's billing settings.
- Risk: the network is open, and anything in the sandbox can leave over it. Before you paste, remove card numbers, bank account numbers, sort codes, IBANs, login details and addresses. Keep only date, merchant, amount and currency. The agent does not store those details in memory.

## First-run setup
1. This package has no schedule. Run it when you review your spending, for example once a month. A session you start in Console has no cost cap. To cap a run, create the session through the API with a `max_list_cost` budget ([budgets](https://platform.claude.com/docs/en/managed-agents/budgets)); a budget cannot be added to a session later. No run cost has been measured yet.
2. Run `ant apply --dry-run .` and inspect the resource plan.
3. Install the agent, environment, skill and memory store:

   `ant apply agents/subscription-expense-reviewer.md environments/cloud.yaml memory_stores/history.yaml skills/workflow-guide`

   `ant apply .` installs the same four resources, because there is no deployment.
4. Create a session in Console with this agent and environment. Attach the memory store with `read_write` access if you want it to compare against past reviews.
5. Send this as your first message, with every `<placeholder>` replaced. If one is left, you get a setup checklist instead of a review:

   Your inputs
   - Charges: <paste rows of date, merchant, amount, currency; two or more months if you can, with card and account numbers removed>
   - Renewal dates: <annual plans and domains with the date each renews, or "none">
   - Subscription budget: <e.g. 200 USD a month, or "none">
   - Tools still in use: <the tools you know you use, or "not sure">

## Verification
1. Ask the agent which tools and memory mounts are actually available.
2. Run once with placeholders left in. You should get only a setup checklist.
3. Run with real inputs and check that each total lists the rows it came from, that nothing is called recurring on a single charge, and that every price cites the pricing page URL and fetch date.
4. In a session with the memory store attached, ask it to write a dated note to memory. Start a second session with the store attached and check it can read that note.

## Status
Generated files passed local YAML/frontmatter and reference checks. **Not live-tested against your Anthropic workspace.** No run cost has been measured yet.
