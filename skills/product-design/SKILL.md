---
name: product-design
description: Product-design guidance for user-facing interfaces and growth journeys. Use when work defines, prototypes, implements, or reviews interaction, visual hierarchy, motion, accessibility, conversion, or redesign.
argument-hint: "<question, artifact, or review target>"
license: Mixed; see LICENSE-emilkowalski, LICENSE-revenue-centric-design, LICENSE-taste, and SOURCES.md
metadata:
  adapted-for: "wayfinder-led workflow"
---

# Product Design

**Coherence** is the governing principle: audience, promise, journey, hierarchy, interaction, visual direction, accessibility, and business model should reinforce the same valuable outcome.

## Contract

Product Design is a specialist lens, not a competing delivery workflow. When another workflow is active, that workflow owns routing, artifacts, workspace mutation, and handoff. Contribute only the product-design decisions that belong to its stage.

When invoked directly, follow the requested mode:

- Answer a bounded design or vocabulary question directly.
- Keep reviews, audits, analysis, and planning read-only unless the user explicitly requests an artifact.
- For implementation, inspect, edit, and verify rather than returning a report.

Use the existing product, design system, repository conventions, and shipped behavior as evidence. A reference supplies decision criteria; it does not authorize replacing a sound local system.

## Required boundaries

These constraints outrank every tactic in the references:

1. **Licensed use.** Do not apply this skill, in whole or in part, to betting, casino, gambling, loot-box, or other real-money games-of-chance products. The Revenue-Centric Design source terms prohibit that use.
2. **Agency.** Keep choices, material consequences, cancellation, and recovery understandable. Defaults may reduce effort; they must preserve informed consent.
3. **Truth.** Use supportable claims and real proof. Label mock content and data. Never fabricate urgency, testimonials, ratings, comparison data, or experiment results.
4. **Accessibility.** Keyboard, pointer, touch, screen-reader, contrast, text scaling, reduced-motion, and reduced-transparency behavior are part of the feature where applicable.
5. **Evidence.** Treat source anecdotes, aesthetic heuristics, and named behavioral mechanisms as hypotheses. Preserve their source and validate consequential claims in the actual product.

## Design read

Recover the smallest model that explains the decision:

- **Audience:** who is making progress, in what context, with what prior knowledge?
- **Outcome:** what observable user result and sustainable business result should improve?
- **Journey:** where does the user arrive, hesitate, decide, succeed, fail, recover, and return?
- **Evidence:** what do research, analytics, support, experiments, and the current artifact establish?
- **System:** which components, tokens, dependencies, constraints, and shipped behaviors already own the decision?
- **Mode:** is this greenfield, a redesign that preserves the current language, or an approved overhaul?
- **Direction:** should visual variance, motion intensity, and information density be restrained, balanced, or expressive?

Keep this read internal when the evidence is clear. State it when visual direction is part of the deliverable or when materially different interpretations need confirmation. Ask only for unresolved decisions that would materially change the outcome; discoverable facts belong to inspection or research.

**Complete when:** the relevant assumptions are explicit and each material unknown has an owner.

## Stage contribution

| Active workflow | Product Design contributes | The workflow continues to own |
| --- | --- | --- |
| `wayfinder` | Audience, outcome, journey, evidence, experience-sensitive scope, and costly-to-reverse design decisions | Classification, definition frontier, authority, risk, and handoff |
| `research` | Product and interface questions that require primary evidence | Source investigation and durable findings |
| `prototype` | Materially different directions and criteria that let the prototype answer one visual or interaction question | Throwaway artifact, comparison surface, and captured verdict |
| `to-spec` | User-visible hierarchy, behavior, states, content, accessibility, recovery, and validation criteria | Canonical specification and testing seams |
| `to-tickets` | Complete user-visible outcomes and applicable state coverage for each vertical slice | Slices, blocking edges, sequencing, and publication |
| `implement` | Reuse of the existing system, coherent craft, complete applicable states, and endpoint verification | Workspace changes, local technical choices, tests, and implementation handoff |
| `code-review` | Product-design standards relevant to the changed experience | Hunk workflow, independent Standards and Spec axes, and inline findings |

