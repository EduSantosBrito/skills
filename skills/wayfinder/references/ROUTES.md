# Routes

Choose from the observed work state, then use impact and uncertainty to select the necessary depth. `wayfinder` is the only workflow work entrypoint and router. `setup-skills` is an explicit pre-workflow bootstrap exception, not a route for ordinary work. Destination skills own their stage; they do not become competing entry points.

This file is the authoritative source for route owners, requirements, blockers, and fallbacks. Require `.agents/artifact-sources.md`; if it or this table is missing or invalid, stop with a configuration diagnostic and leave bootstrap to a separate explicit setup session. Resolve the selected route's logical skill and runtime-capability IDs through the active client's catalog or discovery interface before emitting a command. Use winning-provider or location details when exposed; origin, scope, precedence, and overlap details are optional diagnostics. Never assume or inspect a `skills/` directory in the consumer repository. A route is available only when its owner and requirements resolve, or when its fallback below resolves. Otherwise report the declared blocker instead of inventing a command.

The table uses skill names as client-agnostic route labels. Render handoffs with the active client's actual invocation syntax.

## Route table

Every skill ID in the Owner column must resolve before use. `blocked` means there is no fallback. Capability IDs in Requirements are logical runtime capabilities; discovery is authoritative unless a concrete probe is named.

| Observed state | Owner and route | Requirements beyond the owner | Fallback or blocker |
|---|---|---|---|
| Harm is active or may still be spreading in production, security, privacy, money, or data | `incident-response` | none | If `incident-response` is absent, contain harm and establish ownership, then use `diagnosing-bugs` only if that skill resolves; otherwise blocked |
| Something behaves incorrectly and the cause is not established | `diagnosing-bugs` | none | blocked |
| Raw external issue or pull request needs categorisation and readiness work | `triage` | none | blocked |
| Merge or rebase is already conflicted | `resolving-merge-conflicts` | none | blocked |
| A diff or branch is ready for evaluation | `code-review <fixed-point>` | capability `hunk` at version `>=0.18.1`, probed with `hunk skill path`; capability `background-subagents` with exactly two concurrent workers | blocked; no alternate diff, serial, single-agent, or third-reviewer path |
| A broad **why** question needs primary-source investigation | model-invoke `research <question>` under the current owner | none | blocked; no upstream provider fallback |
| A **how** question needs a read-only end-to-end software trace | `explore <vertical or scenario>` | none | blocked |
| A runnable artifact is needed to answer one design question | `prototype <question>` | none | blocked |
| Module interfaces, boundaries, seams, or deepening need design | `codebase-design <decision>` | none | blocked |
| Shared domain language needs to be established or retained | `domain-modeling <domain question>` | none | blocked |
| A plan, decision, or idea needs explicit stress-testing | `grilling <artifact or decision>` | none | blocked |
| Repeatable endpoint proof is needed and the repository's verification capability is missing or stale | `create-verification-skill <endpoint capability>` | none | blocked |
| An existing rendered interface or journey needs a read-only product-design audit | `product-design review <artifact>` | none | blocked |
| Only a human can complete required external steps | `wizard <procedure>` | none | blocked |
| A spec or agent-ready ticket already defines the work | `implement <pointer>` | none | blocked; no upstream provider fallback |
| One clear, low-impact outcome fits one implementation session | `implement <self-contained brief>` | none | blocked; no upstream provider fallback |
| The outcome is definition-ready but needs a durable specification or multiple delivery slices | `to-spec <definition pointer>` | none | blocked; no upstream provider fallback |
| A durable specification needs vertical delivery slices | `to-tickets <spec pointer>` | none | blocked |
| `to-spec` reports missing definition-level information | `wayfinder <definition artifact and recorded gap>` | none | blocked |
| Product, scope, authority, domain, or material-risk decisions remain open | `wayfinder` full wayfinding in `FULL-WAYFINDING.md` | route-scoped owners used by frontier tickets must resolve before dispatch | blocked for any unavailable selected ticket owner |
| A plan must be answered by someone outside the current conversation and environment | `to-questionnaire <recipient and needed decision>` | none | blocked |
| The request is to learn rather than change or investigate the system | `teach <topic>` | none | capability `direct-answer` when no learning workspace is needed; otherwise blocked |

An urgent label does not turn an incident into ordinary implementation. A technically small change with material impact is not direct implementation merely because its diff may be short. A large specified ticket does not need wayfinding merely because implementation spans files.

