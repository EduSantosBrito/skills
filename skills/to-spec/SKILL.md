---
name: to-spec
description: Gate a durable definition and publish its specification when ready.
argument-hint: "<durable definition artifact pointer>"
disable-model-invocation: true
license: MIT
metadata:
  opencode/autoinvoke: false
  adapted-from: "mattpocock/skills to-spec"
  source-commit: "84fdeffd12f2ee307994d1eb6feb48173b6e0502"
---

# To Spec

Convert a definition-ready artifact into a durable specification. Enter this stage only through the repository's `wayfinder` route. Work from durable evidence rather than conversation memory.

## 1. Establish the source set

Read, in order:

1. the definition artifact passed by `wayfinder`;
2. `.agents/artifact-sources.md` and the convention owner it names for the definition and specification sources;
3. the relevant `CONTEXT.md` or `CONTEXT-MAP.md` entries and active ADRs described by `.agents/domain.md`;
4. the affected repository path, including public contracts, callers, state, effects, tests, and nearby documentation.

Use the user's language and locale for prose. Preserve canonical artifact headings and established domain vocabulary.

Complete this step when every claim used by the readiness decision has a durable pointer or repository citation.

## 2. Run the readiness gate

Read [`references/READINESS.md`](references/READINESS.md). Separate missing facts from missing decisions:

- Investigate discoverable facts automatically, using primary sources for external claims and repository evidence for system behaviour. Keep research bounded to facts needed by this spec.
- Treat a choice among materially different outcomes, scope, authority, risk, or domain meanings as a definition decision owned by `wayfinder`.

This stage synthesizes and specifies. It does not interview the user, run a mini grilling session, or silently choose a material definition.

The gate is complete only as **ready** or **definition-gap**.

## 3A. Definition gap

When the gate finds a material definition decision, follow the definition-gap branch in `references/READINESS.md`.

Draft the gap against the durable definition artifact in its configured source. Publish no spec. Wait for all stage-owned research before recording the gap. If recording it creates or changes a Linear, GitHub, GitLab, or other external record, obtain explicit user authorization immediately before that effect.

End with one fresh-session handoff to `wayfinder`, using the active client's invocation syntax and pointing to the durable artifact and recorded gap.

## 3B. Publish the specification

When ready, read [`references/SPEC-CONTRACT.md`](references/SPEC-CONTRACT.md). Draft one specification for the configured specification source. The artifact must define behaviour, contracts, states, failures, non-functional requirements, observable acceptance criteria, and the verification seam and plan without taking over ticket decomposition.

For a local new specification, the stage may write the one configured artifact after the readiness gate. Before creating or changing a specification in Linear, GitHub, GitLab, or any other external system, show the proposed effect and obtain explicit user authorization at that boundary. Invoking `to-spec`, selecting this route, or approving a definition does not authorize external publication.

After the authorized write, check the published artifact against every item in the contract. Resolve links and durable pointers from the published location. Wait for all stage-owned research and include its evidence or blocker before completion.

## 4. Hand off

End with a localized heading equivalent to `Next step`, followed by the localized equivalent of “Start a fresh session and run:”, then exactly one command for `to-tickets` using the active client's syntax and the published spec pointer.

The durable source is the handoff. Create no transient handoff file.
