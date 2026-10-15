# Conversion & Landing Pages

## Start here

**Entry pointer.** Use this reference when designing or diagnosing a landing page, features page, CTA, social proof, traffic-conversion path, or landing-page contribution to CAC. Start with **Context and diagnosis** when ICP, awareness, traffic quality, page speed, sales validation, or the performance baseline is uncertain; use **Message and proof** for hero comprehension, claims, qualification, CTA language, reviews, imagery, feature communication, and the full-page checklist; use **Attention and action path** for visual hierarchy, deliberation, scanning, and click flow. For checkout, signup, and lead-form completion, use `checkout-and-forms.md`. To decide which sections a page has and in what order, start with **Section argument**.

**Application rule.** Select the source record whose **Use when** matches the case, then keep its **Decision**, **Action**, evidence, caveats, visuals, source language, and source together. Records that overlap remain separate because they are independently sourced.

## Section argument

This section is the authority for section order; it adapts Taste Skill rather than a Revenue-Centric Design record. Before layout, write the page as an argument, one line per section:

| Section | Reader's question | Claim you can prove | Proof or real demonstration | Next step |
| --- | --- | --- | --- | --- |
| 1 | What is this, and is it for me? | A three-legged oak stool, made to order | The stool, shown large | Scroll to how it is made |
| 2 | Why this one? | Each seat is cut from one board | Close-ups of the grain | See the price |

Order the sections by the argument rather than by a stock sequence such as hero, logos, features, testimonial, pricing, and call to action. A section with no claim or other content job can be merged or removed. Required content does not need to sell and must not disappear: navigation, consent, security, terms, legal disclosures, required FAQ answers, and content the user asked for stay. Claims use only proof that exists; the truth and mock-content rules in `visual-direction-and-anti-defaults.md` apply.

## Context and diagnosis

