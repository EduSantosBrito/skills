---
name: explore
description: Read-only, source-grounded explanation of how a software path works.
disable-model-invocation: true
license: MIT
metadata:
  opencode/autoinvoke: false
  informed-by: "cursor/plugins pstack how"
  source: "https://github.com/cursor/plugins/blob/46125561306434d8a1d7745d540d8932ab0cd2a2/pstack/skills/how/SKILL.md"
  source-license: "MIT"
---

Explore this vertical before acting.

Work read-only and return the explanation in the conversation. Use only read-only commands; when material evidence requires mutation or access to a shared service, name the gap and ask permission. Treat implementation and persistent documentation as separate actions that require an explicit request.

`explore` owns **how**: entry points, control flow, data, effects, and observable outcomes. It does not assess architecture or establish broad rationale.

## Set the language standard

1. Determine the language and locale from my writing and the conversation context. Ask when the locale is materially ambiguous.
2. Search official standards-body sources for the latest local or national adoption of ISO 24495-1 for that locale.
3. Apply the verified adoption when one exists; otherwise apply the latest available edition of ISO 24495-1. If official access is unavailable, state that limitation.
4. Write in the language I am using. Use the project's ubiquitous language from `CONTEXT.md` or equivalent documentation when available, and define unfamiliar terms at first use.

## Classify before tracing

Classify the request automatically. Ask only when ambiguity could change its owner or system boundary.

- **Focused** — one function, module, or narrow path. Trace it directly.
- **System** — a subsystem or scenario crosses several modules, processes, services, or state boundaries. Decompose and reconcile it as described below.
- **Rationale-sensitive** — a how trace also needs a specific historical or policy reason to explain a material choice. Trace the behavior first, then recover rationale conditionally.
- **Architecture-assessment** — the user asks where code should live, which boundary should own it, whether the layering is right, or what architecture should change. Hand off to `codebase-design` and stop; do not perform the assessment here.

When broad **why**—motivation, alternatives, external constraints, or historical decisions across sources—dominates the request, hand off to `research` and stop. A narrow unresolved rationale discovered during a trace remains Rationale-sensitive.

## Build the trace

1. **Frame.** Turn my request into one concrete scenario with a trigger, an observable outcome, and an explicit system boundary. Ask only when ambiguity could change the trace.
2. **Reconnoitre.** Inspect the nearest sources of truth first: repository instructions, structure, documentation, entry points, code, configuration, schemas, migrations, tests, and safe tool output. Consult history, ADRs, runtime evidence, or authoritative external sources only when the nearer sources cannot answer a material question.
3. **Trace.** Follow the scenario end to end through entry point, orchestration, domain rules, data transformations, persistence, integrations or events, and observable outcome. Account for every transition with `path:line` evidence.
4. **Model.** Account for every entity touched by the trace: ownership, identifiers, relationships, lifecycle, invariants, reads, writes, and transaction or consistency boundaries. Cover authorization, failures, retries, idempotency, asynchronous work, feature flags, and observability when they can change the outcome.
5. **Verify.** Reconcile code, configuration, schemas, tests, and runtime evidence. Label material conclusions as **Observed**, **Inferred**, **Unknown**, or **Contradicted**. Tests show intended behavior unless runtime evidence confirms the execution.

Prefer representative paths over branch inventories: explain the main path, then only alternatives that materially change behavior or the trace boundary.

### System exploration

For a System question, define two to four independent angles that together cover the framed scenario—for example request/control flow, data/state, external boundaries/failures, and configuration/tests/observability. Give each angle a bounded question and non-overlapping primary scope.

When background subagents are available, launch the angles concurrently as read-only background work. Each worker must follow actual code from an entry point, return claims with `path:line` evidence, and identify gaps or contradictions. When background execution is unavailable, investigate the same angles serially; this is the permitted fallback.

The owner retains synthesis. Wait for every angle, then build one trigger → effect trace across them. Treat worker output as leads, not evidence: inspect the cited sources, verify every material conclusion, and resolve overlaps or contradictions from sources. Neither vote counts nor a worker's self-report establishes confidence.

### Rationale recovery

Recover rationale only when it changes the reader's understanding of a material hop. Check accepted ADRs or the repository's current-decision index first, then relevant history, linked PRs or tickets, and durable documentation. Distinguish their claims from current runtime behavior.

Code shape can support an inference about behavior; it does not prove why that shape was chosen. If no authoritative rationale survives, label it **Unknown**. If broad why becomes the main work, finish the supported how trace and hand the rationale question to `research` in a fresh session.

## Explain the vertical

Use progressive disclosure in this order:

1. **At a glance** — one plain-language sentence stating what the vertical does, followed by its trigger, outcome, and boundary.
2. **Classification** — Focused, System, or Rationale-sensitive, with one sentence explaining the scope.
3. **Visual map** — the smallest diagram that makes the path immediately visible.
4. **End-to-end trace** — numbered stages explaining input → responsibility/rule → output, with evidence beside each stage.
5. **Data model** — entities, relationships, state changes, source of truth, and important consistency rules.
6. **Material branches** — errors, permissions, external boundaries, and asynchronous behavior that change the result.
7. **Confidence notes** — inferences, unknowns, contradictions, and unavailable systems or runtime evidence.
8. **Reading path** — the smallest sufficient set of files to read next, in order, with one reason per file.

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
- behaviorally significant alternative paths are covered;
- observations, inferences, unknowns, and contradictions are distinguishable;
- every System angle is reconciled and its material conclusions are checked in source;
- rationale is either supported by an authoritative artifact, explicitly inferred, or marked Unknown;
- a reader can retell the vertical using the visual map and trace without opening every cited file.
