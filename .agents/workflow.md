# Agent workflow

## Entry point

Start every piece of work with the `wayfinder` skill. Use the active client's invocation syntax—Prime Agent uses `/skill:wayfinder`; clients with direct aliases may use `/wayfinder`. It classifies the actual work state before selecting the minimum sufficient route. The repository's custom `wayfinder`, `explore`, `you-lost-me`, `setup-skills`, `product-design`, and `code-review` skills take precedence over conflicting installations.

## Main build flow

```text
wayfinder → to-spec → to-tickets → implement → code-review
```

Enter at a later stage when the work is already diagnosed, specified, ticketed, implemented, or under review. Use `explore` as a read-only on-ramp when the relevant software vertical or data model is not understood.

## Stage depth

- **Wayfinder:** problem, outcome, actors, shared language, observable scope, authority, constraints, material risk, and human decisions.
- **to-spec:** behaviour, contracts, states, failure behaviour, non-functional requirements, and testing seams.
- **to-tickets:** vertical slices, blocking edges, prefactoring, migration sequencing, and delivery order.
- **implement:** local technical choices consistent with the spec, tickets, and repository standards.

A stage may run a mini grilling session for missing decisions at its own depth. It sends earlier-stage gaps back to their owner and assigns later-stage decisions downstream.

## Specialist lenses

A specialist lens informs the owning workflow without becoming a second stage or handoff command. Apply `product-design` when work changes or evaluates a user-facing interface, journey, interaction, visual hierarchy, motion, accessibility, conversion surface, or redesign.

- Product, scope, authority, and costly-to-reverse experience decisions remain with `wayfinder`.
- Visual or interaction alternatives that must be experienced route to `prototype`; `product-design` supplies the comparison criteria.
- Specifications, tickets, implementations, and reviews keep their normal owners while applying the relevant product-design references.
- A requested read-only audit of a rendered experience may route directly to `product-design review`.

## Research

Facts are the agent's job. Dispatch every research ticket surfaced by scoped grilling automatically and record durable findings against primary sources. Real-browser automation requires explicit user authorization.

## Communication and handoff

Infer the user's language and locale. Apply the applicable local or national adoption of ISO 24495-1, falling back to the latest international edition. End each phase with one copyable command for a fresh session, localized for the user while preserving skill names, paths, identifiers, and canonical artifact headings.

## Review

`code-review` uses Hunk. Load the Hunk skill by running `hunk skill path`, follow that skill, and preserve the independent Standards and Spec review axes. Record actionable findings as Hunk comments when a live review session is available.
