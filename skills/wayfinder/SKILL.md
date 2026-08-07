---
name: wayfinder
description: Route any piece of work to its next fitting workflow, or map definition decisions when the work is still foggy.
argument-hint: "<work, issue, map, or artifact>"
disable-model-invocation: true
license: MIT
metadata:
  adapted-from: "mattpocock/skills wayfinder and ask-matt"
  source-commit: "84fdeffd12f2ee307994d1eb6feb48173b6e0502"
---

# Wayfinder

Use this as the entry point for work of any size. Take the **minimum sufficient route**: the least ceremony that preserves correctness, evidence, and authority. Route clear work immediately; enter full wayfinding only while definition decisions remain.

## 1. Orient

Before writing user-facing prose:

1. Infer the user's language and locale from their writing and the conversation.
2. Search official standards-body sources for the latest local or national adoption of ISO 24495-1 for that locale.
3. Apply the verified adoption when one exists; otherwise apply the latest available edition of ISO 24495-1.

Write user-facing prose, questions, summaries, and the entire next-step protocol—including the command argument—in that language and locale, using established domain vocabulary and `CONTEXT.md` when available. Keep skill names, paths, standards designations, and canonical artifact headings unchanged. Resolve the active client's invocation syntax before the handoff: Prime Agent uses `/skill:<name>`; use `/<name>` only in clients that expose that alias.

Read the supplied issue, map, spec, ticket, diff, or other artifact before classifying it. Inspect only enough of the environment to establish the work's current state. Finding facts is the agent's job; decisions with material trade-offs belong to the user.

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

Ground every non-obvious field in the request or inspected artifact. Size is not line count or file count. Treat impact independently from implementation size.

Then read [`references/ROUTES.md`](references/ROUTES.md), apply its route table, and select the route. When facts do not distinguish plausible routes, ask the smallest discriminating set of questions before routing; this is routing clarification, not a full grilling session.

## 3. Take the route

- **Direct route:** perform no planning work. Produce a self-contained next-session command carrying the symptom, desired outcome, constraints, and artifact pointers the next skill needs. Do not create a map merely to route a small task.
- **Full wayfinding:** when definition decisions or fog prevent a durable specification, read and follow [`references/FULL-WAYFINDING.md`](references/FULL-WAYFINDING.md). This branch owns shared language, definition-level grilling, the decision map, and automatic research.

Grilling is **scoped**, not counted. Use the stage-ownership contract in `references/ROUTES.md`: go as deep as the current stage requires, assign later-stage decisions downstream, and route earlier-stage gaps back to their owner. A next-session command may authorize a mini grilling session only at its destination stage's depth.

Every factual question surfaced by scoped grilling becomes research work and is dispatched automatically where the workflow supports it. Real-browser automation requires the user's explicit authorization; automatic research never implies browser authorization.

## 4. Explain the route

State:

1. the selected route;
2. the observed facts that selected it;
3. why the nearest plausible alternative was not selected;
4. only the materially relevant standards identifiers from `references/ROUTES.md` under `Standards lenses`—omit the section when none helps frame the problem.

Standards are reasoning lenses, not a claim of certification or formal conformity. Do not reproduce or invent clauses.

## 5. Hand off

End every run with a localized heading equivalent to `Next step`, followed by the localized equivalent of:

> Start a fresh session and run:

Then provide exactly one copyable command using the active client's real invocation syntax. Preserve the skill name and localize its argument. Prefer an existing artifact pointer; otherwise include a compact, self-contained brief. Never emit a `/<name>` alias when the active client requires `/skill:<name>`.

A direct routing run is complete when that command lets a fresh session begin without guessing material context. A full-wayfinding run uses the completion and handoff rules in `references/FULL-WAYFINDING.md`.
