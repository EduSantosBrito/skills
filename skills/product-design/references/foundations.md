# Product Design Foundations

## Scope

Use this reference for interface structure, component decisions, visual craft, product ethics, and product-design review.

- For motion decisions, implementation, review, and gestures, use `motion-and-interaction.md`; it is the authoritative motion reference.
- For commercial tactics and sourced records, start from the matching topic reference — e.g. `conversion-and-landing-pages.md`, `onboarding-and-activation.md`, `pricing-and-monetization.md` — or the full routing table in `../SKILL.md`.

## Coherence: align every layer to the outcome

A product feels designed when its audience, promise, hierarchy, behavior, and business model reinforce one another. A visually polished screen can still fail if it addresses the wrong audience, hides the next step, contradicts familiar behavior, or extracts value before delivering it.

Start with the outcome and make every layer answer to it:

1. **Promise:** What progress does the product offer, to whom, and under what conditions?
2. **Proof:** What makes that promise credible for this audience and awareness level?
3. **Path:** What is the shortest understandable route to first and repeated value?
4. **Interface:** What must be seen, understood, chosen, and recovered from at each step?
5. **System:** Which reusable component or token should own each durable decision?
6. **Measure:** What endpoint demonstrates user value and sustainable business value?

## Eight foundations

### Purpose

Every feature, element, and interruption spends attention and trust. Give each one a user job and remove it when the job is weak. “More capability” is not automatically more value.

### Agency

Keep people in control. Make choices and consequences legible, preserve undo where feasible, and reserve confirmation dialogs for genuinely consequential or irreversible effects. An interface that makes a preferred action obvious can still provide honest alternatives and exits.

### Responsibility

Ask for data, permissions, payment, and commitment at the moment their purpose is clear. Collect only what the outcome requires. Anticipate harmful misuse and do not ship a feature whose uncontained risk outweighs its benefit.

### Familiarity

Use conventions to make behavior predictable. Affordances suggest what can be acted on, signifiers communicate state and where interaction happens, and mapping places controls near the objects they affect; things that look alike should behave alike. Break a familiar pattern only with evidence that the alternative improves the target outcome.

### Flexibility

Design for device, input, language, expertise, content size, and ability. The same product may need quick touch interactions on mobile and dense precise workflows on desktop. Personalization is useful when no single arrangement serves legitimate contexts.

### Simplicity

Simplicity is not visual emptiness. Show the common path first, put advanced choices one level deeper, use plain specific labels, and add context when it reduces uncertainty. Keep explanations that users need; removing them makes the screen minimal, not simple.

### Craft

Alignment, typography, states, latency, edge cases, and interaction feedback compound into trust. Values should be intentional and shared where the system benefits. Craft includes maintaining the behavior as content, devices, and features change.

### Delight

Delight is the result of purpose, agency, clarity, and craft working together. Decorative surprise is justified only when it matches the product, does not delay frequent work, and remains accessible.

## Information architecture and wayfinding

Ensure every view answers:

- Where am I?
- What can I do here?
- Which action matters most now?
- What will happen if I take it?
- How do I leave, undo, or recover?

Use hierarchy rather than explanation debt:

- Put the primary action where the reading and task flow lead naturally.
- Use contrast, size, position, spacing, and grouping to encode priority, applying the classical contrast, repetition, alignment, and proximity relationships.
- Keep a control close to the object or state it changes.
- Prefer specific labels such as “Export report” over generic labels such as “Continue.”
- Keep a primary task visible instead of moving it into overflow merely to make the screen look clean.
- Keep destructive actions distinct and proportionate to the actual consequence.

## Design the whole state space

The happy path is one state among many. Account for the states the component or journey can actually enter:

- initial, first-run, and returning
- loading, slow, empty, partial, stale, and offline
- success, validation error, dependency error, and permission denial
- disabled, read-only, destructive pending, and completed
- interrupted, canceled, retried, duplicated, and recovered
- narrow, wide, zoomed, long-content, localized, and text-scaled
- keyboard, pointer, touch, screen reader, reduced motion, and reduced transparency

To test the content and environment states with realistic extreme data, use `interface-stress-testing.md`; for touch, viewport, and safe-area behavior on phones, use `mobile-web.md`.

Do not store visual state that can be derived from authoritative domain state. When optimistic UI is useful, define what happens if the effect fails or completes after the user leaves.

## Components as product boundaries

A component earns reuse by owning a coherent decision, not by wrapping markup.

