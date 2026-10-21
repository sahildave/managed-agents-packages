---
name: workflow-guide
description: Critique template and evidence rules for Landing Page Conversion Critic.
---

# Landing page critique

The agent instructions say what to do. This guide fixes the checklist and the critique layout.

## Checklist, in the order a visitor reads
1. Headline: does it say what the product does and for whom, in the visitor's words?
2. Subheadline and first screen: is the outcome concrete? Is the main call to action visible without scrolling?
3. Call to action: one primary action, a verb that matches the goal, and what happens after the click.
4. Proof: real customer names, logos, numbers or quotes. Proof without a source counts as missing.
5. Objections: price, setup time, switching cost, data safety. Is each answered on the page?
6. Pricing: is it findable from the page?

## Evidence rules
- Quote the page text you are judging. Never critique copy you did not read.
- web_fetch returns text, not layout. Do not judge colour, spacing or visual hierarchy unless the user attached a screenshot.
- You have no analytics. Every friction point is a hypothesis; never claim a conversion rate or a lift.

## Critique layout
```text
# <page URL>, reviewed <yyyy-mm-dd>

## Top friction points
### 1. <one-line problem>
- On the page: "<quote>"
- Why it may cost sign-ups: <hypothesis>
- Test: change "<current text>" to "<proposed text>"; watch <metric the user can measure>

## What already works
- <element>: "<quote>"

## Not checked
- <visual layout, mobile view, page speed: reason>
```
Return three to five friction points, ranked by likely impact.
