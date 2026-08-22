---
name: implement
description: Implement a defined change as the smallest complete vertical slice.
argument-hint: "<spec, ticket, or clear brief pointer>"
disable-model-invocation: true
license: MIT
metadata:
  opencode/autoinvoke: false
  adapted-from: "mattpocock/skills implement"
  source-commit: "84fdeffd12f2ee307994d1eb6feb48173b6e0502"
---

# Implement

Implement the supplied spec, agent-ready ticket, or clear low-impact brief. Enter this stage through the repository's `wayfinder` route and keep the supplied durable artifact as the behavioural authority.

## 1. Establish the baseline

Read the artifact and its linked definition, spec, ADRs, and domain context. Resolve configured sources through `.agents/artifact-sources.md` rather than guessing where artifacts live.

Before editing:

- inspect repository guidance, status, staged and unstaged changes, and the affected path;
- capture the pre-implementation `HEAD` as the review fixed point;
- distinguish existing user or agent work from this implementation's intended write-set;
- stop before overwriting a direct conflict, while completing independent work first.

Staging, committing, amending, and pushing are unconditionally outside this stage's ownership. Do not perform them, delegate them to a child, or accept a request to perform them while `implement` owns the session. Report that they require a separate owner and workflow after this stage. Also do not reset, publish, or open a pull request from this stage.

The baseline is complete when existing work is accounted for and the eventual review can identify this implementation without attributing unrelated changes to it.

## 2. Reconstruct the working theory

Trace the changed scenario from entry point to observable endpoint. Read the implementation, callers, consumers, types or schemas, state and effects, tests, configuration, and relevant failure paths.

Write down, in working notes or the final report rather than a transient handoff file:

- the domain concept and affected path;
- invariants that must remain true;
- trust and effect boundaries;
- the authoritative source of truth;
- observable success and failure;
- compatibility constraints and why the current shape may exist.

Resolve discoverable facts from the repository. Return an earlier-stage material definition gap to `wayfinder` rather than encoding a plausible answer. Resolve a spec contradiction through its durable owner rather than weakening the implementation locally.

The theory is sufficient when it explains every boundary the slice will cross and every endpoint claim the verification must prove.

## 3. Choose the slice and proof

Select the smallest **complete vertical slice** that delivers the requested behaviour from boundary to endpoint. Keep parsing, domain decisions, state changes, failure behaviour, and observable output coherent; a thin diff that leaves one of them inconsistent is not a small slice.

Name the highest economical public verification seam before editing:

- Use TDD when that seam can fail deterministically on the missing behaviour without brittle setup. Observe the focused test fail for the intended reason, implement to green, then refactor while green.
- When a red-first test is not economical, state the concrete seam limitation and use the strongest existing executable proof. Do not compensate with mocks coupled to irrelevant call order.

Prefer existing harnesses and project dependencies. Add a seam or tool only when the endpoint cannot otherwise be proved economically.

## 4. Implement and integrate

Make the narrowest coherent change that satisfies the artifact. Parse uncertain input at its boundary, keep invariants with their representation, make state transitions and effects visible, and preserve shipped contracts unless the artifact explicitly changes them.

Run the highest-signal focused check after each meaningful increment. Inspect failures rather than weakening tests, validation, permissions, or security controls.

Delegation is optional. When independent work warrants subagents, read [`references/DELEGATION.md`](references/DELEGATION.md) before dispatch. The parent remains owner and waits for every child before completion.

## 5. Verify the result

Run checks in signal order:

1. focused regression or acceptance tests at the selected seam;
2. relevant static checks, type checks, lint, and build;
3. broader tests proportional to the changed contract;
4. the endpoint proof that observes the requested result through the real supported surface.

Exercise material negative and failure cases. For remote, concurrent, or durable effects, verify the operation-level guarantee the spec names rather than treating delivery, queue acceptance, or a timeout as completion.

Record commands and outcomes exactly. Separate static guarantees, observed test or endpoint evidence, and residual assumptions. Never claim a check that did not run.

## 6. Inspect and hand off

Wait for all children. Re-read the changed path, inspect status and the complete diff, and confirm:

- only intended work was added by this implementation;
- existing work remains preserved;
- generated files, lockfiles, snapshots, and dependency changes have an explained cause;
- the durable artifact, implementation, and verification evidence agree;
- the review fixed point, durable spec or ticket pointers, changed paths, and committed-after-fixed-point, staged, unstaged, and untracked state are known.

Report the outcome, key boundary decision, changed components, checks and endpoint evidence, and residual risk. A commit is not a prerequisite for review: preserve the captured fixed point and enumerate committed-after-fixed-point, staged, unstaged, and untracked changes separately, including `none` for empty categories.

When the review route's declared runtime requirements are available, end with a localized heading equivalent to `Next step`, followed by the localized equivalent of “Start a fresh session and run:”, then exactly one `code-review` command using the active client's syntax. Its argument must carry the fixed point, durable spec or ticket pointers, changed-path scope, and working-tree state needed to review this implementation.

Create no transient handoff file. If review prerequisites are unavailable, report the concrete blocker and remain in this stage rather than emitting an unusable command.
