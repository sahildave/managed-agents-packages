---
name: workflow-guide
description: Recurrence rules, cost arithmetic, pricing and renewal rules and report template for Subscription Expense Reviewer.
---

# Subscription expense review

The agent instructions say what to do each run. This guide fixes when a charge counts as recurring, how to total costs, how to read pricing pages and renewal dates, what to keep in memory and the report layout.

## Reading the paste
- Accept any row shape that gives a date, a merchant and an amount. Note the currency on each row; if it is missing, ask rather than assume.
- Merchant names on statements vary (`ACME*PRO 4821`, `Acme Pro`). Group them only when the name clearly matches; list uncertain matches under "Check".
- Drop any card number, account number, sort code, IBAN, address or reference that looks personal before you quote a row.

## When a charge is recurring
- Monthly: the same merchant on roughly the same day in two or more months.
- Yearly: only if the user says so, or memory has the charge from about a year earlier.
- One charge with no repeat in the rows is "one-off or unknown", not recurring.

## Flags
- Duplicate: two recurring charges for the same merchant in the same period, or two tools the user lists for the same job.
- Price rise: a later amount above an earlier one for the same merchant, in the rows or against the last snapshot. Show both amounts and dates.
- Unused: a recurring merchant missing from the "still in use" list. If that list is "not sure", flag nothing as unused and ask instead.
- Over budget: the monthly total above the budget the user gave.

## Cost arithmetic
- Monthly cost: the latest amount of a monthly charge; a yearly charge divided by 12. Yearly cost: monthly times 12.
- Total per currency. Never convert currencies; you have no exchange rate.
- Show the rows each total came from, so the user can check the sum.

## Pricing pages
- Fetch the vendor's own public pricing page for each recurring tool. Cite the URL and fetch date next to every price you quote.
- Name the plan only when the charged amount matches a listed price; otherwise say "plan not matched".
- A cheaper fit is a lower plan or an annual discount shown on that page. You cannot see the user's usage or seats, so label each one "check it covers what you use".
- If the page is blocked, behind a login or shows no prices, say so and quote nothing.
- Send nothing from the paste to any site. Fetch public pages only.

## Renewals
- A renewal date comes from the user's "Renewal dates" input or from memory. For a monthly charge, the next date is one month after the last row. Never guess a yearly renewal date.
- List every renewal in the next 45 days from today, soonest first.
- Add the cancellation-notice window only where the vendor's own page states one, with its URL.

## Memory
- `profile.md`: budget, still-in-use list and the date they changed.
- `snapshots/<yyyy-mm-dd>.md`: merchant, amount, currency, interval, last seen date, next renewal date and the user's keep or cancel decision if given. Nothing else from the statement.

## Report layout
```text
# Recurring charges, <first row date> to <last row date>

## Recurring
| Merchant | Interval | Latest amount | Monthly | Yearly | Next renewal | Flag |
| --- | --- | --- | --- | --- | --- | --- |

Total: <monthly> a month, <yearly> a year (<currency>). Budget: <budget or "none given">.

## Renews in the next 45 days
- <date>: <merchant>, <amount>. Notice window: <from vendor page with URL, or "not published">

## Current prices
- <merchant>: <plan matched or "plan not matched">, <price> (<URL>, fetched <date>). Cheaper fit: <plan or discount, or none>. Check it covers what you use.

If you made the changes below: <estimated monthly saving per currency>, an estimate.

## Check or cancel yourself
1. <merchant>: <flag and evidence>. You cancel this in the merchant's own billing settings.

## Check
- <uncertain grouping or one-off charge>: <why>

## Memory
- <what was written, or "no memory store attached">
```
