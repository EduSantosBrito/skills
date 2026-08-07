# Routes

Choose from the observed work state, then use impact and uncertainty to select the necessary depth. Prefer an installed skill whose declared contract matches the route. If the needed capability is not installed, say so instead of pretending a command exists; name the intended capability and the closest safe installed route.

The table uses `/<name>` as a compact route label, not a universal command syntax. Render the final command for the active client—for example, Prime Agent uses `/skill:<name>`.

## Route table

| Observed state | Route |
|---|---|
| The repository has not been configured for this workflow and the requested route needs tracker or domain conventions | `/setup-skills` |
| Harm is active or may still be spreading in production, security, privacy, money, or data | An installed incident-response skill. If none exists, establish containment and ownership before routing technical diagnosis to `/diagnosing-bugs`. |
| Something behaves incorrectly and the cause is not established | `/diagnosing-bugs` |
| Raw external issue or pull request needs categorisation and readiness work | `/triage` |
| Merge or rebase is already conflicted | `/resolving-merge-conflicts` |
| A diff or branch is ready for evaluation | `/code-review <fixed-point>` |
| A factual unknown blocks a decision | `/research <question>` |
| A runnable artifact is needed to answer a design question | `/prototype <question>` |
| An existing rendered interface or journey needs a read-only product-design audit | `/product-design review <artifact>` |
| Only a human can complete required external steps | `/wizard <procedure>` |
| A spec or agent-ready ticket already defines the work | `/implement <pointer>` |
| One clear, low-impact outcome fits one implementation session | `/implement <self-contained brief>` |
| The outcome is defined but needs a durable specification or multiple delivery slices | `/to-spec <definition pointer or brief>` |
| Product, scope, authority, domain, or material-risk decisions remain open | Full wayfinding in `FULL-WAYFINDING.md` |
| A plan must be answered by someone outside the current conversation and environment | `/to-questionnaire <recipient and needed decision>` |
| The request is to learn rather than change or investigate the system | `/teach <topic>` or a direct answer when no multi-session learning workspace is needed |

An urgent label does not turn an incident into ordinary implementation. A technically small change with material impact is not a direct implementation merely because the diff may be small. A large but already specified ticket does not need wayfinding merely because implementation spans many files.

## Specialist lenses

Choose the workflow from the observed work state first. A specialist lens informs that workflow; it does not replace stage ownership or create a second handoff command.

Apply `product-design` when work changes or evaluates a user-facing interface, journey, interaction, visual hierarchy, motion, accessibility, conversion surface, or redesign. Because `product-design` permits model invocation, the final command still names only the owning workflow and carries the relevant product-design outcome and artifact pointers in its argument.

Route a visual or interaction uncertainty that needs comparison to `/prototype`; `product-design` supplies the design criteria. Route a read-only audit of an existing rendered experience directly to `/product-design review`. Route unresolved product, scope, authority, or material-risk decisions to full wayfinding even when the likely implementation is visual.

## Stage ownership and grilling

Grilling is scoped by decision depth rather than by a question or round limit:

| Stage | Owns |
|---|---|
| Wayfinder | Problem, outcome, actors, shared language, observable scope, authority, constraints, material risk, and human decisions. |
| `to-spec` | Behaviour, contracts, states, failure behaviour, non-functional requirements, and testing seams. |
| `to-tickets` | Vertical slices, blocking edges, prefactoring, migration sequencing, and delivery order. |
| `implement` | Material local technical choices not settled by the spec, tickets, repository, or discoverable facts. |

Carry the relevant depth in the next-session command. A stage may run a mini grilling session for missing decisions it owns. It routes earlier-stage gaps back and assigns later-stage decisions downstream rather than inventing either.

Local, reversible choices governed by repository conventions belong to the agent. Facts available from the repository or primary sources belong to research, not to the user.

## Standards lenses

Mention only identifiers materially connected to the problem. Do not add a standards section merely to fill it.

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

Use the user's language and locale:

```markdown
## <localized equivalent of “Route”>

`/<skill> ...`

## <localized equivalent of “Why”>

- <observed fact>
- <observed fact>

<why the nearest alternative was not selected>

## Standards lenses

- <identifier, only when material>

## <localized equivalent of “Next step”>

<localized equivalent of “Start a fresh session and run:”>

`/<skill> <localized, self-contained argument or artifact pointer>`
```
