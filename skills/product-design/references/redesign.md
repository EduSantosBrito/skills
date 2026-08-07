# Redesign

Use this reference when changing an existing interface, journey, marketing surface, or visual language. Begin every redesign with **preservation**: identify what already carries brand, user, operational, legal, SEO, analytics, and accessibility value before changing it.

## Workflow

1. **Classify the mode.** Choose Preserve, Overhaul, or Greenfield from [Modes](#modes), using evidence and explicit authority. **Complete when:** the mode, authority, and protected contracts are explicit.
2. **Audit the current artifact.** Record only redesign-relevant evidence from [Audit](#audit), then classify each finding as Preserve, Repair, or Explore. **Complete when:** the audit contains only evidence that affects the redesign, every finding is classified as Preserve, Repair, or Explore, and no retirement rests on fashion alone.
3. **Set the preservation contract.** Apply [Protected contracts](#protected-contracts) before selecting changes. Route any needed contract change to the stage that owns the decision. **Complete when:** every protected contract is either retained or paired with explicit authority and an owning stage for the change.
4. **Choose the smallest sufficient lever.** Work through [Lever order](#lever-order) in order and stop when the requested outcome is met. **Complete when:** the requested outcome is met with the earliest sufficient lever, with harmful or broken behavior corrected first.
5. **Decide whether to prototype.** Use [Prototype handoff](#prototype-handoff) when materially different alternatives cannot be judged reliably in prose or static code. **Complete when:** either the direction can be judged from existing evidence or a one-question prototype has a recorded verdict.
6. **Plan migration and release.** Apply [Migration and release](#migration-and-release) to every affected route, metadata field, analytics event, form, component contract, or design-system foundation. **Complete when:** the old and new contracts, compatibility path, comparison instrumentation, rollback conditions, and post-release validation are defined.
7. **Verify the selected mode.** Use [Mode verification](#mode-verification). **Complete when:** the intended improvement has direct endpoint evidence, protected contracts remain intact or were explicitly migrated, and every residual assumption has a concrete owner.

## Modes

Choose from evidence and explicit authority:

- **Preserve:** modernize the current language while retaining recognizable brand, information architecture, content voice, and behavior.
- **Overhaul:** introduce an approved new visual language while preserving contracts that were not authorized to change.
- **Greenfield:** no shipped interface or approved full replacement; establish direction from the brief and product system.

**Decision boundary:** when Preserve and Overhaul are both plausible and would produce materially different work, ask for that decision. A request to “make it modern” does not authorize an Overhaul.

## Audit

Record only evidence that affects the redesign:

- **Audience and journeys:** entry points, primary tasks, conversion paths, recovery, and returning use.
- **Brand system:** logo treatment, type, color, imagery, iconography, spacing, shape, motion, and voice.
- **Information architecture:** routes, navigation, anchors, headings, content relationships, and search behavior.
- **Behavior:** states, input methods, responsive rules, performance, accessibility, and signature interactions.
- **Operational contracts:** analytics events, experiments, forms, integrations, consent, legal copy, and support flows.
- **Discovery contracts:** ranking pages, URLs, metadata, structured data, redirects, and social previews.
- **Evidence:** research, support signals, analytics, experiments, known defects, and current endpoint observations.

Classify each finding:

- **Preserve:** recognizable or valuable behavior supported by evidence.
- **Repair:** broken, inaccessible, misleading, inconsistent, or unsupported behavior.
- **Explore:** a plausible improvement that needs a prototype, research, or user decision.

**Evidence boundary:** fashion alone is insufficient evidence to classify a pattern for retirement.

## Protected contracts

Preserve these unless the user or owning artifact explicitly authorizes change:

- route structure, public URLs, and redirect behavior;
- primary navigation meaning and established task paths;
- form names, semantics, ordering dependencies, and autofill behavior;
- analytics identifiers and experiment assignments;
- logo, wordmark, and protected brand assets;
- legal, consent, pricing, renewal, and cancellation meaning;
- working keyboard, screen-reader, contrast, text-scaling, and preference behavior;
- content voice and factual claims outside an approved rewrite;
- data and integration contracts hidden behind the interface.

**Boundary:** a visual replacement does not authorize a behavioral or commercial replacement.

**Handoff:** surface a needed contract change to the stage that owns the decision.

## Lever order

Apply changes in leverage and risk order. Stop when the requested outcome is met:

1. **Hierarchy and content clarity:** fix promise, labels, grouping, order, and the primary path.
2. **Typography and rhythm:** repair measure, hierarchy, spacing, alignment, and responsive composition.
3. **Color, shape, and depth:** normalize semantic tokens and restore consistent hierarchy.
4. **Interaction feedback:** repair states, focus, latency perception, recovery, and accessible alternatives.
5. **Motion:** add continuity or explanation only where a named job remains.
6. **Section or journey recomposition:** change structure when local craft cannot solve the observed problem.
7. **System replacement:** replace a component or design system only with explicit authority and migration evidence.

**Override:** this order does not promise that typography always precedes accessibility or defects. Correct harmful or broken behavior first.

## Prototype handoff

**Trigger:** route to `prototype` when materially different alternatives cannot be judged reliably in prose or static code.

**Question:** ask one question per prototype. Useful questions include:

- Which hierarchy makes the next action understandable?
- Should this preserve the existing visual language or demonstrate an overhaul?
- Does the proposed density work with realistic content?
- Does the interaction explain state change without delaying frequent work?

**Comparison:** compare materially different directions against the same content and endpoint criteria.

**Handoff:** capture the verdict in the owning issue or specification; keep the throwaway implementation out of the production branch.

## Migration and release

Apply this section when changes alter routes, metadata, analytics, forms, component contracts, or design-system foundations:

- name the old and new contract;
- define compatibility, redirects, or expand-contract behavior;
- preserve instrumentation long enough to compare outcomes;
- identify rollback conditions;
- validate discovery, accessibility, performance, and critical journeys after release.

**Consequence boundary:** treat a redesign as a consequential configuration change when it affects a large user population, revenue path, regulated flow, or difficult-to-reverse brand commitment.

## Mode verification

### Preserve

- recognizable assets, language, and primary paths remain recognizable;
- repaired behavior is backed by an observation;
- no protected contract changed silently;
- new craft follows the existing system or an approved evolution of it.

### Overhaul

- authority for the new language is recorded;
- retained content and operational contracts still work;
- migrations, redirects, analytics, and rollback are covered where applicable;
- the result is evaluated at the rendered endpoint with realistic content.

### Greenfield

- direction follows audience, outcome, evidence, and platform constraints;
- new tokens and components represent durable decisions rather than demo-specific values;
- applicable states, accessibility, responsive behavior, and validation are defined.