Route from the observed work state before applying this lens. A visual uncertainty that needs comparison belongs to `prototype`; an unresolved product, scope, authority, or material-risk decision belongs to `wayfinder`.

## Decision path

1. Establish the design read from the prompt, artifact, and environment.
2. Select only the reference branches that materially affect the current stage.
3. Trace the decision backward from the user-visible endpoint. Give every proposed element a job in comprehension, task completion, trust, feedback, or appropriate delight.
4. Preserve existing owners. Put durable shared decisions in their token, component, journey, or content owner.
5. Verify the endpoint at the depth owned by the active workflow. Separate observed evidence from assumptions and future validation.

For commercial journeys, debug in this order: audience and buying context, promise, proof, offer and friction, then visual presentation. Visual polish cannot repair an upstream product decision.

**Complete when:** the owning workflow can continue without guessing a material experience decision.

## Reference routing

Load only the branches needed for the current decision, but load every branch that materially affects it.

| When the task is about | Open |
| --- | --- |
| General interface architecture, hierarchy, states, components, visual craft, or ethical design | `references/foundations.md` |
| Visual direction for landing pages, portfolios, campaigns, or anti-template review | `references/visual-direction-and-anti-defaults.md` |
| Modernizing an existing interface, preserving a brand, or approving an overhaul | `references/redesign.md` |
| Motion, easing, gestures, continuity, performance, materials, or animation review | `references/motion-and-interaction.md` |
| Naming an animation effect | `references/animation-vocabulary.md` |
| Explicitly choosing, recommending, installing, or replacing a frontend library | `references/ui-library-selection.md` |
| Landing pages, hero copy, CTA, social proof, or conversion | `references/conversion-and-landing-pages.md` |
| First run, empty states, trials, time-to-value, or activation | `references/onboarding-and-activation.md` |
| Cancellation, support burden, churn, retention, or NRR | `references/churn-and-retention.md` |
| Pricing, packaging, trials, upgrades, or monetization | `references/pricing-and-monetization.md` |
| Behavioral mechanisms or persuasion | `references/behavioral-science-toolkit.md` |
| Feature scope, adoption, prioritization, or attention hierarchy | `references/product-strategy-and-features.md` |
| Revenue-Centric Design philosophy and process | `references/revenue-centric-design.md` |
| ICP, positioning, distribution, PLG, GTM, or first customers | `references/positioning-icp-and-gtm.md` |
| AI differentiation, moats, or commoditization | `references/ai-era-differentiation.md` |
| Experimentation, signal quality, churn/LTV, or vanity metrics | `references/metrics-and-experimentation.md` |

Treat exact values, framework recipes, package APIs, benchmarks, and aesthetic tactics as candidates. Verify them against the installed environment, primary documentation, and the rendered result.

## Direct review contract

For a direct review or audit, report findings in user-impact order and keep these parts distinct:

- **Observed:** what the artifact, rendered endpoint, code, data, or research shows.
- **Interpretation:** which product-design decision is implicated and why.
- **Recommendation:** the smallest complete change.
- **Validation:** what would demonstrate improvement.
- **Confidence:** confirmed fact, supported inference, or unresolved assumption.

Cite precise locations. Avoid taste-only findings: connect visual observations to hierarchy, comprehension, consistency, interaction, accessibility, trust, or a declared direction. If static code cannot establish feel, require a rendered or real-device check.

A review is complete when every finding has evidence and a next consumer can act without hidden context. Say explicitly when there are no findings.

## Provenance

This is a deduplicated adaptation of design material by Emil Kowalski, Revenue-Centric Design material distilled from Richard ([@richardrx](https://x.com/richardrx)), and selected ideas from Taste Skill by Leonxlnx. Its structure follows Matt Pocock's writing-for-agents guidance. See `SOURCES.md` and the bundled license files before copying or redistributing it.