### Context cascade — establish ICP and awareness before visual treatment
**Decision.** The visual layer of a landing page is the tip of a cascade that begins at the ICP — so "make it more colorful" critiques the *end* of a process as if it were the start.
**Use when.** Gathering or acting on LP feedback, or reaching for button color first.
**Action.** Work the cascade in order: ICP → the buyer's **awareness level** (Eugene Schwartz's 5 stages) → what you say and how → visual positioning (tone → form, color, type, space). Low awareness: open on the problem, name the pain in the first fold, then the mechanism and your fix. Higher awareness: go straight to your advantages vs. alternatives. Jump to button color and you've silently (and probably wrongly) answered who you sell to, their awareness, which pain, and what tone.
**Source language.** "They're looking at the end of a process and thinking it's the beginning."
**Source.** [@richardrx · 2026-06-23](https://x.com/richardrx/status/2069469303464730988)

### Context — debug ICP and awareness before visual design
**Decision.** Conversion is context engineering — who arrives, with what pain, at what stage, needing what proof. Two invisible variables must be debugged before writing a line of code: the Who (ICP) and the When (awareness level). Visual design comes last.
**Use when.** Your LP underperforms and you reach for button-color tweaks; or you define ICP by demographics.
**Action.** (1) Reject the demographic fallacy: geography/age/income is a bad proxy — King Charles and Ozzy Osbourne are demographic twins with opposite needs. Real ICP is *buying criteria* (trigger, pain, prior attempt, proof needed); persona is just biography, the spec for your user. (2) Map the visitor's Eugene Schwartz awareness level. Rule: headline speaks to the current stage; proof pushes them one stage forward. Selling "Solution" to the "Unaware" is proposing on a first date. Debug order: ICP wrong → awareness wrong → proof insufficient for the stage → only then touch visual design.

Awareness → angle / hero / proof:
- **Unaware** — symptom & identity / "Still doing X this way?" / simple diagnostic, checklist, benchmark
- **Problem-aware** — cost & urgency / "If you have X, you're losing Y" / numbers, before/after, calculation
- **Solution-aware** — trade-offs & selection / "3 ways to solve X — why the 3rd scales" / honest comparison, matrix
- **Product-aware** — differentiation & proof stack / "Why us, why now" / cases, demo, objections
- **Most aware** — final risk & friction / "Swap X for Y in Z days, no risk" / guarantees, onboarding, effort reduction

**Visual.** Schwartz's 5 awareness stages as a rising ramp (Unaware → Problem → Solution → Product → Most Aware) — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2011427153133351046__3.jpg); plus the demographic-twins diagram (Charles vs Ozzy, identical on paper) — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2011427153133351046__2.jpg)
**Source language.** "There's no 'conversion rate' in a vacuum. There's contextualized conversion."
**Source.** [@richardrx · 2026-01-14](https://x.com/richardrx/status/2011427153133351046)

### Cold traffic — use scale as the page’s honesty test
**Decision.** Conversion measured on warm audiences (existing followers) is inflated — they forgive the page's flaws. Only cold traffic reveals how much of your rate is the page versus borrowed trust.
**Use when.** Ad spend goes up but revenue barely moves, and the conversion rate "drops" even though you fixed nothing.
**Action.** Treat any baseline built on warm public as fiction, not a performance number. When you scale budget into cold traffic and the rate collapses, that gap is the page's real ceiling — fix the obvious page defects first, then judge media.
**Evidence.** A founder tripled ad spend; revenue rose only 11%. Warm-traffic conversion of ~3% (driven by Instagram followers) cratered to 0.5% on cold traffic; fixing the obvious lifted it to 2% — 4x the real number.
**Source language.** "Scaling budget into cold traffic works like an honesty test: it shows how much of your conversion is your page and how much is borrowed trust."
**Source.** [@richardrx · 2026-06-08](https://x.com/richardrx/status/2063972594223661127)

### Research layer — reconstruct the converting system before reusing a page
**Decision.** A converting sales page is the visible shell of an invisible system. Copying the layout copies what's cheapest to produce; the expensive part (research) stays invisible and gets left behind.
**Use when.** A page "looks like it works" and you're tempted to clone it for your own offer.
**Action.** Before copying, ask: what on this page is a function of the *product*, and what is a function of the *customer research* done before writing each line and placing each element? The hidden layer is customer vocabulary pulled from interviews, objections ordered to the ICP's specific fear, social proof hand-picked to resonate, and a core promise tuned to the stated desire. This error has a name: cargo cult — replicating the visible ritual hoping to summon the result, without grasping the causal mechanism.
**Evidence.** Two ~95%-identical pages, same niche/offer/order: 4% vs 0.6%. The 4% page belonged to Richard's client; the 0.6% was a near-pixel clone by a builder — who unknowingly DM'd the original team to complain it wasn't converting.
**Source language.** "There's a name for copying the form expecting the function. It's called cargo cult."
**Source.** [@richardrx · 2026-05-09](https://x.com/richardrx/status/2053086365781205142)

### Performance loop — judge the landing page by conversion
**Decision.** A landing page isn't a beauty contest — it has one measurable job: qualify the user and lower CAC by turning traffic into revenue. Evaluating a static image with no context is nearly useless.
**Use when.** The timeline turns into "AI vs human" / "who designed it better" debates that ignore conversion, while obvious conversion flaws go unaddressed.
**Action.** Treat conversion as a continuous loop, never an isolated event: form a thesis → ship the interface and collect data → find where the user hesitated, form a new hypothesis, and optimize the next cycle. The debate defaults to aesthetics because it's easier to opine on looks than to measure results — which is exactly what keeps most LPs underperforming.
**Visual.** A side-by-side "Google Stitch vs Human" LP comparison being judged on looks alone — context for the argument, not a model to copy — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2034638793219694734__q__1.jpg)
**Source language.** "Product design doesn't compete with art. It sells."
**Source.** [@richardrx · 2026-03-19](https://x.com/richardrx/status/2034638793219694734)

### Page speed — treat load performance as a conversion experiment
**Decision.** Web performance is a conversion lever, not only engineering hygiene: a faster largest contentful paint (LCP) can raise sales before anyone touches the visual design.
**Use when.** The team separates "conversion work" from performance work, especially on paid traffic, where every bounce has already been paid for.
**Action.** Treat LCP and the other Core Web Vitals as conversion experiments with the same rigor as copy tests: hold offer, creative, and screen constant, then measure sales or leads alongside the speed change.
**Evidence.** As reported in the post: Vodafone Italy A/B-tested a variant with 31% better LCP (same offer, creative, and screen; paid traffic; about 100,000 clicks and 34,000 visits a day per variant) and recorded 8% more sales, 15% better lead-to-visit, and 11% better cart-to-visit. This is one company's test: use it as a reason to measure, not as an expected lift.
**Source.** [@richardrx · 2026-08-04](https://x.com/richardrx/status/2084589988843299217)

### Sales validation — ask what is missing before the buyer pays
**Decision.** Compliments are free and prove nothing. Trying to sell is the cheapest validation test: either the buyer pays, or the hesitation reveals the real objection.
**Use when.** People praise the idea, but nobody buys.
**Action.** Try to close inside the ICP. When the buyer hesitates, ask what is missing for them to pay now — in Brazil, "Falta o que pra você fazer o PIX agora?" ("What's missing for you to send the PIX payment right now?"). The answer is either the real objection, which joins the build list, or politeness. Follow with "If it had that, would you pay now?" and repeat until about 20 sales. Turn recurring doubts into sales arguments and FAQ items; design comes after, to scale what conversation proved sells. Read with "Charge your first ten users from day one" in `positioning-icp-and-gtm.md`.
**Evidence.** Practitioner anecdote: Richard reports selling 20 subscriptions from a gray clickable wireframe whose QR code did not work yet. Buyers asked for invoices and a second mechanic login, not visual polish.
**Ethical boundary.** Tell buyers what works today and what is still being built; a prototype sale must not present unbuilt capability as delivered.
**Source.** [@richardrx · 2026-07-07](https://x.com/richardrx/status/2074539418266812580) and [@richardrx · 2026-06-24](https://x.com/richardrx/status/2069743203863962080)

## Message and proof

### Five-second test — lead with the problem
**Decision.** A visitor scans your LP for ~5 seconds. If they can't answer what it does, who it's for, and why they should care, they leave — they won't stay to figure it out. Conversion begins on the first line.
**Use when.** Your hero opens by describing what the product *is/does* (a feature/category) instead of the visitor's pain.
**Action.** Open with the visitor's problem, not yourself. "AI-powered project management platform" → meh; "Your team loses 6 hours a week hunting for information" → keep going. One talks about itself, the other talks about me. If the first line doesn't connect with the pain, the rest of the page goes invisible.
**Source language.** "If you who built it can't answer in 5 seconds, your visitor can't either."
**Source.** [@richardrx · 2026-05-01](https://x.com/richardrx/status/2050280273682510230)

### Hero comprehension — test the hero with a stranger from the ICP
**Decision.** If a stranger from your ICP cannot say what the product does and for whom after five seconds with the hero, the hero failed, however good it looks. In those seconds the visitor asks, roughly in order: what is this, is this for me, why should I care now. Every second spent decoding brings them closer to leaving.
**Use when.** A hero trades clarity for "creativity": "Revolutionize your workflow" does not say what the product does; "The definitive productivity platform" does not say for whom.
**Action.** Show the hero to one person from the ICP for five seconds, hide it, and ask: "What does this product do? For whom?" Build the hero from (1) a headline that says what the product does, in the customer's language; (2) a subheadline that names the ICP and the concrete result; (3) real visual proof — a screenshot of the product working, not a generic illustration; (4) a specific CTA; (5) immediate social proof above the fold, such as a logo or a number. Specificity sells: "Work-order control for auto repair shops" beats "Management software". Read with **Five-second test — lead with the problem**: that post leads with the pain, this one with what the product does. Both demand the what, for-whom, and why-now answers within five seconds; let the visitor's awareness level decide which leads.
**Source.** [@richardrx · 2026-05-29](https://x.com/richardrx/status/2060409264683044995)

### Specificity — turn description into persuasion
**Decision.** Generic LP copy gets discarded by the brain; specific messages are processed faster and generate more trust. A converting LP shows the *transformation* the product causes, not just what it does.
**Use when.** Your hero reads "The complete platform for [generic category]", a 5-feature subtitle, "Start free", and no real social proof — the default Brazilian SaaS template.
**Action.** Fix the four standard failures: (1) "Complete platform" means nothing → "Cut new-dev onboarding time 40%"; (2) features on top → lead with the pain, feature as the solution (nobody wakes up wanting a "custom report feature"); (3) "Start free" is the weakest CTA (no value, no risk reduction, no urgency) → "See your first report in 2 minutes"; (4) "Used by Company X" proves nothing → "We cut Company X's churn from 12% to 6%". One page describes, the other sells.
**Evidence.** Across 30 Brazilian SaaS LPs: descriptive vs transformation-led ran 0.5% vs 3% conversion — same traffic, 6x more leads — driven by argument sequence and promise specificity, not visual design.
**Source.** [@richardrx · 2026-04-17](https://x.com/richardrx/status/2045154631974539650)

### CTA microcopy — specify the outcome before testing color
**Decision.** The CTA label moves conversion far more than button color or shape — it's the last thing the user reads before deciding, so it must reduce the mental effort of simulating what happens next.
**Use when.** A technical founder is A/B testing button colors for weeks over a 0.3% (non-significant) delta while the label still says "Sign up" with no click trigger.
**Action.** Make the CTA answer the three questions the brain asks before clicking: (1) what happens when I click, (2) how long it takes, (3) what it costs/commits. "Sign up" answers none; "Start free in 30s" answers two. Add a click trigger (the small line under the CTA) to answer the rest and break an objection: "Start Free Trial" + "14 days, no card". Rooted in outcome bias and Construal Level Theory (making the outcome concrete).
**Source language.** "The button is the last thing the user reads before deciding — treat it as such."
**Source.** [@richardrx · 2026-05-25](https://x.com/richardrx/status/2058875777739866490)

### CTA stage — match the label to the funnel stage
**Decision.** The CTA verb should follow the user's state at each funnel stage: first contact, "See how it works" ("Descubra como funciona"); product page, "I want this product" ("Quero esse produto"); checkout, "Complete my purchase" ("Finalizar minha compra"). Short (about four words or fewer), clear, directional labels raise perceived control and confidence.
**Use when.** One generic CTA label serves the whole journey.
**Action.** Audit every CTA against the stage where it appears, then test stage-matched variants. **CTA microcopy** above defines what each label must answer.
**Source.** [@richardrx · 2025-11-07](https://x.com/richardrx/status/1986836679953719632)

### Click trigger — research the objection before writing the line
**Decision.** One line of risk-reducing microcopy beside the CTA — a "click trigger", which marketing calls objection-breaking — can recover hesitant users: "Lifetime guarantee", "Free shipping", "7 days free, no card". It places certainty on top of a known ICP doubt.
**Use when.** Users hesitate right before the CTA.
**Action.** Find the real objections in customer conversations, complaint sites (such as Reclame Aqui in Brazil), and app-store reviews. Write a trigger for the strongest objection, then test which trigger performs best.
**Ethical boundary.** A click trigger is a promise. State only terms the business honors, and keep their conditions visible where the user commits.
**Source.** [@richardrx · 2025-12-19](https://x.com/richardrx/status/2002076748112875558)

### Qualification — filter on the landing page to lower CAC
**Decision.** High CAC is rarely a media problem — it's usually a filtering problem. The landing page can qualify leads before the form, killing deals that were never going to close.
**Use when.** Clicks become leads, leads become SDR calls, calls don't close, and founders react by swapping creative or channel (or blaming the SDR).
**Action.** Pull three filtering levers so the lead self-selects without feeling filtered: (1) copy specificity — "Cash flow for service providers billing R$500k–R$3M" beats "Organize your finances"; (2) visible pricing — screens out no-budget leads so sales only meets real objections; (3) a qualification question as the first interaction (or copy/examples that play that role). CAC is cost per closed deal, not cost per lead.
**Evidence.** If you close 1 in 50 leads, dropping to 30 leads with 1 close nearly doubles media efficiency — same spend, lower CAC.
**Source language.** "The lead with no money won't magically generate money between the landing page and the sales call."
**Source.** [@richardrx · 2026-05-18](https://x.com/richardrx/status/2056385204785213446)

### Credibility — let 4.2–4.5-star imperfection show
**Decision.** A flawless rating reads as fake; consumers distrust unanimity. A profile that includes constructive criticism feels more authentic and converts better than pure praise.
**Use when.** Building or curating reviews/ratings and social proof on a landing page or product.
**Action.** Let imperfection show. Stack the highest-converting combination: a detailed case study with quantifiable ROI, ideally a video testimonial from a brand recognizable to your ICP, plus customer logos. Avoid the common failure — social proof done badly: identical cards, first-name-only, all 5 stars, generic avatars instead of a real photo. Make each review verifiable (e.g., link to the actual LinkedIn post).
**Evidence.** Third-party marketing statistics (vendor surveys and studies; perishable — verify currency before relying on them): Northwestern: purchase probability peaks at 4.2–4.5 stars, not 5. Testimonials lift LP conversion up to 34% (VWO); 5+ reviews → 270% more likely to be bought (Yotpo); 93% read reviews before buying (BrightLocal).
**Visual.** A social-proof wall done right: real faces, names + roles, verifiable reviews, and recognizable client logos (Volkswagen, Coca-Cola, Samsung, Itaú, Volvo, DocuSign, Hotmart) under a "+10,000 professionals" headline — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2054910531132183030__1.jpg)
**Source language.** "Credibility drives conversion."
**Source.** [@richardrx · 2026-05-14](https://x.com/richardrx/status/2054910531132183030)

### Customer-photo layout — test it as a hypothesis, not a rule about faces
**Decision.** A layout fronted by a real customer's photo and quote is a candidate worth testing against a long-form or illustrated page; it is not evidence that real people beat stock models or team photos. The post explains its claimed effect with banner blindness — visitors ignoring what looks like advertising — which remains an untested hypothesis.
**Use when.** Choosing imagery and structure for a landing-page hero or proof section, and you can test the variant on your own traffic.
**Action.** If you test it, change one thing you can name (the layout, the testimonial, or the photo) and photograph real customers with their consent. Re-test any result before generalizing it to another product or page.
**Evidence.** The post says Highrise (the 37signals CRM; 37signals later became Basecamp) found real users and team developers converting best on average, above stock-photo models. 37signals' own write-up ([Signal v. Noise, "Behind the scenes: A/B testing part 3"](https://signalvnoise.com/posts/2991-behind-the-scenes-ab-testing-part-3-final), 2011) does not support that comparison: it tested photographed customers only — no stock models, no staff — and reported that which person appeared mattered little. The person-photo variant also changed the layout and added a testimonial, so the lift cannot be attributed to the photo. The authors caution against copying the result and report that a Basecamp retest did not reproduce it.
**Visual.** The Highrise homepage test side by side: the illustrated "original design" and the "person design" fronted by a real customer's photo and quote, marked +102.5% — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/1985681720104903142__1.jpg)
**Source.** [@richardrx · 2025-11-04](https://x.com/richardrx/status/1985681720104903142)

### Skimming — front-load three bullets and make the demo easy to find
**Decision.** Almost nobody reads your features page — they skim three bullets and hunt for a demo video. Design for that behavior (with the caveat that the more conscious, technical slice of your ICP *will* read the detail).
**Use when.** You're packing a features page with dense prose expecting visitors to read it top to bottom.
**Action.** Front-load three crisp bullets and make a demo video easy to find; let the deep copy serve the minority of technical, high-awareness buyers who actually read it.
**Source.** [@richardrx · 2026-02-09](https://x.com/richardrx/status/2020815036168437814)

### Page checklist — audit the whole landing page top to bottom
**Decision.** A converting landing page can be audited against one checklist: the 2026 list by [@namyakhann](https://x.com/namyakhann) (Supafast), which Richard translated and endorsed in full.
**Use when.** Auditing or building any landing page.
**Action.** Check five layers. **Hero:** one clear promise, one specific audience, one exact-action CTA, a visual that shows rather than explains, and a trust seal above the fold. **Copy:** a headline under 10 words, benefit before feature, customer language, one central transformation, scannable in five seconds. **Social proof:** logos if you have recognizable names, metrics if you have traction, testimonials with specific results, no generic praise. **Structure:** Hero → Pain → Solution → Proof → CTA; at most three feature sections; an FAQ that answers the top five objections; the CTA repeated two or three times. **Technical:** load under three seconds, genuinely mobile-first, a single-scroll flow. The numeric limits are checklist heuristics, not measured thresholds.
**Source language.** "Clarity > creativity. Result > feature. Speed > polish."
**Source.** [@richardrx · 2026-01-02](https://x.com/richardrx/status/2007216871607771303), translating @namyakhann's checklist

## Attention and action path

### Pre-verbal layer — fix contrast, layout, and trust before copy
**Decision.** The brain processes three pre-verbal variables — contrast, on-screen placement, and trust — before it reads the words, and they usually move the needle more than any headline.
**Use when.** You're rewriting home copy for weeks chasing conversion without touching the visual/attentional layer.
**Action.** (1) Contrast is relative to surroundings, not an isolated color — a big, differently-shaped button in whitespace is *seen before it's read* (accessibility ratio 4.5:1 is a floor, not the goal). (2) Placement: Fitts's law (closer, bigger targets get clicked more) plus the F-pattern (Nielsen Norman eyetracking) — a CTA bottom-right with no visual anchor sits outside the attentional map. (3) Trust is built in four reinforcing layers: a real (non-stock) human face, a known brand or specific verifiable proof, an offer that fits the stated problem, and a solution mechanism logically coherent with the promise. When all four align, the user converts without knowing why; when one fails, they invent a rational reason to leave.
**Source language.** "Optimizing copy without working contrast, placement, and trust is masking the symptom."
**Source.** [@richardrx · 2026-04-28](https://x.com/richardrx/status/2049215050997784774)

### Scanning — give the primary action obvious contrast
**Decision.** Users scan interfaces, weighing cognitive effort against payoff, and ignore most of it. They enter with one question — "What can I do here?" — so the primary action must win on contrast within seconds.
**Use when.** The main CTA competes with 6 other elements, or the most important action is buried inside a dropdown that requires a click to reveal.
**Action.** Make the primary action visually dominant so it's found in a glance. If the key button competes with too many elements it loses prominence; if it's hidden behind interaction it's effectively invisible. Leverage image superiority to guide attention down the page.
**Visual.** A login screen annotated with two biases — "limited choice bias" (a single dominant Google sign-in button) and "image superiority" (a vivid hero illustration pulling the eye) — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2042013751742705816__1.jpg)
**Source.** [@richardrx · 2026-04-08](https://x.com/richardrx/status/2042013751742705816)

### Decision window — shorten the path to action below the path to doubt
**Decision.** The purchase decision is mostly made before checkout. Conversion is architecture: the user converts when the path to the action is shorter than the path to doubt, because every extra second of deliberation raises the odds they close the tab.
**Use when.** You're optimizing the checkout, CTA, or headline while ignoring the deliberation time upstream.
**Action.** Compress decision time two ways: pressurize the environment with real scarcity ("Only 1 room left at this price", "Booked 3 times in the last hour") — driven by loss aversion (Kahneman: losing hurts up to ~2x more than the equivalent gain), so "1 left" registers as "I'll lose this"; or remove steps entirely (Amazon's patented 1-Click ordering).
**Evidence.** Booking runs 1,000+ simultaneous experiments (per Lukas Vermeer, 8 yrs leading experimentation); showing sold-out hotels alongside available ones *raised* bookings by sharpening perceived scarcity.
**Source language.** "The user converts when the path to the action is shorter than the path to doubt."
**Source.** [@richardrx · 2026-05-11](https://x.com/richardrx/status/2053832356293738914)

### Performance aesthetic — design for conversion over applause
**Decision.** There's an invisible war between branding (looking good in the screenshot) and performance (conversion, retention, expansion). The page that puts money in the till is often visually aggressive, text-heavy, and far from the Apple aesthetic founders dream of.
**Use when.** You're choosing between a page that wins design compliments and one built to convert.
**Action.** Engineer the converting pattern even if the artist in you cringes: (1) one obvious attention point — eyes go where they must; (2) a high-contrast CTA with redundancy; (3) a clear promise delivering easily-perceived value; (4) guarantee, social proof, and a free element to reduce risk aversion; (5) organic images by the second fold to back the offer and build trust.
**Evidence.** The analyzed page (quoted): 100 visits → 19 signups, a 19% conversion rate.
**Visual.** An "ugly-but-converts" waterproofing LP: urgency bar, high-contrast orange CTAs, a short above-the-fold form, stat row (12,500+ / 4.9★ / 20+ yrs / 100%), and a trust-badge strip (including lifetime warranty) — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2023777916673220817__q__1.jpg)
**Source language.** "Some LPs go after compliments, others go after conversion."
**Source.** [@richardrx · 2026-02-17](https://x.com/richardrx/status/2023777916673220817)

### Focused path — keep clicks on-page and make CTA contrast brutal
**Decision.** For conversion you want little distraction and lots of redundancy. Any clickable element that leads off-page is lost conversion — no matter how prestigious the source.
**Use when.** You're tempted to link out to a glowing NY Times piece or a top influencer's video, or your CTA blends into the interface.
**Action.** Kill outbound clicks entirely. Make the CTA generate strong contrast against the rest of the interface in position, size, and color — if it isn't easy to notice and click, it won't be clicked.
**Visual.** A wireframe showing the level of contrast a CTA button needs against the surrounding interface — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2019514730696565238__1.jpg)
**Source.** [@richardrx · 2026-02-05](https://x.com/richardrx/status/2019514730696565238)

### First landing page — prioritize speed, contrast, proof, and direct action
**Decision.** Profit is more sensitive to conversion than to cost, and the landing page is often the first gate between a founder's product and its users. The page-building platform matters less than speed, clarity, contrast, proof, and direct action.
**Use when.** Building a first landing page cheaply.
**Action.** Follow five rules: (1) use any platform, but deliver content fast — the post targets an "A" grade on GTmetrix; (2) lead with a short pain or a clear benefit, then make the promise tangible in the subheading; (3) create visual contrast with what the ICP sees every day; (4) keep proof at least as strong as the promise, moving from strong, shallow proof at the top to denser evidence below; (5) place direct CTAs tied to the outcome roughly every one and a half sections.
**Source language.** "Nobody wants to know about your product's features — they want what it generates or the pain it kills. Not 6GB of space, 3,000 songs in your pocket."
**Source.** [@richardrx · 2025-11-10](https://x.com/richardrx/status/1987842649261261240)
