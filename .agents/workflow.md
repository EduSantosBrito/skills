# Agent workflow

## Entry point

After repository bootstrap, start every piece of workflow work with the `wayfinder` skill, using the active client's invocation syntax. `wayfinder` is the only work entrypoint and router: it classifies the current state and selects the minimum sufficient next owner.

`setup-skills` is the sole declared exception: it is an explicit repository-bootstrap command used before the workflow is configured, not an entrypoint for work. A workflow owner that detects missing configuration must stop with a diagnostic instead of invoking setup itself.

The active `wayfinder` provider's `references/ROUTES.md` is the authoritative route, requirement, blocker, and fallback table. Before emitting a command, resolve the selected route's skill and capability IDs through the active client's catalog or discovery interface. Winning-provider and location details are useful when exposed; origin, scope, precedence, and overlap are optional diagnostics. Never infer availability from installation paths, consumer directories, or the bootstrap package.

## Session lifecycle

- Every transition to another owner or workflow stage starts a fresh session.
- A human-in-the-loop pause stays in the current session. Resume it after the user replies.
- A handoff uses the durable artifact in the source configured by `.agents/artifact-sources.md`. When no artifact exists, pass a compact, self-contained brief in the command.
- Do not create a temporary handoff file. Before handing off, wait for every background task owned by the current stage and incorporate its result or blocker into the durable artifact or inline brief.

## Main build flow

```text
wayfinder → to-spec → to-tickets → implement → code-review
```

Each arrow is a fresh-session boundary. Enter at a later stage when a durable artifact already establishes its preconditions. `to-tickets` remains an upstream dependency.

If `to-spec` finds a definition gap, it records the gap against the durable definition artifact and hands back to `wayfinder` in a fresh session. It does not ask the user specification questions or silently fill definition gaps.

## Stage ownership

- **Wayfinder:** problem, outcome, actors, shared language, observable scope, authority, constraints, material risk, and human decisions.
- **to-spec:** behaviour, contracts, states, failure behaviour, non-functional requirements, and testing seams.
- **to-tickets:** vertical slices, blocking edges, prefactoring, migration sequencing, and delivery order.
- **implement:** local technical choices consistent with the spec, tickets, and repository standards.

Later-stage details move downstream. Earlier-stage gaps return to their owner through a fresh-session handoff.

## Specialist routes

- `research` owns broad **why** questions across primary sources. It is model-invoked by an owning workflow decision, not a user entrypoint. `answer` mode returns findings without persistence; `record` mode persists one finding in the configured research source.
- `explore` owns read-only **how** traces through the system. It may surface a rationale gap and hand that question to `research`; it does not invent the rationale.
- `prototype` owns a throwaway artifact needed to resolve one design question.
- `codebase-design` owns module boundaries, interfaces, seams, and deepening decisions.
- `create-verification-skill` is used only when a repeated endpoint proof is needed and the repository's verification capability is missing or stale. Existing, current verification remains the source of truth.
- `product-design` is a specialist lens. The active workflow continues to own routing, mutation, artifacts, and handoff.

## Artifact sources

Read `.agents/artifact-sources.md` before creating or fetching workflow artifacts. It names the source, concrete location, presence contract, and convention owner for tasks/maps/tickets, specs, research, domain context, and architecture decisions without duplicating ownership.

Creating or changing a record in Linear, GitHub, GitLab, or any other external system requires explicit user authorization immediately before the effect. Invoking a skill, selecting a route, approving a local draft, or authorizing research does not authorize an external mutation.

## Review

`code-review` requires Hunk and runtime support for two background subagents, one for Standards and one for Spec. Load Hunk with `hunk skill path` and preserve the independent axes. If Hunk or two background subagents are unavailable, review is blocked; there is no fallback review path.
