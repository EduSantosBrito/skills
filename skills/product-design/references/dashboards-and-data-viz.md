# Dashboards & Data Visualization

## Start here

**Entry pointer.** Use this reference when designing or auditing a dashboard, analytics or admin panel, report, or KPI selection. Treat the dashboard as a retention surface: it should deliver enough value that the user needs to return, not only report data. The core rule set — who it serves, noise as a cognitive tax, insights over raw data, the "so what?" test, rounding, grouping by business context, and size-plus-position hierarchy — lives in **Make the dashboard answer "what do I do now?"** in `revenue-centric-design.md`; the records below extend it. For the state coverage every data view needs (loading, empty, partial, stale), use `foundations.md`.

**Application rule.** Select the source record whose **Use when** matches the case, then keep its **Decision**, **Action**, evidence, caveats, visuals, source language, and source together. Records that overlap remain separate because they are independently sourced.

**Truth rule.** Comparative framing ("15% above your monthly target", "You're in the top 20%") must be computed from the user's real data and a stated reference; never fabricate a benchmark to create belonging or urgency.

## Choose what earns a place

### Glanceable dashboard — make the main KPI and its meaning readable at once
**Decision.** A good dashboard informs at a glance, like a car's: the user must keep their eyes on where they are going. Every element either earns its place or is noise. Inform in order to support the user's next decision and the value they get; the post's hope that this lowers churn and raises LTV is a hypothesis to check in your own cohorts.
**Use when.** Designing or auditing any analytics or admin dashboard.
**Action.** (1) Define who the dashboard is for; information without context is spam. (2) Treat everything not useful as noise: each extra line, card, or icon is cognitive load unless it is indispensable for reading the data. (3) Put the main KPI where reading starts for the target locale — top-left for left-to-right readers, which the post explains with the F-pattern, a hypothesis rather than a law. In right-to-left layouts, under assistive technology, or in a responsive reflow, reading starts elsewhere; keep the KPI first in the source order and the reading order. (4) Attach meaning to data: "You generated 500 tickets" becomes "That's 15% above your monthly target"; true comparative framing ("You're in the top 20%") can add belonging. (5) Design the empty state so it guides users to fill it. (6) Drive to action, not to completeness: an actionable panel beats a complete one (GA4 has everything and little that is usable). (7) Personalize by role: a CEO's panel differs from a marketing analyst's.
**Visual.** An annotated repair-shop dashboard ("Quadro Geral") with seven callouts: 01 logo; 02 sidebar navigation; 03 the main revenue KPI (R$57,257, ↗6.2% vs last month) top-left; 04 average ticket; 05 the Max / 12-month / 3-month / 30-day range tabs; 06 a single primary action ("Adicionar OS"); 07 the composition card's ⋮ options menu for personalizing the panel — plus a revenue-composition donut, a 12-month revenue history, and services / parts / outsourcing breakdown cards — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2000930776636940333__1.jpg)
**Source language.** "Information without context is spam."
**Source.** [@richardrx · 2025-12-16](https://x.com/richardrx/status/2000930776636940333)

### KPI shortlist — keep the business's main indicators and leave the rest off
**Decision.** A dashboard is not a pile of gauges. The original dashboard was a board that kept mud off carriage passengers; the Ford Model T kept the idea with just an ignition key and an ammeter, and gauges accumulated from there. That aesthetic is interesting in luxury cars and watch complications, not in software: the more information on screen, the higher the cognitive load and the longer the scan for what is important and actionable.
**Use when.** Stakeholders keep asking to add "just one more" KPI.
**Action.** Build the panel around the main indicators for the business type and leave the rest off it. Candidate shortlists from the post: **e-commerce** — conversion rate, average order value, CAC, customer lifetime value, cart-abandonment rate, and ad return (ROAS or CPA); **SaaS** — MRR, churn, CAC, LTV, ARPU; **apps** — DAU, MAU, retention rate, ARPU, app-store rating, engagement (session length and frequency), and cost per install. Adjust the list to the user's role and decisions.
**Source.** [@richardrx · 2025-11-04](https://x.com/richardrx/status/1985828780838097317)

## Turn data into direction

### Actionable layer — remove information to make room for guidance
**Decision.** Most good product-design work is removal: show less and give clarity to what remains, based on what the user needs on that screen. Removing information opens space for direction, so the app stops only showing data and starts saying what to do with it.
**Use when.** A dashboard shows everything but guides nothing.
**Action.** Compare before and after. Before: a giant number fighting the chart below it, tabs inside tabs, bars that say nothing. After: a chart with room to breathe, the selected month standing out, and space for a card that warns, for example, "Two installments end in August — save what's left over." Less on screen shortens the learning curve, and a product that guides gives a reason to return, turning engagement into retention.
**Source.** [@richardrx · 2026-07-10](https://x.com/richardrx/status/2075623473565647202)
