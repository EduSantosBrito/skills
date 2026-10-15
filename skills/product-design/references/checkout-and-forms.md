# Checkout & Forms

## Start here

**Entry pointer.** Use this reference when designing or diagnosing a checkout, signup-to-paid flow, lead form, registration form, or any high-stakes form where users drop out one input at a time. Start with **Reduce effort** for field count, input types, and perceived effort; use **Remove surprise and risk** for fees, trust signals, abandonment causes, and fraud-prone moments. For landing-page persuasion before the form, use `conversion-and-landing-pages.md`; for qualification friction during onboarding, use **Place friction deliberately** in `onboarding-and-activation.md`.

**Application rule.** Select the source record whose **Use when** matches the case, then keep its **Decision**, **Action**, evidence, caveats, visuals, source language, and source together. Records that overlap remain separate because they are independently sourced.

**Consent rule.** Minimize effort, never disclosure. Total price, fees, renewal terms, delivery time, return policy, and the reason for any sensitive data stay visible before the user commits. Trust signals, discounts, and proof must be true for the business that shows them.

## Reduce effort

### Perceived effort — count fields, input types, and risk together
**Decision.** Effort and perceived risk can stop people at a form stage. Field count is one source; input type is another (in the post's data, text fields cost less than dropdowns and textareas), and requests that feel risky or invasive, such as a phone number, can cost more. Perceived effort is not real effort: five steps with two fields each can outperform two screens with seven fields each. These are hypotheses to measure in your own funnel.
**Use when.** Optimizing lead forms, pre-checkout, or signup.
**Action.** Estimate perceived effort, not steps: a screen full of text, warnings, and secondary information adds cognitive load even without interaction. Remove or defer fields that the stage does not need, and keep the fields that are required for the transaction, legal compliance, safety, or qualification. Measure completion together with lead quality, so a shorter form that brings worse leads does not count as a win. Sometimes the fix lies between the fields: more breathing room, less noise, clearer hierarchy. The form should feel like a corridor, not an interrogation room.
**Evidence.** As quoted in the post and perishable: a HubSpot analysis of 40,000+ landing pages found 3-field forms converting above 25%, with conversion trending down as fields were added, and a phone field lowering conversion to about 13.5% from 19%. Vendor data on lead forms; validate against your own funnel.
**Source.** [@richardrx · 2026-08-12](https://x.com/richardrx/status/2087502085151424711)

### Form inputs — remove cognitive load one input at a time
**Decision.** Registration forms can lose users one input at a time, wasting CAC while founders polish the hero. Reduce the cognitive load that the stage does not need, so the flow gets out of the user's way.
**Use when.** Conversion leaks between signup and first value, or onboarding is form-heavy.
**Action.** (1) Ask only what is relevant at that step, keeping required, legal, safety, and qualification fields. (2) Prefer tapping or choosing over typing where it fits the data, especially on mobile. (3) Explain why you need sensitive data, such as documents; the post reports that this raises completion, and it is required for informed consent either way. (4) Allow paste: people copy card numbers and postal codes rather than memorize them. (5) Help users avoid password typos with an optional visibility toggle. (6) Choose the control by option count, density, and keyboard use: for a few options, roughly six or fewer, a visible radio group (which may be styled as buttons) is a candidate to test against a dropdown; long lists and keyboard-heavy entry may still suit a select or a combobox. For keyboard types and input zoom on phones, use `mobile-web.md`.
**Source language.** "You lose money on the boring screens."
**Source.** [@richardrx · 2025-12-23](https://x.com/richardrx/status/2003495704849760387)

## Remove surprise and risk

### Checkout minimum — ask the least and surprise with nothing
**Decision.** At checkout, extra inputs can lower conversion, and late negative surprises give people reasons to leave: expensive shipping, any paid shipping, a service fee, a packaging fee. The post presents its list as practitioner experience; test each item on your own checkout.
**Use when.** Auditing or building any checkout, signup-to-paid flow, or high-stakes form.
**Action.** (1) Ask for the fewest fields the transaction, the law, and fraud prevention allow. (2) Show the full cost from the first price the user sees; the post builds extra charges into the product price rather than adding them late. (3) Communicate the security controls you actually have, such as encrypted payment, the payment provider, and buyer protection; a lock icon labeled "Secure purchase" is a cue, not proof, and belongs only beside real controls. (4) Show an extra discount in the cart if one genuinely applies. (5) Show the company's legal identity; in Brazil, the CNPJ company-registration number signals a real company. (6) Show product photos, even for digital products. (7) Split what you can into smaller steps. (8) Use mobile-appropriate inputs, such as `type="tel"` for phone numbers, which keeps `+` and country codes available (see `mobile-web.md`). (9) Use truthful social proof in checkout. (10) Measure completion: different ICPs perceive risk differently.
**Evidence.** The post's headline claim that about 70% of drop-off happens at checkout carries no cited study. It also measures something different from the "97% buy nothing" figure in the next record (abandoners versus all visitors), so do not combine the two numbers.
**Visual.** Richard's own checkout applying the list at once: lock icon and "Site Seguro" in the header; four fields only (name, surname, email, +55 phone with a numeric mask); a product thumbnail in the order summary; a 5% PIX discount and free shipping on the receipt; a "Compre com confiança" trust list (100% money-back, support 7 days a week, 10,000+ sales) with a named testimonial; and the CNPJ in the footer — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/1999584679247134761__1.jpg)
**Source language.** "I worked at PayPal literally designing checkouts for the biggest e-commerces and brands in Brazil. Hundreds of them."
**Source.** [@richardrx · 2025-12-12](https://x.com/richardrx/status/1999584679247134761)

### Abandonment causes — work the known leaks as a checklist
**Decision.** Most visitors buy nothing, and the reasons abandoners commonly state are known; many are candidates for design fixes: extra costs revealed late, forced account creation, slow delivery, a complicated checkout, distrust of the site, unclear total price, site errors, and a weak return policy.
**Use when.** Diagnosing why traffic does not convert to purchase.
**Action.** Treat the causes as a checklist: remove late costs, allow guest checkout, show delivery time early, simplify the checkout, add truthful trust signals, show the total price up front, test for errors, and publish the return policy. Amazon tells international buyers there are no additional costs after purchase; make the same promise only when it is true. Then confirm which causes apply in your own analytics and research.
**Evidence.** Figures as quoted in the post, without a named survey in the record and perishable: late extra costs 49%, forced account creation 24%, slow delivery 19%, complicated checkout 18%, distrust of the site 17%, unclear price 17%, site errors 12%, bad return policy 11%. The shares sum to more than 100%, so respondents could give several reasons; they are shares of abandoners, while "97% of visitors buy nothing" is a share of all visitors.
**Source language.** "You can frame this as winning new conversions, or as better capturing what you're losing today."
**Source.** [@richardrx · 2025-12-09](https://x.com/richardrx/status/1998432350842016222)

### Fraud-risk microcopy — protect the user at the exact moment of risk
**Decision.** Design must protect users from the real environment the product lives in, especially in low-trust markets. A specific line of microcopy at the right moment can reduce the risk of scams that cost more than the friction it adds; it does not guarantee prevention.
**Use when.** Users are being scammed through a flow your product enables, such as delivery-PIN sharing or social engineering.
**Action.** Place the warning at the exact moment of risk, alongside whatever product and operational safeguards the risk requires, in plain language, for example: "Never share your number outside the app. The store and courier already have your contact via chat." Transparency is the antidote in low-trust verticals such as auto repair and delivery. Keep the warning short, specific, and tied to the action it protects; generic warnings everywhere become noise.
**Source language.** "Scam costs more than friction."
**Source.** [@richardrx · 2026-06-29](https://x.com/richardrx/status/2071546806987538924)
