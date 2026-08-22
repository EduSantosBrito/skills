# Full wayfinding

Adapted from Matt Pocock's [`wayfinder`](https://github.com/mattpocock/skills/blob/84fdeffd12f2ee307994d1eb6feb48173b6e0502/skills/engineering/wayfinder/SKILL.md) at commit `84fdeffd12f2ee307994d1eb6feb48173b6e0502`.

Use this branch when definition decisions obscure the route from a loose idea to a durable specification. It resolves a shared frontier of decision tickets. It produces definition decisions, not implementation deliverables.

## Definition depth

Wayfinding owns:

- the problem and desired outcome;
- actors and shared domain language;
- observable scope and exclusions;
- authority and human decisions;
- constraints, trade-offs, material risks, and impacts;
- decisions whose alternatives would materially change the specification.

Apply the ownership contract in [`ROUTES.md`](ROUTES.md). A question belongs on the definition frontier when materially different answers would change the destination, user-visible scope, authority, acceptance, material risk, or a costly-to-reverse commitment. Put other in-scope questions in `Deferred downstream` with their owner.

### Product-design decisions

When the destination changes a user-facing experience, record `product-design` as a specialist lens in `Notes`:

- **Wayfinder:** audience, valuable outcome, journey scope, experience authority, protected redesign contracts, and costly-to-reverse brand or trust decisions.
- **Prototype:** visual, interaction, motion, or density alternatives that must be experienced to resolve one decision.
- **to-spec:** hierarchy, behaviour, states, responsive rules, accessibility, recovery, content contracts, and validation criteria.
- **implement:** file placement, component composition, framework APIs, utility classes, and reversible choices governed by the existing system.

A request to make an interface “modern,” “premium,” or “better” does not authorize an overhaul. Keep preserve-versus-overhaul on the frontier when it materially changes the destination.

## The map

Read `.agents/artifact-sources.md`. Prepare the canonical low-resolution map for the configured tasks/maps/tickets source. Decisions live once in their tickets or linked durable findings; the map keeps links and one-line gists. If the source is external, draft the map first and obtain explicit authorization immediately before creating it.

```markdown
## Destination

<the observable result this effort is defining>

## Language and locale

<language and locale for user-facing artifacts and handoffs>

## Notes

<domain, standing constraints, specialist lenses, and later skills to consult>

## Decisions so far

- [<closed ticket name>](link) — <one-line gist>

## Not yet specified

<definition fog that cannot yet be stated as a precise question>

## Deferred downstream

- **to-spec:** <specification decision>
- **to-tickets:** <delivery decision>
- **implement:** <local technical decision>

## Out of scope

<work beyond the destination>

## Status

<definition in progress | definition ready>
```

Create a durable map or minimal definition brief. A small clear effort may be definition-ready without child tickets, but a fresh `to-spec` session still needs the durable pointer.

## Decision tickets

Each child holds one definition decision or a tightly coupled packet:

```markdown
## Question

<the decision>

## Why now

<how materially different answers change the definition>
```

Refer to tickets by linked name in human-facing text. Claim before working so concurrent sessions skip claimed work. Use the source's native blocking relationship. The **frontier** is every open, unblocked, unclaimed child.

Ticket types:

- **Research (AFK):** broad **why** evidence from primary sources blocks definition. Store the finding in the configured research source and link it from the ticket.
- **Explore (AFK):** a repository-grounded **how** trace is needed. It may escalate an unresolved rationale question to Research.
- **Prototype (HITL):** a rough runnable or visible artifact is needed to decide behaviour or appearance.
- **Grilling (HITL):** the user must make a definition decision; apply domain modeling when the workspace can retain resolved vocabulary.
- **Task (AFK or HITL):** another result is required before a definition decision can be made.

## Fog and deferral

**Fog of war** is definition work you can see but cannot yet phrase precisely. Resolving a ticket may graduate fog into tickets.

Downstream detail does not belong in fog. `Deferred downstream` is in scope but owned later. `Out of scope` stays outside unless the destination changes.

## Chart the map

1. **Name the destination.** Use localized definition-depth grilling. Establish only language that affects decisions or prevents ambiguity.
2. **Map the frontier.** Work breadth-first across actors, scope, authority, constraints, risks, impacts, and material trade-offs. Assign later detail downstream.
3. **Create the map.** Fill locale, destination, notes, fog, downstream deferrals, exclusions, and status.
4. **Prepare frontier tickets.** Draft tickets and blocking edges. Before creating or changing any external record, show the proposed effects and obtain explicit authorization at that boundary; then create tickets before relations.
5. **Dispatch factual work.** Model-invoke `research` for broad why and use `explore` for how. `research` is not a user entrypoint. Each background worker has one ticket, a bounded question, an owner, and a durable destination. Automatic research does not authorize real-browser automation or external record mutation.
6. **Join before completion.** Wait for every background worker owned by this stage. Record its finding, unresolved question, or blocker and update the map.
7. **Assess readiness.** If no definition decision remains open, mark `definition ready`; otherwise hand off the next frontier owner.

Charting does not implement the destination or silently resolve HITL decisions.

## Work the map

1. Load the map at low resolution.
2. Take the named ticket or first frontier ticket and claim it.
3. Resolve it at definition depth. Broad rationale uses `research`; system behaviour uses `explore`; user decisions use localized grilling.
4. Prepare the durable finding, ticket resolution, and linked gist. Ask for explicit authorization immediately before any external create or update, then apply only the authorized mutations.
5. Update the frontier: graduate precise fog, assign downstream decisions, rule out exclusions, and update invalidated tickets.
6. Wait for all work owned by the stage, then reassess readiness from current state rather than ticket count.

Re-read relevant tracker state before mutation when other sessions may update it concurrently. Authorization must still be current at the effect boundary.

## Session and ownership boundaries

Every transition to another ticket owner or workflow stage starts a fresh session. Background subagents are fresh child sessions; the dispatching stage remains their lifecycle owner and joins all of them before handoff.

A live HITL pause remains in its current session. Ask the smallest coherent question set, make the requested reply the final content, and resume after the reply. A paused response has no `Next step` heading or skill command.

Handoffs use a durable artifact pointer from the configured source. When no artifact exists, use an inline self-contained command brief. Never create a transient handoff file.

## Definition-ready criterion

The map is definition-ready when a fresh `to-spec` session can specify the work without guessing the problem, outcome, actors, user-visible scope, authority, material constraints, or human decisions. Remaining uncertainty has a downstream owner and cannot materially redefine the work.

Open technical questions do not keep the map in progress. An unresolved definition question does.

If `to-spec` later finds a definition gap, it records that gap against this durable artifact and hands back to `wayfinder` in a fresh session. It does not question the user or silently fill the gap.

## Localized handoff

Use the map's language and locale. Confirm all stage-owned background work is complete.

When definition decisions remain, end with the localized equivalent of:

```markdown
## Next step

The definition frontier is still open.

Start a fresh session and run:

`<invoke the next frontier owner using the active client syntax> Continue <map pointer>. Resolve <linked ticket name>.`
```

When definition is ready, end with the localized equivalent of:

```markdown
## Next step

The work is ready for specification. Remaining technical decisions have downstream owners.

Start a fresh session and run:

`<invoke to-spec using the active client syntax> Build the specification from <map pointer>. Follow every link under “Decisions so far”. If definition-level information is missing, record a definition-gap against the map and hand it back to wayfinder in a fresh session.`
```
