# Full wayfinding

Adapted from Matt Pocock's [`wayfinder`](https://github.com/mattpocock/skills/blob/84fdeffd12f2ee307994d1eb6feb48173b6e0502/skills/engineering/wayfinder/SKILL.md) at commit `84fdeffd12f2ee307994d1eb6feb48173b6e0502`.

Use this branch when the route from a loose idea to a durable specification is obscured by definition decisions. It charts a shared map of **decision tickets** and resolves the definition frontier. It produces decisions, not implementation deliverables.

## Definition depth

Wayfinding may go as deep as necessary into:

- the problem and desired outcome;
- actors and shared domain language;
- observable scope and exclusions;
- authority and human decisions;
- constraints, trade-offs, material risks, and impacts;
- decisions whose alternatives would materially change the specification.

Apply the stage-ownership contract in [`ROUTES.md`](ROUTES.md). A question belongs in the definition frontier when materially different answers would change the destination, user-visible scope, authority, acceptance, material risk, or a costly-to-reverse commitment. Otherwise put it in `Deferred downstream` with its owner.

### Product-design decisions

When the destination changes a user-facing experience, record `product-design` as a specialist lens in the map's `Notes`. Keep these decisions at their owning depth:

- **Wayfinder:** audience, valuable outcome, journey scope, experience authority, protected redesign contracts, and costly-to-reverse brand or trust decisions.
- **Prototype:** visual, interaction, motion, or density alternatives that must be experienced to resolve one decision.
- **to-spec:** hierarchy, behavior, states, responsive rules, accessibility, recovery, content contracts, and validation criteria.
- **implement:** file placement, component composition, framework APIs, utility classes, and reversible choices governed by the existing system.

A request to make an interface “modern,” “premium,” or “better” does not authorize a visual overhaul. When preserve and overhaul are materially different destinations, keep that decision on the definition frontier.

## The map

The map is the canonical low-resolution index on the configured issue tracker. Decisions live once, in their tickets; the map links and gists them.

```markdown
## Destination

<the observable result this effort is defining>

## Language and locale

<inferred language and locale for every user-facing artifact and handoff>

## Notes

<domain, standing constraints, specialist lenses such as `product-design`, and skills later sessions should consult>

## Decisions so far

- [<closed ticket name>](link) — <one-line gist>

## Not yet specified

<definition fog that is in scope but cannot yet be stated as a precise question>

## Deferred downstream

- **to-spec:** <specification decision>
- **to-tickets:** <delivery decision>
- **implement:** <local technical decision>

## Out of scope

<work beyond the destination>

## Status

<definition in progress | definition ready>
```

Always create a durable map or minimal definition brief. A small clear effort may be definition-ready immediately and need no child tickets, but a fresh `/to-spec` session still needs a source.

## Decision tickets

Each child issue carries one definition decision or a tightly coupled decision packet that must be answered together:

```markdown
## Question

<the decision>

## Why now

<how materially different answers would change the definition>
```

Refer to tickets by linked name in human-facing text, never by bare identifier. Claim a ticket before working it so concurrent sessions skip it. Use the tracker's native blocking relationship; the **frontier** is every open, unblocked, unclaimed child.

Use the original ticket types:

- **Research (AFK):** a fact from primary sources blocks a definition decision.
- **Prototype (HITL):** a rough runnable or visible artifact is needed to decide how something should behave or look.
- **Grilling (HITL):** the user must make a decision; invoke grilling and domain modeling together where a working directory can retain the vocabulary.
- **Task (AFK or HITL):** work must be completed before a definition decision can be made.

## Fog and deferral

**Fog of war** is definition work you can see coming but cannot yet phrase as a precise question. Resolving a ticket may graduate fog into tickets.

Do not keep downstream detail in the fog. `Deferred downstream` is in scope but owned by a later stage. `Out of scope` is beyond the destination and does not graduate unless the destination changes.

## Chart the map

1. **Name the destination.** Use localized, definition-scoped grilling. Establish common language with domain modeling; retain only terms that affect decisions or prevent ambiguity.
2. **Map the definition frontier.** Grill breadth-first across actors, scope, authority, constraints, risks, impacts, and material trade-offs. Assign specification and implementation detail downstream as soon as it is recognized.
3. **Create the map or minimal brief.** Fill the locale, destination, notes, fog, downstream deferrals, exclusions, and status.
4. **Create precise frontier tickets.** Create tickets first, then wire blocking edges once identifiers exist.
5. **Dispatch every research ticket automatically.** Research primary sources in parallel and attach durable, cited findings to the ticket or repository convention. Automatic research does not authorize Selenium, Chrome, Playwright, Puppeteer, browser-use, or another real browser; obtain explicit authorization before using one.
6. **Assess definition readiness.** If no definition decision remains open, mark the map `definition ready`; otherwise stop after charting and hand off the next frontier decision.

Charting does not implement the destination or silently resolve HITL decisions.

## Work the map

1. Load the map at low resolution rather than fetching every ticket.
2. Take the named ticket or the first frontier ticket and claim it.
3. Resolve it at definition depth. Zoom into linked decisions only as needed. Facts trigger automatic research; user decisions trigger localized grilling. A tightly coupled decision packet may resolve together.
4. Post the resolution, close the ticket, and append one linked gist to `Decisions so far`.
5. Update the frontier: graduate newly precise definition fog, assign downstream decisions, rule exclusions out of scope, and update or remove invalidated tickets.
6. Reassess readiness from the current state rather than from ticket count.

Other sessions may update the tracker concurrently; re-read relevant state before mutating it.

## Definition-ready criterion

The map is definition-ready when a fresh `to-spec` session can specify the work without guessing the problem, outcome, actors, user-visible scope, authority, material constraints, or human decisions. Remaining uncertainty must be assigned to a downstream owner and must not be capable of materially redefining the work.

Open technical questions do not keep the map in progress. An unresolved definition question does.

## Localized handoff

Use the map's language and locale.

While definition decisions remain, end with the localized equivalent of:

```markdown
## Next step

The definition frontier is still open.

Start a fresh session and run:

`<invoke wayfinder using the active client syntax> Continue <map-url>. Take the next unblocked definition decision.`
```

When definition is ready, end with the localized equivalent of:

```markdown
## Next step

The work is ready for specification. Remaining technical decisions have downstream owners.

Start a fresh session and run:

`<invoke to-spec using the active client syntax> Build the specification from <map-url>. Follow every link under “Decisions so far”. If specification-level information is missing, run a mini grilling session at specification depth; return definition gaps to wayfinder.`
```
