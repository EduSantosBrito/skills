---
name: explore
description: Explore and explain a software vertical end to end with visual maps, plain language, and source evidence.
disable-model-invocation: true
license: MIT
---

Explore this vertical before acting.

Work read-only and return the explanation in the conversation. Use only read-only commands; when material evidence requires mutation or access to a shared service, name the gap and ask permission. Treat implementation and persistent documentation as separate actions that require an explicit request.

## Set the language standard

1. Determine the language and locale from my writing and the conversation context. Ask when the locale is materially ambiguous.
2. Search official standards-body sources for the latest local or national adoption of ISO 24495-1 for that locale.
3. Apply the verified adoption when one exists; otherwise apply the latest available edition of ISO 24495-1. If official access is unavailable, state that limitation.
4. Write in the language I am using. Use the project's ubiquitous language from `CONTEXT.md` or equivalent documentation when available, and define unfamiliar terms at first use.

## Build the trace

1. **Frame.** Turn my request into one concrete scenario with a trigger, an observable outcome, and an explicit system boundary. Ask only when ambiguity could change the trace.
2. **Reconnoitre.** Inspect the nearest sources of truth first: repository instructions, structure, documentation, entry points, code, configuration, schemas, migrations, tests, and safe tool output. Consult history, ADRs, runtime evidence, or authoritative external sources only when the nearer sources cannot answer a material question.
3. **Trace.** Follow the scenario end to end through entry point, orchestration, domain rules, data transformations, persistence, integrations or events, and observable outcome. Account for every transition with `path:line` evidence.
4. **Model.** Account for every entity touched by the trace: ownership, identifiers, relationships, lifecycle, invariants, reads, writes, and transaction or consistency boundaries. Cover authorization, failures, retries, idempotency, asynchronous work, feature flags, and observability when they can change the outcome.
5. **Verify.** Reconcile code, configuration, schemas, tests, and runtime evidence. Label material conclusions as **Observed**, **Inferred**, **Unknown**, or **Contradicted**. Tests show intended behavior unless runtime evidence confirms the execution.

Prefer representative paths over branch inventories: explain the main path, then only the alternatives that materially change behavior or architecture.

## Explain the vertical

Use progressive disclosure in this order:

1. **At a glance** — one plain-language sentence stating what the vertical does, followed by its trigger, outcome, and boundary.
2. **Visual map** — the smallest diagram that makes the path immediately visible.
3. **End-to-end trace** — numbered stages explaining input → responsibility/rule → output, with evidence beside each stage.
4. **Data model** — entities, relationships, state changes, source of truth, and important consistency rules.
5. **Material branches** — errors, permissions, external boundaries, and asynchronous behavior that change the result.
6. **Confidence notes** — inferences, unknowns, contradictions, and unavailable systems or runtime evidence.
7. **Reading path** — the smallest sufficient set of files to read next, in order, with one reason per file.

Choose visuals by meaning:

- sequence diagram for runtime interactions;
- entity-relationship diagram for data relationships;
- state diagram for lifecycle;
- flowchart for branching control flow.

Use the fewest visuals that create a clear mental model—normally one overview and, when needed, one data or state view. Prefer Mermaid; use compact ASCII when Mermaid will not render. Use domain names rather than file inventories inside diagrams, and follow every diagram with a short “How to read this” explanation. Never make a diagram the only explanation.

Keep sections short, front-load the takeaway, use one idea per sentence, and prefer concrete examples over abstract descriptions. Quote code only when a small excerpt explains behavior better than a citation.

## Completion

The exploration is complete only when:

- the selected scenario is traced from trigger to observable outcome;
- every material hop, data mutation, boundary, and side effect has evidence;
- the relevant data relationships and state transitions are explained;
- architecturally significant alternatives are covered;
- observations, inferences, unknowns, and contradictions are distinguishable;
- a reader can retell the vertical using the visual map and trace without opening every cited file.
