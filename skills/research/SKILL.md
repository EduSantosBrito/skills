---
name: research
description: Investigate broad why questions—rationale, history, alternatives, constraints, regressions, thresholds, or disputed claims—against primary sources with explicit evidence labels and verifiable citations. Use when Wayfinder needs evidence before definition, or when code history, docs, APIs, or external facts require research.
argument-hint: "<question> [answer|record]"
license: "MIT; see LICENSE-mattpocock, LICENSE-pstack, and SOURCES.md"
metadata:
  adapted-from: "mattpocock/skills research; cursor/plugins pstack why"
  matt-source-commit: "5b15a47f2d7150f545fbcacbfe381787fc0230dc"
  pstack-source-commit: "46125561306434d8a1d7745d540d8932ab0cd2a2"
---

# Research

Answer broad **why** questions with an evidence trail. This specialist is model-invoked by an owning workflow decision; it is not a user workflow entrypoint. Invocation selects the capability, not permission for an external effect.

## 1. Set the contract

Restate the question, target, decision it informs, and stopping condition. Ask only when ambiguity would materially change the investigation.

Choose one mode:

- **answer** — the default. Return findings in the conversation. It does not persist findings and makes no workspace or external mutation.
- **record** — use when the owning workflow requires durable findings. Read `.agents/artifact-sources.md`, then follow [`references/RECORD.md`](references/RECORD.md). It persists exactly one artifact in the configured research source. A local new artifact is the mode's sole workspace write; an external create or update still requires explicit user authorization immediately before the effect.

## 2. Build an evidence plan

Start from the sources most capable of distinguishing the live explanations. Choose sources by need, not by checklist:

- For repository rationale, anchor the target in paths, symbols, current code, tests, blame, commits, pull requests, issues, ADRs, and release history. Code establishes mechanics; only an explicit record establishes intent directly.
- For an external contract or fact, prefer the specification, standards body, official documentation, first-party API, source repository, or dataset that owns it.
- For regressions, incidents, thresholds, or product constraints, inspect the relevant first-party operational record, analytics, incident material, or decision trail when available and authorized.

Use secondary sources to discover primary evidence, not as substitutes for it. Search only source categories that could materially answer the question or discriminate between hypotheses; identify unavailable categories that leave a consequential blind spot.

Treat a null result as evidence about the bounded search, not proof of universal absence. Preserve the source, exact query or lookup, scope or time range, and result.

Use read-only search and fetch tools when sufficient. Obtain authorization before launching or controlling a real browser. Creating or changing a record in Linear, GitHub, GitLab, or any other external system requires separate explicit authorization at that effect boundary; skill invocation and browser authorization do not imply it. Never interpolate untrusted input into commands or queries when a structured tool exists.

## 3. Own background work

Prefer background workers when the runtime supports them and source legs are independent or reading is substantial. The current stage remains the owner and sole synthesizer.

Before each dispatch, define:

- one bounded question and source scope;
- a budget: deadline or maximum queries/documents plus a stop condition;
- a destination: findings and citations return to the owner, never directly into the durable artifact;
- cancellation conditions: stale question, duplicated coverage, exhausted budget, withdrawn authority, or no remaining discriminating evidence.

Workers stay read-only. Run independent legs in parallel and serial dependencies in order. If background execution is unavailable, investigate serially. Join every worker or confirm its cancellation before answering, writing the record, or handing off; no research task remains active at handoff.

## 4. Classify what the record supports

Keep these labels distinct:

- **Direct evidence** — a source explicitly states the fact or rationale. Cite it adjacent to the claim.
- **Inference** — evidence supports a conclusion that no source states. Show the chain and hedge the wording.
- **Hypothesis** — a plausible, testable explanation. State what would support or falsify it.
- **Gap** — material evidence is unavailable, unsearched, or absent from a bounded search. Name the consequence.
- **Contradiction** — sources disagree. Present both claims, provenance, and chronology without silently choosing one.

A source may be direct evidence of what someone wrote while still being stale or wrong about shipped behavior. Reconcile code, history, and external records where the distinction matters. Never turn present-day code shape into historical intent without labeling the result as inference.

Make citations verifiable in under a minute:

- repository evidence: `path:line` and a commit SHA when the version matters;
- history: commit SHA, pull request or issue ID, and permalink when available;
- external evidence: stable first-party URL with section, anchor, page, or version;
- data or tool evidence: system, query or operation, bounded scope, and durable result pointer when one exists.

Do not cite a search-results page for a claim. Put every material claim next to its citation, and list every consulted source—including relevant null results—at the end.

## 5. Deliver

In **answer** mode, use the user's language and progressively disclose:

1. **Bottom line**
2. **Direct evidence**
3. **Inferences**
4. **Hypotheses**, when live alternatives remain
5. **Gaps and contradictions**
6. **Sources consulted**, including bounded null results

Omit empty sections, but never collapse one evidence class into another. If the research informs a change, finish with concise **Preserve / Change / Avoid / Risk** constraints.

In **record** mode, write the artifact only after synthesis. For an external destination, first show the proposed record and ask for explicit authorization; after authorization, create or update only that record. Then return its durable pointer and a short conclusion in the conversation.

Research is complete when the question is answered to the stated stopping condition; repository claims are code/history-anchored where relevant; every material conclusion is labeled and cited; consequential nulls, gaps, and contradictions are visible; the owner has verified worker output; and no background work remains active.