- Provide a good accessible default before adding variants.
- Expose semantic capabilities and states rather than internal DOM or animation sequencing.
- Make invalid combinations hard to express; use explicit variants for legitimate alternatives.
- Preserve native semantics and input behavior where possible.
- Let content size and localization shape layout; use fixed dimensions only when they do not encode demo copy.
- Put shared values in tokens only when they are durable decisions used across owners.
- Handle edge cases inside the owner when every consumer would otherwise need the same workaround.
- Keep adoption friction low: minimal setup, clear names, examples that demonstrate real states, and providers or dependencies only when concretely needed.

Interactive documentation should let consumers experience states and copy a correct implementation. It is part of the component contract, not marketing garnish.

## Visual craft

### Typography

- Build hierarchy from size, weight, line height, tracking, and measure together.
- Generate a type scale from a modular ratio when no product ramp exists; `design-primitives-and-tokens.md` carries candidate ratios.
- Treat published measure and leading ranges as starting points, not laws; `design-primitives-and-tokens.md` carries the candidate values.
- Tighten tracking and leading gradually as display text grows; keep body text comfortably readable.
- Use optical sizing where the font supports it.
- Prefer relative units so text scaling and zoom do not break the layout.
- Start with a platform or established product typeface; add a new face only for a concrete brand or legibility need.
- Use tabular numbers where changing digits must not shift adjacent content.

### Color and contrast

- Contrast is relational: verify text and controls against their actual background and state.
- Pair color with another way to convey meaning.
- Treat light, dark, high-contrast, forced-color, and translucent contexts as separate test states.
- Use color to reinforce hierarchy rather than make every action compete.

### Space and shape

- Let proximity express relationship and whitespace express separation.
- Reuse a small spacing and radius vocabulary unless the content creates a real exception: pick one base step and build the ladder from it, composing layout on an explicit grid; `design-primitives-and-tokens.md` carries ladder candidates.
- Align optical weight, not only mathematical boxes; icons and text often need visual correction.
- Preserve scanability and functional-data priority when adding decoration; favor signal over ink (Tufte's data-ink ratio).

### Depth and materials

Use depth to explain hierarchy. Scrims indicate a modal interruption; offset and translucency can preserve flow for parallel surfaces. Larger floating surfaces generally need stronger separation than small controls. Provide solid, high-contrast alternatives when transparency or blur reduces legibility.

## Business alignment without dark patterns

Commercial design is legitimate when the product creates real value and the interface helps the right customer understand, obtain, and sustain it.

- Qualify with specificity, transparent constraints, and fit—not shame or obstruction.
- Show truthful proof near the decision it supports.
- Make price, renewal, trial conversion, cancellation, and material limits understandable before commitment.
- Present upgrades when usage establishes the need; do not interrupt unrelated work with manufactured urgency.
- Use only real scarcity and explain what is scarce.
- Let users compare plans while showing the total cost and keeping the disfavored option legible.
- Treat retention as repeated value, accumulated user benefit, and reliable recovery—not captivity.

Defaults and behavioral mechanisms can reduce cognitive effort, but they also concentrate power. Evaluate them against informed consent, reversibility, vulnerable users, and long-term trust.

## Evidence and measurement

Match the method to the uncertainty:

- **Comprehension:** five-second tests, task-based interviews, and first-click tests.
- **Usability:** observed task success, time, error and recovery behavior—not stated preference alone.
- **Accessibility:** semantic inspection plus keyboard, screen-reader, zoom, contrast, and preference-mode checks.
- **Commercial behavior:** funnel events tied to a defined journey, cohort retention, revenue quality, refunds, support burden, and guardrails.
- **Causal claims:** controlled experiments — use `metrics-and-experimentation.md` for test design, sample-size discipline, and stopping rules.

Segment carefully. Warm audiences, existing customers, cold traffic, and different awareness levels are not interchangeable baselines. A local conversion lift can be harmful if it worsens activation, retention, refunds, trust, or accessibility.

## Completion criteria

Review the design by answering every question. The review is complete when every question has an explicit answer and every remaining hypothesis says how it will be tested:

1. Is the target audience and outcome supported by evidence?
2. Can the user identify the primary action and its consequence?
3. Does the journey deliver value before asking for disproportionate commitment?
4. Are all material states and recovery paths represented?
5. Does the interface preserve agency and tell the truth?
6. Is the decision owned by the right component, token, or journey boundary?
7. Does visual hierarchy support the task rather than merely decorate it?
8. Can the change be used with relevant inputs, preferences, content sizes, and assistive technology?
9. Does the endpoint measure actual user and business value?
10. What remains a hypothesis, and how will it be tested?
