# Specification readiness

Use this gate before drafting or publishing a specification.

## Ready

The definition artifact and its evidence are ready only when a fresh specification session can determine, without inventing a material definition:

- the problem and intended observable outcome;
- affected actors and externally visible scope;
- included and excluded behaviour;
- authority and constraints for consequential effects;
- established domain meanings and applicable ADR decisions;
- material risks, affected people, compatibility obligations, and irreversible consequences;
- which remaining unknowns are discoverable facts rather than human choices.

The artifact need not contain implementation details, test cases, module boundaries, or delivery slices. Those belong to this stage or later owners.

## Missing facts

Research a fact when reliable evidence can settle it without choosing among materially different product outcomes. Cite the result in the spec or gap record. If bounded research cannot settle a fact and different answers would materially change the definition, treat the unresolved choice as a definition gap.

## Definition gap

A definition gap exists when specification would otherwise have to choose a material product, scope, authority, risk, or domain decision. Record each gap in this shape:

```markdown
## Definition gap

### <short gap name>

- evidence: <durable artifact pointers and repository or primary-source citations>
- missing-decision: <one decision stated without proposing a hidden default>
- impact: <behaviour, scope, risk, compatibility, or verification that cannot be specified>
- owner: wayfinder
```

Append or publish the record according to the configured convention for the definition artifact. Preserve evidence gathered in this stage. Do not publish a partial spec, ask the user specification questions, or replace the decision with an assumption.

The branch is complete when the durable gap can be opened by a fresh `wayfinder` session and no stage-owned research remains running.
