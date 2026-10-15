# Pricing & Monetization Psychology

## Start here

**Entry pointer.** Use this reference when choosing freemium, setting price, structuring a trial or upgrade gate, designing tiers, ordering pricing-page information, or diagnosing monetization conversion. Start with **Model the economics** for cost-to-serve, price floor and ceiling, price increases, price-led competition, and full-funnel viability; use **Time payment to value** for card requirements, trial endings, and upgrade prompts; use **Engineer the comparison** for plan roles, anchors, decoys, tier names, promotional price display, feature order, and choice load.

**Application rule.** Select the source record whose **Use when** matches the case, then keep its **Decision**, **Action**, evidence, caveats, visuals, source language, and source together. Records that overlap remain separate because they are independently sourced.

## Model the economics

### Freemium funnel — compare higher conversion with lower cash
**Decision.** A free plan lifts signup conversion but can crush the economics — the higher top-of-funnel number hides a worse business.
**Use when.** You're tempted by freemium's better conversion rate.
**Action.** Run the funnel (same R$80k/mo traffic, plans from R$199). **With freemium:** ~8% → 800 signups → 80% activate → 5% pay = 32 payers (R$6,368 MRR), saturating ~160 payers under 20% churn, while 768 free users burn AI tokens (~$0.08 each) — real CAC ≈ R$2,540/payer, payback ~13 months. **Without:** ~3% → 300 payers = R$59,700 MRR (~10×), CAC ~R$275, payback ~6 weeks, LTV:CAC 5:1 that reinvests its own profit. Freemium only pays off if free brings *organic/viral* users you didn't pay for.
**Source language.** "One scenario reinvests its own profit; the other funds losses until the money runs out."
**Source.** [@richardrx · 2026-07-01](https://x.com/richardrx/status/2072312844784152628)

### Cost of free — decide freemium by service cost and activation
**Decision.** Freemium isn't good or bad in the abstract — the *cost of free* decides, and it hinges on (1) how much it costs to serve non-payers and (2) how long/expensive activation is.
**Use when.** Considering a free plan, especially as a bootstrapped (non-bigtech) founder.
**Action.** If serving a free user costs almost nothing and TTV is short, free becomes an acquisition channel (Slack — first message in minutes; it's the short TTV, not the cash, that sustains it). If the product runs on AI (dollar-priced tokens) or activation is long, a free account is an expensive bet that a small fraction funds — which needs deep pockets (the exception, not the average founder). On a friendly average, only ~3–4% of freemium converts. Otherwise: charge — well, and early.
**Source language.** "For an AI product, your free user was never free."
**Source.** [@richardrx · 2026-06-30](https://x.com/richardrx/status/2071962778072469560)

### Value price — anchor to delivered value rather than the cheapest competitor
**Decision.** Pricing is a SaaS's biggest lever, yet ~90% of products are underpriced — the founder, who knows every limitation, anchors on the cheapest competitor instead of on value delivered. The buyer only sees the problem solved.
**Use when.** Setting or revisiting price; fearing a "no."
**Action.** Raise toward value. A 30% price increase doesn't yield 30% MRR (some churn), but what remains is nearly pure cash — no acquisition in between — while growing a channel 30% costs money, time, and has a ceiling. Low price costs you later: less budget to reach your ICP, a CAC-obsession trap (the real metric is the CAC↔LTV *gap*, which price widens on both sides), and higher churn (cheap attracts uncommitted buyers). Design link: the number must be sustained by perceived value — your page and first use justify or destroy it.
**Source language.** "Charging more without seeming to be worth more is just raising the price of rejection."
**Source.** [@richardrx · 2026-06-29](https://x.com/richardrx/status/2071634185228329219)

### Price range — set the floor from cost and the ceiling from value
**Decision.** Two calculations bound a price. The floor is cost to serve plus target margin; the ceiling is the reference value — what the client pays today to solve the problem their own way, or the loss they absorb by not solving it. Guessing, or pricing 20% below a competitor, skips both.
**Use when.** Setting or revisiting SaaS pricing.
**Action.** (1) Floor: add infrastructure, support, tools, and AI tokens per account, then apply the target margin (R$10 per account at an 80% margin gives a R$50 floor). Watch two traps: a price that is too low signals low quality before use, and CAC can eat the margin (CAC R$100 against R$40 monthly margin is a 2.5-month payback; churn in month 3 leaves about R$20 for three months of work). (2) Ceiling: quantify the client's delta in money. The post's auto-repair example: about 12 quotes lost a month to missing follow-up × R$800 ticket × 30% margin, recovering one third, is roughly R$3,200 a month in revenue and R$960 in profit. (3) Place the price on a sliding scale: value easy to prove, a convinced buyer, and little competition move it up; value hard to prove, a skeptical buyer, and a competitor on every corner mean settling for about 10% of the value generated. Commodity features such as work orders, scheduling, and reports do not sustain price; they only put you in the same comparison table. The figures illustrate the method and are not benchmarks.
**Source.** [@richardrx · 2026-08-03](https://x.com/richardrx/status/2084250609687884144)

### Price increase — test new prices on new customers, anchored in value
**Decision.** Founders raise prices too little and too late. Price is usually a stronger profit lever than acquisition, yet loss aversion keeps it untouched: fear of losing what you have outweighs the chance to gain.
**Use when.** More than 12 months have passed since the last price change and the product has improved since.
**Action.** Test the new price on new customers only and leave the installed base untouched; the new price wins if higher revenue per customer outweighs any drop in conversion. Raise gradually and anchor every increase in what improved — never announce a bare increase. You will rarely have the volume to A/B test price (see **Require sufficient power before an A/B test** in `metrics-and-experimentation.md`); segment and run willingness-to-pay research instead. The post also claims that customers who pay more churn less; verify that in your own cohorts.
**Evidence.** As quoted in the post and perishable: ProfitWell estimates that a 1% price improvement yields about 8–11% more profit on typical SaaS margins, against about 2% for a 1% acquisition improvement; the post also says 70% of executives rank acquisition as the most important growth lever, without naming the survey. Treat both as context, not as your margin structure.
**Source language.** "If 1% on price pays five times more than 1% on acquisition, why is nearly all your energy at the top of the funnel?"
**Source.** [@richardrx · 2026-06-03](https://x.com/richardrx/status/2062127283977019757)

### Price competition — niche down instead of selling on being cheapest
**Decision.** Competing on price is adverse selection: price-led copies attract bargain hunters who arrive because you are cheapest and leave when someone else is R$1 cheaper — high churn, no loyalty, the most support tickets. Following Guy Kawasaki's "Be a baker, not an eater", bake your own pie through a niche (a CRM for facial-aesthetics clinics, not another CRM) and charge more without a direct comparison.
**Use when.** You are tempted to differentiate only by being cheaper than a large player.
**Action.** Use the large player's weight against it, like jiu-jitsu: mine its public complaints (Reclame Aqui, app stores, Google reviews, communities, Facebook and WhatsApp groups, niche sites) for the niche, angle, vocabulary, pain, and promise of your landing page. Expect to be copied: storefronts look alike, but the model underneath — niche, angle, and economics — is what differs, as with McDonald's real-estate model and Burger King's royalties. Read with **Value price** above.
**Evidence.** The post's claims that one complainer represents about 26 equally unhappy silent customers, and that a niche can charge 5×, are uncited rules of thumb.
**Source.** [@richardrx · 2026-06-03](https://x.com/richardrx/status/2062314549483589691)

## Time payment to value

### Trial card — optimize for the right ICP across the full funnel
**Decision.** Requiring a credit card multiplies trial-to-paid conversion but shrinks signups; the goal is the model that attracts and retains the right ICP, not the one with the highest headline conversion.
**Use when.** Choosing trial-with-card vs trial-without-card (or freemium), or designing recurring billing for a Brazilian market.
**Action.** Weigh the funnel both ways. Trial-with-card converts harder but starves you of volume; trial-without-card floods the funnel with low-intent users. Run the full math, not just the conversion rate. In Brazil, also account for PIX recorrente, whose dynamics differ from monthly card billing.
**Evidence.** ChartMogul 2026 (US, 200 products): trial-with-card converts ~31.4% vs 8.9% without — 3x+. Worked funnel: 1,000 visitors → 30 trials → 9.4 paying (with card) vs 85 trials → 7.5 paying (without). Author observes PIX-recorrente cohorts churn more than card cohorts.
**Source language.** "Don't ask which model converts more — ask which model attracts and retains the right ICP."
**Source.** [@richardrx · 2026-05-15](https://x.com/richardrx/status/2055247161349054950)

### Value trigger — tie the trial’s end to value consumption
**Decision.** Blocking access on a fixed day count (7/14/28) is a lazy rule; the billing trigger should fire on value consumption, after the user's first real win.
**Use when.** You copied a competitor's 14-day trial and paid conversion is failing, or you're setting trial length from scratch.
**Action.** Never paywall before a clear micro-win or solving the core problem — doing so kills conversion and breeds bad word of mouth. Set length using four variables: (1) Product complexity — enterprise needs time for compliance/security review, not just the user. (2) Time to Value — Spotify delivers in seconds, a CRM needs days of data. (3) Usage frequency — rarely-used products may need long trials, or none at all (a once-a-year tax tool shouldn't have a trial). (4) Card entry — no card means a shorter trial to create urgency; with card, watch silent next-month churn. Note: sunk cost only bites if the user built a real asset — a bad onboarding produces frustration, not switching cost.
**Source language.** "Locking access purely on the calendar is a lazy rule that can cost you dearly — you're burning CAC without knowing where value lands."
**Source.** [@richardrx · 2026-03-16](https://x.com/richardrx/status/2033502548301091057)

### Upgrade moment — frame the value already built and at risk
**Decision.** Low upgrade rates are usually a framing-and-timing problem, not a price problem; remind users what they've already invested and what they stand to lose.
**Use when.** A happy, active free user never upgrades, or your upgrade rate sits below 5%.
**Action.** Three framings beat generic limit/discount/feature-gate prompts. (1) Sunk cost: surface the assets they've built — "You created 47 custom reports. On the free plan you lose access to 40." (2) Loss aversion: framing loss outconverts framing gain — "You'll lose access to 8 months of history" beats "Get unlimited history." (3) Limited-access gate timed to an imminent, known result — "Your report is ready. To export as PDF, activate Pro." The timing/context of the gate matters more than the gate itself.
**Source language.** "If your upgrade rate is below 5%, the problem probably isn't price — it's how and when you're asking."
**Source.** [@richardrx · 2026-04-21](https://x.com/richardrx/status/2046544442216054981)

## Engineer the comparison

### Target plan — make the middle tier the intended sale
**Decision.** Each plan has a behavioral job, not just a price; the plan you most want to sell should sit in the middle, flanked by a decoy below and an anchor above.
**Use when.** Building or auditing a SaaS pricing page, especially if you copied competitors without assigning each tier a role.
**Action.** Use the decoy effect: place your target (e.g. Pro) in the middle; make the tier below it clearly inferior on one important attribute (user cap, no critical integration, no priority support) so Pro looks obvious. Keep exactly three plans — four+ triggers the paradox of choice and users stall. Add a top tier (Enterprise) purely to anchor price perception. Ask: "What is my decoy today?" If you can't name one, it likely doesn't exist.
**Evidence.** Ariely's MIT test of The Economist's tiers: with the print-only decoy, 16%/84% chose online/combo; removing it flipped choices to 68%/32%, cutting combo revenue by more than half. Estimated +30–43% subscription revenue.
**Visual.** Economist subscription page; the decoy's removal shifts combo-plan share from 84% down to 32% — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2059951433827426437__1.jpg)
**Source language.** "Option B was never built to be sold — it was built to make C look obvious. It's the bait."
**Source.** [@richardrx · 2026-05-28](https://x.com/richardrx/status/2059951433827426437)

### Comparison frame — use a decoy and high anchor, with Free off the visible top
**Decision.** Conversion shifts when you change the frame of comparison, not the product; equal-looking options cause delay, and showing Free first anchors everyone to zero so everything else feels expensive.
**Use when.** You run the default Free / Pro / Enterprise (sob consulta) ladder and Pro isn't converting.
**Action.** Insert a decoy: a Starter just below Pro with irritating limitations (e.g. R$79 vs Pro R$99) so users compare Starter↔Pro and Pro wins for R$20 more. Remove Free from the visible top so the first number isn't zero — anchoring means the first price seen sets the reference; lead with a higher/previous/Enterprise price so Pro at R$99 reads as cheap.
**Evidence.** The Economist sold 3x more print+digital after adding a same-price print-only decoy nobody bought. Author cites documented tests lifting conversion 10–20% via reframing alone.
**Source language.** "You're competing against your own free plan. And losing."
**Source.** [@richardrx · 2026-04-14](https://x.com/richardrx/status/2044014136770580743)

### Serial position — put the killer feature first and differentiator last
**Decision.** Users don't read pricing lists linearly; attention and memory cluster on the first and last items, so feature order is itself a conversion lever.
**Use when.** Laying out the feature rows inside a pricing card or comparison table.
**Action.** Exploit the serial-position effect (primacy + recency). Top: value anchor — never "24/7 support"; lead with the core/killer feature that solves the ICP's main pain and justifies ~80% of the ticket and the ROI. Middle: utilitarian features (exports, integrations, storage limits) the user won't memorize but will scan to compare against the next plan. Bottom (nearest the CTA): the differentiator, bonus, or loss-aversion hook — a lifetime guarantee or dedicated support. The middle of the list is "a cognitive black hole."
**Visual.** Pricing card emphasizing the bold first row (core feature) and bold last row (super bonus), with greyed utilitarian middle rows — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2029623167900061970__1.jpg)
**Source language.** "Pricing success depends not just on what you deliver, but on the order the brain is led to process the value."
**Source.** [@richardrx · 2026-03-05](https://x.com/richardrx/status/2029623167900061970)

### Value axis — keep one progression and tune the decoy’s distance
**Decision.** A plan ladder must read as one clear progression of value; mixing quantitative and qualitative axes muddles it, and where you place the decoy's price decides which plan looks like the deal.
**Use when.** Naming and pricing tiers, or the "value staircase" between your plans isn't obvious to users.
**Action.** Pick one progression — quantitative (rising credits/users) or qualitative (24/7 human support, special features) — rather than blending both. Borrow Starbucks-style naming (Tall/Grande/Venti) so every tier sounds good and lifts the brand. Then position the decoy: place it near the most expensive plan and the expensive plan looks cheap; place it near the cheapest and the decoy itself becomes the most attractive option. **Tier labels** below qualifies the naming choice: in experimental choice sets, prestige-sounding names reduced deferral but favored cheaper tiers and weakened the middle option's pull, so test names together with the decoy.
**Visual.** Decorative 3D price-tag illustration — no data.
**Source.** [@richardrx · 2026-02-02](https://x.com/richardrx/status/2018357024543715480)

### Good-Better-Best — control the pricing-page comparison
**Decision.** Lost LTV is rarely about price — it's analysis paralysis from a missing choice architecture. The brain is lazy and judges by relative comparison (priming + anchoring), so if you don't design the anchor, users compare you to "nothing" or to the cheapest competitor.
**Use when.** Designing or fixing a pricing page; conversions die at the final step despite strong CAC spend.
**Action.** Use a Good-Better-Best (GBB) structure: **Good** = a stripped entry plan that anchors a low price but is limited enough to make users feel pain and look up (never make it free — then everything above looks expensive). **Better** = your standard plan, the target for ~80% of buyers; price it closer to Good than to Best so users think "paying only ~20% more I get double?" **Best** = the value anchor that exists mainly to make Better look cheap (bicycle analogy: without the carbon-fiber Best, the carbon-wheel Better looks expensive). Golden rule: keep comparisons on one axis — don't pit "10,000 tokens" against "Priority Support"; prefer linear, ideally asymmetric, growth. Cap at 2–5 plans (6 = anxiety, paradox of choice). Then control which attributes you compare — your own "Brazil vs Paraguay" table — choosing indicators that favor your value thesis. Highlight Better with color/size/badges. "Stop making the user do the math — do the math for them."
**Evidence.** Cites Briesch et al. (1997) and Mazumdar et al. (2005) on reference-price models, and Chernev (2015) on choice overload.
**Visual.** Two mirrored BR-vs-PY indicator tables prove framing: swapping which metrics are shown flips which country "wins" — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2018693884449009956__2.jpg), [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2018693884449009956__3.jpg). Four-tier mockup highlights a "Most Popular" target beside a high anchor (Hick's law / few options) — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2018693884449009956__4.jpg)
**Source language.** "Your pricing page is killing your LTV — and I can prove it."
**Source.** [@richardrx · 2026-02-03](https://x.com/richardrx/status/2018693884449009956)

### Tier labels and deal display — test names and promotional typography as bounded experiments
**Decision.** Two hypotheses for pricing pages whose cards are interchangeable with every competitor's. First, on an individual, genuinely favorable promotional price, an unfamiliar typeface may prompt deeper processing of the deal — provided buyers still read the price easily. Second, tier labels may shift both whether buyers choose at all and which tier they choose, and the two effects can run in opposite directions. Neither result has been shown for whole pricing pages or for realized revenue.
**Use when.** Plan distribution has been flat for months and you can run a controlled test, or you are choosing tier names and want to know what they may do to the plan mix.
**Action.** If you test typography, limit it to one genuine promotional price and keep the price legible, comprehensible, and exposed to assistive technology as text; the rest of the page stays fluent, and a price that people struggle to read ends the test. If you test tier names, evaluate them together with the middle-tier anchor, because prestige-sounding labels can weaken the pull of the middle option (**Target plan** and **Value axis** above). Measure choice deferral, initial tier share, and downstream revenue separately. Richard extends the label result to functional names such as Basic, Standard, and Essential; that is his practitioner hypothesis, not the tested comparison. This record prices the naming choice in **Value axis**: aspirational names may reduce deferral, while less prestigious names may shift share toward higher tiers.
**Evidence.** [Motyka et al. (2016)](https://link.springer.com/article/10.1007/s11747-015-0459-0) tested individual favorable price promotions: an unfamiliar font increased purchase behavior when people successfully processed it, while fluent fonts were preferred for monetarily similar offers ([university summary](https://drexel.edu/news/archive/2016/february/game-of-fonts)). [Wang et al. (2024)](https://iro.uiowa.edu/esploro/outputs/journalArticle/A-rose-by-any-other-name/9984618647902771), five experiments with 1,954 participants, compared two prestige-metal families: superior-sounding Silver/Gold/Platinum reduced choice deferral but favored cheaper tiers and weakened the compromise effect; lower-prestige Bronze/Silver/Gold favored higher-priced choices. Both are experimental choice results checked against their abstracts, not field revenue evidence.
**Visual.** Three pricing screenshots from the post quoted by @pankajstwt — a three-column Basic/Starter/Pro with near-identical feature lists; a two-column Launch/Scale; a one-time Starter/Premium/Pro plus Ultimate — generic templates that are hard to tell apart: [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2092692547244007852__q__1.jpg), [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2092692547244007852__q__2.jpg), [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2092692547244007852__q__3.jpg)
**Source.** [@richardrx · 2026-08-26](https://x.com/richardrx/status/2092692547244007852)