## Workflow-wide runtime requirements

- `setup-skills` and `wayfinder` require capability `skill-provider-discovery` to enumerate logical skill and capability IDs. Missing discovery blocks setup or routing.
- Every owner or stage transition requires capability `fresh-session-handoff`. Missing support blocks the transition.
- Every stage that starts background work requires capability `background-work-join`. If work cannot be joined or observably cancelled, remain in the stage.
- `to-tickets` is a required upstream dependency for ticketing. Its absence blocks that route.
- Missing `research`, `to-spec`, or `implement` blocks that route without substituting an upstream provider.
- Route-scoped dependencies are usable only when their IDs resolve. Apply only the fallback in the table.
- `create-verification-skill` is not a fallback for running an existing proof. Route to it only to create or refresh a repeatable project capability.

## Research and exploration

`research` owns broad rationale: history, alternatives, external constraints, and primary-source evidence for **why**. `explore` owns repository-grounded **how**: entry points, control flow, data, effects, and observable outcomes.

`research` is model-invoked by an owning workflow decision and is not a user entrypoint. Its `answer` mode does not persist; its `record` mode persists one configured research artifact. Invocation does not authorize creation or mutation of an external record.

When an `explore` trace finds an unresolved rationale, report the trace first, then hand the rationale question to `research` in a fresh session. When research needs a code-path fact, it may request an `explore` trace. Neither owner silently absorbs the other's question.

## Specialist lenses

A specialist lens informs the owning workflow without becoming a second router or handoff command. Apply `product-design` when work changes or evaluates a user-facing interface, journey, interaction, visual hierarchy, motion, accessibility, conversion surface, or redesign.

Route an experiential comparison to `prototype`, module design to `codebase-design`, and unresolved product, scope, authority, or material-risk decisions to full wayfinding. A read-only audit of an existing rendered experience may route directly to `product-design review`.

## Stage ownership

| Stage | Owns |
|---|---|
| Wayfinder | Problem, outcome, actors, shared language, observable scope, authority, constraints, material risk, and human decisions |
| `to-spec` | Behaviour, contracts, states, failure behaviour, non-functional requirements, and testing seams; records and returns definition gaps without questioning the user |
| `to-tickets` | Vertical slices, blocking edges, prefactoring, migration sequencing, and delivery order |
| `implement` | Material local technical choices not settled by the spec, tickets, repository, or discoverable facts |

Every owner or stage transition starts a fresh session. A live human-in-the-loop pause remains in the current session. Later-stage decisions move downstream; earlier-stage gaps return to their owner through a durable artifact pointer.

Local reversible choices governed by repository conventions belong to the agent. Discoverable facts belong to research or exploration, not to the user.

## Standards lenses

Mention only identifiers materially connected to the problem. Standards are lenses, not claims of conformity.

| Problem signal | Identifiers |
|---|---|
| Requirements, scope, or behavioural ambiguity | ISO/IEC/IEEE 29148 |
| General product quality or testing | ISO/IEC 25010; ISO/IEC/IEEE 29119-2 |
| AI-system quality or testing | ISO/IEC 25059; ISO/IEC TR 29119-11 |
| AI risk or impact on people | ISO/IEC 23894; ISO/IEC 42005 |
| AI lifecycle | ISO/IEC 5338 |
| Human-centred interaction | ISO 9241-210 |
| Accessibility | ISO/IEC 30071-1 |
| Information security | ISO/IEC 27001; ISO/IEC 27002 |
| Privacy | ISO/IEC 27701 |
| Incident management or service continuity | ISO/IEC 27035-1; ISO/IEC 20000-1 |
| Configuration or consequential change | ISO 10007 |
| Software lifecycle | ISO/IEC/IEEE 12207 |

## Route report

Use the user's language and locale. In **Awaiting user** mode, include the route and rationale, then end with the pending questions and requested reply.

In **Handoff** mode, wait for all stage-owned background work, then use:

```markdown
## <localized equivalent of “Route”>

`<skill> ...`

## <localized equivalent of “Why”>

- <observed fact>
- <observed fact>

<why the nearest alternative was not selected>

## Standards lenses

- <identifier, only when material>

## <localized equivalent of “Next step”>

<localized equivalent of “Start a fresh session and run:”>

`<invoke skill using the active client syntax> <durable artifact pointer, or localized self-contained brief when no artifact exists>`
```

Create no transient handoff file.
