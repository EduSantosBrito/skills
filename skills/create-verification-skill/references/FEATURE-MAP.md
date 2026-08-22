# Feature map contract

The map is a small maintained index of endpoint proofs, not an inventory of implementation details. Use the task/map source selected by `.agents/artifact-sources.md` to prioritize features and the spec/docs source to recover intended outcomes. Cite durable artifact pointers economically. The endpoint observation remains the proof.

## Index

Create `features/README.md` inside the generated project-local skill. It contains:

1. the endpoint and scope;
2. baseline Launch and Doctor preconditions;
3. isolation and driving conventions;
4. evidence location, redaction, retention, and skip reporting;
5. an index of 3–5 feature files with one-line observable outcomes.

The index and sibling files must agree exactly. Keep evidence outside scratch state removed by Cleanup.

## Feature file

Use one file per user-visible feature. Begin with an H1 and a one-paragraph user/consumer description. Add concise `Definition sources:` and `Endpoint:` lines, then these four H2 sections in order:

1. `Sub-features` — stable short IDs for the behaviour covered.
2. `How to get to it (user POV)` — each real entry point and prerequisite.
3. `Driving it with <harness>` — preconditions followed by literal actions and observable results.
4. `Gotchas` — traps that can invalidate a run, including shared state or unreachable prerequisites.

Each drive recipe must state:

- the initial known state;
- the user/consumer action through the endpoint;
- the immediate visible or returned result;
- a second endpoint observation for durable side effects when feasible;
- the evidence artifacts retained;
- run-owned state Cleanup removes.

Do not report one entry point as proof of another. Mark an entry point unreachable only with the route attempted and concrete unmet prerequisite.

## Drift signals

The map or harness is stale when a mapped route, command, handle, precondition, launch/readiness rule, evidence assertion, or cleanup rule no longer matches source or runtime. A newly shipped priority surface is drift only when a durable task/spec/doc or concrete public source path shows it belongs in this small map.
