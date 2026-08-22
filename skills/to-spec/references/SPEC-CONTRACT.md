# Specification contract

Publish the specification in the source selected by `.agents/artifact-sources.md` and its convention owner. Use these canonical headings unless that source requires equivalent fields.

## Definition source

Link the durable definition artifact, relevant ADRs, domain context, and any primary research used. Distinguish observed facts from bounded assumptions.

## Problem and outcome

State the actor-visible problem and the observable outcome. Preserve the scope and vocabulary established during definition.

## Scope

Name behaviour included in this specification and explicit out-of-scope boundaries. Do not add delivery slices or speculative extension points.

## Behaviour

Describe externally observable scenarios, including relevant alternate paths. Use examples or tables when they make conditions and outcomes less ambiguous.

## Contracts

For each affected boundary, define applicable inputs, preconditions, outputs, side effects, compatibility obligations, authorization, and ordering or consistency guarantees. Keep uncertain input distinct from parsed, valid, or authorized values.

## States and transitions

Name meaningful states, legal transitions, terminal states, and the source of truth. Include retry, cancellation, recovery, and duplicate handling when the behaviour can observe them.

## Failure behaviour

Define rejection and failure categories, what the actor observes, which effects may already have occurred, and how recovery or reconciliation works. Do not describe an unperformed effect as success.

## Non-functional requirements

State only requirements supported by the definition or governing evidence. Make security, privacy, accessibility, capacity, latency, durability, observability, and operability constraints measurable where material.

## Acceptance criteria

Write criteria as observable conditions at the endpoint that understands success. Cover the main path, material boundaries, negative cases, and relevant failures. Avoid implementation-detail assertions.

## Verification plan

Name the highest economical public seam, existing test or harness prior art, required fixtures or controllable collaborators, and the endpoint proof for each criterion. Prefer one high seam over many internal seams. If the existing seam cannot prove the contract, specify the smallest new capability required and why.

## Completion check

Before publication, confirm:

- every material behaviour has an observable criterion;
- every criterion has a verification path;
- state, failure, and NFR claims agree with the contracts;
- no definition decision was invented;
- links and source pointers resolve from the published artifact;
- the artifact is sufficient for `to-tickets` to create vertical delivery slices without rediscovering the definition.
