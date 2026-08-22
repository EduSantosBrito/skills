# Record mode

Read this branch only when durable research was requested or Wayfinder requires it for a handoff.

## Select the destination

1. Read `.agents/artifact-sources.md` and the convention owner it names for research.
2. Match the repository's existing research layout and naming. If the configured source is local and has no research convention, use `docs/research/<descriptive-slug>.md`.
3. For a local destination, check the chosen path immediately before writing and create a new non-colliding path. If the required local path already exists, obtain explicit authorization before replacing or editing it.
4. For Linear, GitHub, GitLab, or any other external destination, draft the exact proposed record and obtain explicit user authorization immediately before creating or updating it.

Record mode permits one new local research artifact by default. Editing an existing local artifact requires explicit authorization. No mode or invocation authorizes an external mutation: an external create or update requires explicit authorization at its own effect boundary. This mode never authorizes edits to source configuration, related docs, or tickets. The owner—not a background worker—writes the artifact after all workers have returned or been cancelled.

## Write one self-contained record

Use the smallest structure that preserves the evidence:

```markdown
# <finding-oriented title>

**Date:** <YYYY-MM-DD>
**Question:** <bounded question>
**Scope:** <systems, versions, repositories, and time bounds>

## Bottom line

<answer and confidence>

## Direct evidence

<claims with adjacent citations>

## Inferences

<evidence chains and calibrated wording>

## Hypotheses

<live alternatives and tests; omit if none>

## Gaps and contradictions

<unknowns, bounded null results, unavailable sources, disagreements>

## Sources consulted

- <source, query/scope, result or null result, durable citation>

## Change constraints

<Preserve / Change / Avoid / Risk, only when the research informs a change>
```

Use permanent links and pinned versions where available. Distinguish the date of an event from the date a source described it. Quote only the minimum text needed to establish a claim.

After writing, re-read the artifact and verify that it is the only mutation made by this skill, every material claim has a resolvable citation, evidence classes remain distinct, and the conversation reports the exact durable pointer. In `answer` mode there is no artifact to verify because nothing persists.
