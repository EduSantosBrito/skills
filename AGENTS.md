## Agent skills

### Workflow

After bootstrap, start every piece of work with the `wayfinder` skill, using the active client's invocation syntax. `setup-skills` is the sole bootstrap exception before the workflow is configured. See `.agents/workflow.md`.

### Artifact sources

Tasks, maps, and tickets live in Linear. Specs live in `docs/specs/`, research in `docs/research/`, domain context in `CONTEXT.md`, and architecture decisions in `docs/decisions/`. Read `.agents/artifact-sources.md` for locations, presence contracts, and convention pointers.

### Triage labels

Use the five canonical labels: `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, and `wontfix`. See `.agents/triage-labels.md`.

### Domain docs

This repository uses a single-context layout. See `.agents/domain.md`.
