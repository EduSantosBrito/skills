---
name: wayfinder
description: Route any piece of work to its next fitting workflow, or map definition decisions when the work is still foggy.
argument-hint: "<work, issue, map, or artifact>"
disable-model-invocation: true
license: MIT
metadata:
  opencode/autoinvoke: false
  adapted-from: "mattpocock/skills wayfinder and ask-matt"
  source-commit: "84fdeffd12f2ee307994d1eb6feb48173b6e0502"
---

# Wayfinder

Use this as the only workflow work entrypoint. `setup-skills` is an explicit bootstrap exception used before workflow work begins, not a competing work entrypoint. Take the **minimum sufficient route**: the least ceremony that preserves correctness, evidence, and authority. Route clear work immediately; enter full wayfinding only while definition decisions remain.

## 1. Orient

Before writing user-facing prose:

1. Infer the user's language and locale.
2. Search official standards-body sources for the latest local or national adoption of ISO 24495-1 for that locale.
3. Apply the verified adoption when one exists; otherwise apply the latest available edition of ISO 24495-1.

Write user-facing prose, questions, summaries, and handoff arguments in that language and locale. Keep skill names, paths, standards designations, and canonical artifact headings unchanged. Resolve and use the active client's invocation syntax without assuming a portable slash-command form.

Read the supplied artifact before classifying. Require `.agents/artifact-sources.md` and use it to locate durable artifacts. Read [`references/ROUTES.md`](references/ROUTES.md) as the authoritative route, requirement, blocker, and fallback table. Resolve the selected route's logical owner and runtime-capability IDs through the active client's catalog or discovery interface before emitting a command. Availability of each required ID is the mandatory provider proof; use the winning provider or location when exposed, and treat origin, scope, precedence, and overlap details as optional diagnostics. Never infer a provider by inspecting consumer directories or source-repository paths. If artifact configuration, the route table, or discovery is missing or invalid, stop with a configuration diagnostic. Do not invoke bootstrap from this workflow session. Use established domain vocabulary and `CONTEXT.md` when available.

## 2. Classify before choosing

First write a factual routing card without proposing a route:

```yaml
work-kind: incident | bug | planned-change | decision | research | review | other
current-state: idea | symptom | reproduced | defined | specified | ticketed | implemented
outcome-clear: yes | no
material-decisions-open: yes | no
execution-span: one-session | multi-session | unknown
existing-artifact: <type and pointer, or none>
impact: <production, external effects, sensitive data, irreversibility, affected people, or none found>
```

Ground every non-obvious field in the request or inspected artifact. Treat impact independently from line count or file count.

Select only a route whose logical owner and required runtime capabilities discovery resolves, or whose fallback declared in `references/ROUTES.md` resolves. A blocked route stays blocked; never emit a command for an unavailable owner.

When facts do not distinguish plausible routes, ask the smallest discriminating set of questions. This is routing clarification, not full grilling.

## 3. Take the route

- **Direct route:** do no planning work. Prepare a self-contained fresh-session command with the outcome, constraints, verification target, and durable artifact pointers the next owner needs.
- **Full wayfinding:** when definition decisions prevent a durable specification, read and follow [`references/FULL-WAYFINDING.md`](references/FULL-WAYFINDING.md).

Use the ownership contract in `references/ROUTES.md`. Assign later-stage decisions downstream. A `to-spec` definition gap returns to `wayfinder`; `to-spec` does not ask the user or invent the missing definition.

`research` owns broad **why** investigations. It is model-invoked by this routing decision, not a user entrypoint; `answer` does not persist, while `record` persists one configured research artifact. `explore` owns read-only **how** traces and may escalate an unresolved rationale question to `research`. Route module-boundary design to `codebase-design`. Route a missing or stale repeatable endpoint-proof capability to `create-verification-skill`; do not route there when current repository verification can already prove the endpoint.

Before creating or changing a map, ticket, comment, issue, or other record in Linear, GitHub, GitLab, or another external system, prepare the proposed mutation and ask for explicit authorization at that effect boundary. Skill invocation, route selection, and prior authorization for research or browser use do not authorize an external mutation.

Every background task has the current stage as owner. Wait for all of them before the stage completes. Incorporate each result or blocker into the durable artifact or inline brief before handoff.

## 4. Explain the route

State:

1. the selected route;
2. the observed facts that selected it;
3. why the nearest plausible alternative was not selected;
4. only materially relevant standards identifiers from `references/ROUTES.md` under `Standards lenses`.

Standards are reasoning lenses, not a claim of certification or formal conformity. Omit the section when none helps frame the problem.

## 5. Pause or hand off

End each response in exactly one terminal mode:

- **Awaiting user:** a routing clarification, authorization, or material decision is pending. Keep the work in this session. Make the questions and requested reply the final content. There is no `Next step` heading or skill command.
- **Handoff:** the current owner or stage is complete and no user reply is pending. Confirm that all owned background work has finished. Start the next owner or stage in a fresh session.

For a handoff, end with a localized heading equivalent to `Next step`, followed by the localized equivalent of:

> Start a fresh session and run:

Provide exactly one command using the active client's syntax. When a durable artifact exists, point to it in its configured source. Otherwise carry a compact, self-contained brief inline. Never create a transient handoff file.

A direct route is complete when the next session can begin without guessing material context. Full wayfinding uses the pause, completion, and handoff rules in `references/FULL-WAYFINDING.md`.
