# Product Strategy & Feature Discipline

## Run every feature through a two-layer "Swiss Knife filter" before building
**Use when** — A roadmap item feels appealing but nobody applied a filter before committing to build.

**Decision** — A feature you ship stays forever and charges rent forever, so the right question isn't "is this good?" but "does it deserve the permanent cost it imposes on the product?"

**Action** — Layer 1 — does it deserve to exist? Pass all four: (1) cognitive load (more surface = more to learn + Hick's law decision time); (2) ICP specificity (a CRM for facial-aesthetics clinics charges 5x a generic one); (3) operational cost (maintain/support/document, not build); (4) reinforces the core claim. Layer 2 — build now? Two axes: easily rejectable (clear "no"?) and easily implementable (cost to the validating version, not the dream version). Build the no-brainers first; fail any of the four, kill it guilt-free. To rank survivors, score (New Users + New Revenue + Impact Level) / Effort.

**Visual** — Prioritization scoring table: (New Users + New Revenue + Impact Level) / Effort = Score — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2059236567533650119__1.jpg)

**Source language** — "Every feature that gets in, stays. And it charges rent forever."

**Source** — [@richardrx · 2026-05-26](https://x.com/richardrx/status/2059236567533650119)

## Design feature adoption into the habitual path
**Use when** — Three weeks post-launch only ~9% of active users opened the feature and ~4% used it twice, despite changelog, email, and "new" badges.

**Decision** — Shipping a feature doesn't make it discovered; users move through their habitual path and never see what they aren't looking for.

**Action** — Stop treating adoption as announcement. The killers are inattentional blindness (users don't see what they aren't seeking) plus status-quo bias (re-learning cost outweighs perceived benefit even when the new way is better). Instead: directional empty states that surface the feature where it'd be used; triggered onboarding fired by the behavior that signals need (CRM user hits the sales page → introduce the objection-busting AI); and a feature adoption rate metric measuring habit/appropriate frequency, not clicks. Anything below an adoption threshold goes back into review.

**Source language** — "Launching a feature is easy; getting it used is a whole other thing."

**Source** — [@richardrx · 2026-05-20](https://x.com/richardrx/status/2057162392048476345)

## Compute your Swiss Knife Index to expose feature creep
**Use when** — The roadmap has become a user wishlist and every new feature feels like progress (especially with AI making building cheap).

**Decision** — A product's worth is measured by features actually used, not features shipped; a bloated product is expensive to sustain and hard to sell, not rich.

**Action** — Swiss Knife Index (SKI) = (features used by >40% of active users in a 30-day window) ÷ (total features). Below 0.3, you own a clumsy Swiss army knife. Fix it with: quarterly audits on real usage data (not team opinion); hide, don't delete (push rarely-used features into advanced settings — reachable for the 3%, gone for the 97%); and a gate on every new feature — "which existing feature do I kill to make cognitive room?" Litmus test: which feature would you show first with 30 seconds to sell? The rest stays invisible until needed. See the academic grounding (2034248739557159293) and the curve (2033880553607364684).

**Visual** — SKI curve — perceived utility rises then declines past the optimal point as complexity keeps climbing — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2057124008445796659__1.jpg)

**Source language** — "Which feature would I show first if I had 30 seconds to sell the product?"

**Source** — [@richardrx · 2026-05-20](https://x.com/richardrx/status/2057124008445796659)

## Design the attention hierarchy to direct behavior
**Use when** — "My interface looks good, but people don't use the main features" — and the key feature is buried behind three clicks the user will never make.

**Decision** — A product that organizes delivers access; a product that directs delivers activation — and the visual hierarchy decides which the user gets.

**Action** — Recognize that attention hierarchy is the structure deciding what users see first, find with effort, or never discover. Built without intent, the product sabotages itself: users use what's most salient, which is rarely what retains. Plan the hierarchy to influence behavior — make the value-driving, retention-driving feature the most prominent thing — instead of merely arranging information neatly.

**Visual** — A typographic demo (huge headline "YOU WILL READ THIS FIRST") proving the eye follows visual weight, not reading order — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2039399756452057159__1.jpg)

**Source language** — "A well-designed attention hierarchy makes the user use what retains; a bad one makes them use what's most salient."

**Source** — [@richardrx · 2026-04-01](https://x.com/richardrx/status/2039399756452057159)

## Ground feature discipline in the academic feature-fatigue research
**Use when** — You need the evidence behind cutting features, and want to separate pre-purchase appeal from post-purchase utility.

**Decision** — Past a cognitive-load threshold, the subjective evaluation of a product doesn't stay neutral — it declines into frustration, confusion, and task abandonment, directly hitting CAC and LTV.

**Action** — Apply the SKI as a decision criterion grounded in feature fatigue. More features help pre-purchase comparison via distinction bias but hurt the decision via analysis paralysis (more options = longer decisions and more no-decisions; no decision, no conversion). Each extra feature steepens the learning curve — measurable B2B productivity loss — and when value comes slowly, users silently churn before the trial ends, blaming themselves, not the product. This complements the index (2057124008445796659) and the curve (2033880553607364684).

**Evidence** — Thompson, Hamilton & Rust (2005), "Feature Fatigue," JMR 42(4); distinction bias (Hsee & Zhang 2004); analysis paralysis (Iyengar & Lepper 2000).

**Source language** — "A product that grows without criteria doesn't get rich — it gets expensive to sustain and hard to sell."

**Source** — [@richardrx · 2026-03-18](https://x.com/richardrx/status/2034248739557159293)

## Past the optimal feature count, a technically bigger product becomes functionally worse
**Use when** — You hear "my interface looks good, but people don't use the main features" — a sign you've passed the optimal point.

**Decision** — The relationship between feature count and perceived utility is non-linear: there's an optimal point, after which each added feature reduces perceived utility while raising sustaining cost and the learning curve.

**Action** — Read the SKI curve: utility climbs to a peak (~10 features in the example) then falls as complexity keeps rising. The fix isn't more visibility — it's reducing the product's cognitive load so the rest becomes visible again. Criterion: any feature used by under 10% of the active base must justify its existence or leave. There's no universal ideal count — only the ideal for your ICP, context, and device.

**Visual** — SKI graph: green perceived-utility curve peaks at the optimal point (10.3 features, 97), red complexity curve rises monotonically and overtakes utility in the "decline zone" — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2033880553607364684__1.jpg)

**Source language** — "A bloated product isn't a rich product — it's a product actively destroying the conversion and retention you paid dearly to win."

**Source** — [@richardrx · 2026-03-17](https://x.com/richardrx/status/2033880553607364684)

## Classify features by real usage, then shrink the product
**Use when** — Auditing a bloated roadmap or justifying a feature purge.

**Decision** — The post argues that in the average product most features are rarely or never used, and that the unused majority can lower activation, raise churn, enlarge the attack surface, and add sustaining cost and complexity. Low usage is a lead for review, not authorization to delete: some features sell without being used, and some matter precisely because they are rare.

**Action** — Measure adoption by feature and cohort; that measurement is necessary but not sufficient. Classify candidates with the post's scheme — A. Core, the small set carrying the product; B. Strategic, contributes to sales; C. Discard candidate — and protect safety, security, accessibility, compliance, recovery, rare critical jobs, and legitimate segments from the discard group. The product owner decides any retirement with evidence of cost and value, a migration or recovery path, and the impact on affected users. The Swiss Knife Index above gives the threshold form.

**Evidence** — Vendor data quoted in the post and perishable: Pendo's analysis across about 2,500 companies' apps found about 6% feature adoption in the average product and 15.6% in the top 10%, leaving about 94% (84.4% in the top decile) rarely or never used.

**Source** — [@richardrx · 2026-07-17](https://x.com/richardrx/status/2078079228717764886)

## Treat feature creep as a business cost and prune it on a schedule
**Use when** — A product keeps growing features without a subtraction ritual.

**Decision** — The Homer Simpson car problem ("fiturite", feature-itis): implementing every unsatisfied request as a feature eventually makes the product hard to operate, steepens the learning curve, and worsens the experience through cognitive overload and choice paralysis. It also costs the business — more development for features that serve few users, more maintenance, and eventually whole teams for barely-needed areas.

**Action** — Treat pruning review as a recurring cost line: grass grows by itself, so you have to mow. Ask who your most strategic users are, what they use, what unused functionality you can abstract away, and what aligns with the vision. Low-usage features that serve low-paying or high-churn sub-niches are candidates, not automatic cuts: apply the protections and owner decision in the previous record before removing anything.

**Source** — [@richardrx · 2025-11-03](https://x.com/richardrx/status/1985329704312709254) and [@richardrx · 2026-07-06](https://x.com/richardrx/status/2074118439321350163)

## Focus on your core; trying to be "all-in-one" dilutes your value proposition
**Use when** — The product is tempted to "embrace the world" and become a do-everything tool, abandoning the specific ICP that made it loved.

**Decision** — Chasing a bigger TAM by going generic destroys retention of your heavy users without converting new ones — the same roadmap mistake in cars and in software.

**Action** — Remember who your ICP actually is and build for them, even at the expense of broad appeal. In software, when UI/UX tries to cover everything, the value proposition dilutes: you wreck heavy-user retention and fail to convert newcomers because you've gone generic. Focus relentlessly on the core.

**Evidence** — Porsche chased China's TAM with generic EVs, abandoning its ICP (visceral flat-six machines); ~€3.9B in losses to reverse the roadmap — operating profit fell from €4,000M (2022) to €40M (9M 2025), margin 18% → 0.2%. [Porsche figures from the quoted post; treat as illustrative.]

**Source language** — "Focus on your damn core."

**Source** — [@richardrx · 2026-03-11](https://x.com/richardrx/status/2031722047080960265)

## Mature the product by doing the same thing better
**Use when** — The product keeps getting denser for heavy users and conversion falls.

**Decision** — Technical founders keep densifying the product for power users until it becomes a Boeing 747 cockpit: expensive, complex, and hard for the average user. Maturing means doing better what the product already does — smoother flows, bug fixes, clearer attention direction. Hidden risk: a power-user product has a smaller top of funnel, so it changes markets (TAM and SAM) and must charge more; the founder then reads "the product is bad" when the ICP simply was not adjusted.

**Action** — Stop adding depth by default; smooth the core flows, fix bugs, and direct attention first. If the product is deliberately moving upmarket, recalculate TAM, SAM, and price, then align the ICP, copy (more executive, less tool-like), visuals (show the result, not the internals), and detail quality (high-paying buyers tolerate careless design less).

**Evidence** — Christoph Janz's five paths to $100M ARR, from the elephant (few customers paying a lot) to the fly (millions paying little), all work; the problem is becoming an elephant without noticing and still charging mouse prices.

**Source** — [@richardrx · 2026-07-02](https://x.com/richardrx/status/2072718071060447691)

## Route cancellation-driven feature requests through the queue
**Use when** — Feature requests from cancelling customers pressure the roadmap.

**Decision** — A cancellation does not buy a feature. When three auto shops cancelled RepareCar over missing boleto (bank-slip) issuance, the request was logged with name and date beside 20+ others in the same queue, the oldest from June; boleto sat in a deliberately-not-doing package because the ICP was already defined.

**Action** — Log each request with the customer and date, aggregate demand, then prioritize by severity, ICP fit, and strategy under the team's own prioritization authority — not by the latest cancellation. In the post's reported practice, bugs jump the queue and anything new defaults to the parking lot; adopt that only if it matches your severity policy. When a customer asks about timing, state the real queue ("20 requests are ahead of yours") instead of promising a date you cannot keep.

**Evidence** — Richard's own support setup, as described in the post: AI triages, a human answers novel questions, both open Linear tickets, and a daily Claude task prioritizes them. One company's practice, not a benchmark.

**Source** — [@richardrx · 2026-08-10](https://x.com/richardrx/status/2086931878251057479)

## Price each roadmap item in runway, then sell
**Use when** — The roadmap keeps growing while distribution is untested.

**Decision** — Building is the founder's comfort zone; distribution is the game. In the survival phase you do both jobs and almost always choose building, pretending the next feature will make selling easier.

**Action** — Before every survival-phase roadmap item, ask how many months of runway the feature costs and whether it actually makes selling easier or only postpones selling. If the honest answer is "it's the comfortable thing to build", spend that time on the job that hurts: selling.

**Evidence** — Richard spent 90% of his time perfecting a delivery product a year before iFood existed; it died polished. As reported in the post: Humane raised about US$240M with ex-Apple founders and polished hardware, returns outpaced sales by summer 2024, and HP took the assets for US$116M.

**Source** — [@richardrx · 2026-07-21](https://x.com/richardrx/status/2079575881115226453)

## Work the sequence before claiming product-market fit
**Use when** — A founder says they want product-market fit (PMF) without the groundwork.

**Decision** — Richard's own ten-step checklist places PMF at step 8 and argues that founders claim it too early. It is one practitioner's sequence, not a required workflow for this skill.

**Action** — Use the checklist's questions to find gaps in the evidence behind a PMF claim and to frame hypotheses inside the active workflow, without imposing its order as gates or changing that workflow's handoffs: (1) define the ICP — does it exist, or is it who you wish it were? (2) surface the ICP's pains and desires — real, verified where, with how many people? (3) understand awareness — do they know the pain, the solution, yours? (4) slice niche and sub-niche — their particularities, and whether they exclude each other; (5) size the TAM of niche and sub-niche — is enough market left after niching? (6) decide who the solution serves — can you stand out there? (7) validate the thesis — is the pain solved in a way the ICP pays for? (8) reach PMF — does the product stick, do users recommend it unprompted, does the business sustain itself without your push? (9) fix leaks in acquisition, activation, and retention, measured where they happen; (10) scale.

**Source** — [@richardrx · 2026-07-09](https://x.com/richardrx/status/2075192130184630688)
