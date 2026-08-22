# Agent Skills

[![skills.sh](https://skills.sh/b/EduSantosBrito/skills)](https://skills.sh/EduSantosBrito/skills)

> Heavily opinionated, intentionally small skills for coding agents.

This repository contains ten portable [Agent Skills](https://agentskills.io/). Install all or a selected subset with [skills.sh](https://skills.sh/) in any supported agent CLI.

## Local skills

### Core workflow

#### [`wayfinder`](./skills/wayfinder/SKILL.md)

The only workflow work entrypoint. It classifies the current state, chooses the minimum sufficient route, and owns definition decisions when the destination is still unclear. After repository bootstrap, start every piece of work here; destination skills are owners, not competing routers.

#### [`setup-skills`](./skills/setup-skills/SKILL.md)

Explicitly bootstraps a repository before workflow work begins. It is the declared entrypoint exception, not a competing work entrypoint. It discovers logical skill providers and runtime capabilities through the active client, asks for every artifact source and location, then drafts portable project projections and blockers; it does not install skills globally or silently overwrite customized guidance.

#### [`to-spec`](./skills/to-spec/SKILL.md)

Turns a definition-ready durable artifact into a specification. It does not interview the user or fill definition gaps: it records a `definition-gap` against the source artifact and hands ownership back to Wayfinder in a fresh session.

#### [`implement`](./skills/implement/SKILL.md)

Builds and proves the smallest complete vertical slice. Staging, committing, and pushing are unconditionally outside this owner, including for children and requests made during the stage. Its completion handoff separately enumerates committed-after-fixed-point, staged, unstaged, and untracked state for a fresh `code-review` session, so a working tree does not need a temporary commit.

#### [`code-review`](./skills/code-review/SKILL.md)

Reviews a working tree on exactly two independent axes: Standards and Spec. It has two hard requirements with no fallback: Hunk `>=0.18.1` and runtime support for exactly two concurrent background subagents. The review source is:

```bash
hunk diff <fixed-point-sha> --no-exclude-untracked
```

That source includes committed changes after the fixed point plus staged, unstaged, and untracked files. Missing Hunk, insufficient subagent capacity, a failed reviewer, or a third reviewer blocks the review rather than degrading it to another path.

### Specialists

#### [`research`](./skills/research/SKILL.md)

Model-invoked by an owning workflow decision, rather than used as a user entrypoint, to investigate broad **why** questions across primary sources. `answer` does not persist; `record` persists one finding in the configured research source. Neither invocation nor route selection authorizes an external mutation.

#### [`explore`](./skills/explore/SKILL.md)

Traces **how** a software path works from trigger to observable outcome. It is read-only and repository-grounded. When the trace exposes an unresolved material rationale, it finishes the supported trace and escalates that rationale to `research` in a fresh session.

#### [`create-verification-skill`](./skills/create-verification-skill/SKILL.md)

Creates or refreshes a durable project-local capability to launch, doctor, drive, observe, and clean up one real product endpoint. Wayfinder routes here only when repeatable endpoint proof is missing or stale. It complements `prototype` and `codebase-design`, reads the configured artifact sources, and does not depend on Cursor or Cursor-specific paths and tooling.

#### [`product-design`](./skills/product-design/SKILL.md)

Supplies stage-appropriate product and interface design guidance without replacing workflow ownership. Direct audits are read-only; implementation and review retain their normal owners.

#### [`you-lost-me`](./skills/you-lost-me/SKILL.md)

Re-pitches an explanation that did not land, using the user's language, shared domain vocabulary, and the applicable plain-language standard. It runs only when invoked.

## Upstream dependencies

The skills above are packaged by this repository. The build flow still requires a provider for logical skill ID `to-tickets`. Other routes resolve `codebase-design`, `diagnosing-bugs`, `domain-modeling`, `grilling`, `prototype`, `resolving-merge-conflicts`, `teach`, `to-questionnaire`, `triage`, and `wizard` only when selected; incident response is optional. [`skills/wayfinder/references/ROUTES.md`](./skills/wayfinder/references/ROUTES.md) is the authoritative route, requirement, blocker, and fallback table.

## Way of working

Run `setup-skills` explicitly once per repository as bootstrap, then use `wayfinder` as the single workflow work entrypoint. Workflow owners diagnose missing configuration instead of invoking setup directly. The main build flow is:

```text
wayfinder → to-spec → to-tickets → implement → code-review
```

Every transition to another owner or stage starts a fresh session. A live human-in-the-loop pause stays in the same session and resumes after the answer. Handoffs point to a durable artifact in its configured source; when no durable artifact exists, the command carries a compact self-contained brief inline. The workflow never creates a transient handoff file.

Artifact sources and concrete locations are selected explicitly. In this repository, **tasks, maps, and tickets** live in Linear, **specs** in `docs/specs/`, **research** may be created in `docs/research/`, **domain context** in `CONTEXT.md`, and **architecture decisions** in `docs/decisions/`. [`.agents/artifact-sources.md`](./.agents/artifact-sources.md) is the generated thin ownership index; [`skills/setup-skills/artifact-sources.md`](./skills/setup-skills/artifact-sources.md) is only its placeholder template. Linear setup also projects `.agents/issue-tracker.md`; local source locations are safe paths relative to the consumer project and may be absent when their presence contract is `optional`.

`product-design`, `prototype`, `codebase-design`, `research`, `explore`, and `create-verification-skill` are specialist routes or lenses. They complement the owning stage rather than adding alternate entrypoints. Creating or changing any external record requires explicit authorization at the effect boundary; invoking a skill never implies that authority. `to-tickets` remains upstream.

## Install

Install all local skills into the current project:

```bash
npx skills@latest add EduSantosBrito/skills
```

Install all local skills globally instead:

```bash
npx skills@latest add EduSantosBrito/skills --global
```

Install one skill into the current project with `--skill`:

```bash
npx skills@latest add EduSantosBrito/skills --skill wayfinder
```

Combine `--skill <name>` with `--global` for a global single-skill installation. Valid local names are `wayfinder`, `setup-skills`, `to-spec`, `implement`, `code-review`, `research`, `explore`, `create-verification-skill`, `product-design`, and `you-lost-me`.

The installer asks which supported agent CLIs should receive the selected skills. Restart or reload the agent after installation, then use that client's documented invocation syntax. During bootstrap, `setup-skills` discovers the skill and capability IDs actually available to that client, records a winning provider or location when exposed, and treats origin, scope, precedence, and overlaps as optional diagnostics. A route blocks only when a required owner or capability ID is absent and the fallback declared in `ROUTES.md` does not resolve. A selective installation never becomes a static skill-presence flag in project configuration.

## Configure a repository

Start a fresh session and invoke `setup-skills` using the active client's syntax. It:

- reads the active `wayfinder` provider's `ROUTES.md` and validates every cited skill and capability directly against client discovery;
- probes Hunk `>=0.18.1` and exactly two concurrent background subagents, reporting review blockers without installing a fallback;
- asks independently for task, specification, research, domain-context, and architecture-decision sources and locations;
- renders `.agents/artifact-sources.md` for the project and projects the approved workflow, domain, issue-tracker, optional triage, and non-secret local selector files;
- shows complete drafts and diffs before writing, requiring explicit approval for customized targets.

Bootstrap does not install skills globally. After it completes, start every piece of workflow work with `wayfinder` in a fresh session.

## Repository structure

Each skill is a self-contained directory:

```text
skills/
  <skill-name>/
    SKILL.md
    agents/          # Optional agent-specific metadata
    references/      # Optional supporting documentation
```

Only `SKILL.md` is required by the portable skill format. This repository also supplies `agents/openai.yaml` for every local skill.

## Credits and provenance

The workflow is adapted from and informed by [Matt Pocock's skills](https://github.com/mattpocock/skills) and Lauren Tan's pstack skills in [Cursor plugins](https://github.com/cursor/plugins/tree/main/pstack). Local source metadata pins the relevant revisions. `research` combines Matt's research workflow with pstack's broad `why` investigation; `explore` is informed by pstack's `how`; `code-review` combines Matt's two-axis review with pstack interrogation ideas; and `create-verification-skill` ports pstack's create/maintain verification contracts without retaining a Cursor runtime dependency.

`you-lost-me` adapts Matt Pocock's `wait-what`. `wayfinder`, `to-spec`, `implement`, `setup-skills`, and `code-review` adapt or extend Matt's engineering workflows. The local editorial structure follows Matt's `writing-for-agents` guidance.

`product-design` consolidates MIT-licensed material from [Emil Kowalski's skills](https://github.com/emilkowalski/skills), custom-licensed [Revenue-Centric Design](https://github.com/heliocosta-dev/revenue-centric-design), and selected MIT-licensed ideas from [Taste Skill](https://github.com/Leonxlnx/taste-skill). See each skill's frontmatter, `SOURCES.md`, and bundled license files for exact attribution and terms.

## License

The repository's original material is [MIT](./LICENSE). Adapted portions retain their upstream notices. `product-design` contains material under separate terms; its [`SOURCES.md`](./skills/product-design/SOURCES.md) and bundled license files govern those portions. Do not represent the complete `product-design` directory as MIT-only.
