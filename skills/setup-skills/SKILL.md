---
name: setup-skills
description: Configure a repository for the Wayfinder-led workflow, including explicit artifact sources and locations, runtime capabilities, triage vocabulary, domain docs, and review integration. Run explicitly before first workflow use.
disable-model-invocation: true
license: MIT
metadata:
  opencode/autoinvoke: false
---

# Setup Skills

Bootstrap repository configuration without installing skills globally. This is an explicit pre-workflow command, not a workflow entrypoint: after bootstrap, every piece of work starts with `wayfinder`.

Resolve this skill's own installed directory through the active client's skill discovery. Resolve the active `wayfinder` provider through the same discovery interface and read its `references/ROUTES.md`; that table is authoritative for route owners, requirements, blockers, and fallbacks. Read [`artifact-sources.md`](artifact-sources.md) and selected convention templates relative to the discovered setup directory. Never look for a `skills/` directory in the consumer repository or infer availability from package contents. A configured repository has a project-specific artifact-source index and approved workflow, domain, issue-tracker, and optional triage guidance.

## 1. Validate and explore

Before asking questions or drafting files:

1. Require capability `skill-provider-discovery`; require the discovered `setup-skills` and `wayfinder` sources, `ROUTES.md`, artifact-source template, and selected convention templates to be contained regular files under their owning provider roots after realpath resolution. Missing discovery or an invalid source blocks setup.
2. Read `ROUTES.md` directly. Validate that each route has an owner or action, every skill and capability ID is syntactically valid, every requirement has a blocker or fallback, and no entry contains a source-repository path or static availability claim. Treat `research`, `to-spec`, and `implement` as blocked when absent, with no upstream fallback; require Hunk `>=0.18.1` and exactly two concurrent background subagents for `code-review`.
3. Inspect remotes, `.git/config`, root `AGENTS.md` or `CLAUDE.md`, `.agents/`, `.gitignore`, domain/context docs, existing artifact directories, monorepo signals, declared local overrides, and declared dependencies.
4. Ask the active client's catalog or discovery interface for every logical skill ID and runtime capability ID cited by `ROUTES.md`. IDs are the required discovery evidence. Also verify this skill's own requirements directly: provider locations can be resolved, packaged sources can be read, and approved project files can be written with contained project-relative paths. Record the winning provider or location when exposed; treat origin, scope, precedence, and overlapping-provider details as optional diagnostics. Do not hard-code client names, global directories, command syntax, or installation layouts.
5. Probe Hunk with `hunk --version` and `hunk skill path`, and confirm whether the runtime can launch exactly two concurrent background subagents. Record missing review capability as a blocker; do not install or invent a fallback.
6. Resolve every route owner and requirement against discovery, applying only the fallback declared in `ROUTES.md`. Mark a route blocked when neither its owner nor fallback resolves; selective installation is never inferred from package contents or persisted as a presence claim.
7. Classify every target as absent, literal-template-identical, generated-from-template, or customized. Never treat a customized `.agents/*`, `AGENTS.md`, or `CLAUDE.md` as safe to replace.

Exploration is complete when every route requirement and every proposed target has a known state. Do not mutate repository files during this step.

## 2. Select sources and locations explicitly

Present repository evidence first. Ask separately, one answer at a time, and record both the source and the concrete location or selector.

### A. Tasks, maps, and tickets

Ask for the system: Linear, GitHub, GitLab, Local, or Other. Then ask for the concrete workspace/repository/project/team/path and convention owner that repository evidence did not establish. This source owns intake, Wayfinder maps, decision tickets, and implementation tickets; it never owns specifications or research merely because the same provider could store them.

Use the matching `issue-tracker-*.md` template. For Linear, the draft set must include `.agents/issue-tracker.md`; use optional `.agents/issue-tracker.local.md` only for non-secret project selectors. For Other, draft one dedicated convention file under `.agents/`.

### B. Specifications

Ask for the source type and exact durable location independently. For a local source, propose an existing project-relative path or `docs/specs/`; never emit an absolute path or a package-relative `skills/` path. For a remote source, identify its dedicated convention owner. Do not silently inherit the task tracker.

### C. Research

Ask for the source type and exact durable location independently. For a local source, propose an existing project-relative path or `docs/research/`; never emit an absolute path or a package-relative `skills/` path. For a remote source, identify its dedicated convention owner. Do not silently inherit either earlier answer.

### D. Domain docs

Ask for the source type and separate domain-context and architecture-decision locations, then whether the repository uses the single-context layout from [`domain.md`](domain.md) or a multi-context layout justified by observed monorepo boundaries. For a single-context local source, propose `CONTEXT.md` and `docs/decisions/`. Local locations are safe project-relative paths and are owned by `.agents/domain.md`.

Render [`artifact-sources.md`](artifact-sources.md) into `.agents/artifact-sources.md` as a thin index with one ownership row for tasks/maps/tickets, specs, research, domain context, and architecture decisions. Replace every placeholder. Each row must name its source type, concrete safe project-relative location or remote selector, one operable convention owner, and a presence contract. Use `optional` when a local path may not exist until its first artifact, `present` when setup observed it, `required` only when the selected source contract requires it, and `n/a` for remote selectors. A convention owner is a generated `.agents/` file or a logical `skill:<id>` resolved by discovery.

## 3. Cross the wizard boundary when required

If a selected provider requires human-only authentication or dashboard work, do not invoke `wizard` inside this setup session. Finish the current phase with a self-contained handoff to a fresh `wizard` session using the active client's syntax. Include the provider, required discoveries, allowed effects, authorization requirements, and the exact information setup needs on return.

The wizard owns only the human procedure. It must:

- request explicit authorization immediately before creating or changing any external record;
- finish with either a durable, non-secret result pointer or an inline self-contained result brief;
- create no transient repository handoff file;
- delete any temporary script from the operating system's temporary directory after success;
- hand off to a fresh `setup-skills` session in resume mode.

On resume, re-read repository status and the result. Do not assume the workspace stayed unchanged. The resumed setup session owns all repository configuration drafts and writes.

## 4. Select optional conventions

When `triage` is available, ask whether to keep the five canonical labels: `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, and `wontfix`. Use [`triage-labels.md`](triage-labels.md) on yes; on no, collect only explicit mappings. Skip triage configuration when that dependency is unavailable.

For Linear, use [`issue-tracker-linear.md`](issue-tracker-linear.md) for public Linear artifact conventions and [`issue-tracker-linear.local.md`](issue-tracker-linear.local.md) as the shape of non-secret local selectors. Keep credentials in the client secret store. The GitHub and GitLab templates keep request-surface support off unless the user explicitly changes it.

## 5. Draft, diff, and approve

Build complete proposed contents for:

- the existing `## Agent skills` block, or the user-selected root guidance file when neither exists;
- `.agents/artifact-sources.md`;
- each selected source-convention file;
- `.agents/workflow.md`, `.agents/domain.md`, and optional `.agents/triage-labels.md`;
- non-secret local provider configuration.

Show the complete draft and a target-by-target diff before writing any file, including absent-file drafts and generated artifact-source content. Ask for explicit approval in the same session. Preserve all surrounding user content. If a target is customized, identify the conflicting regions and require explicit approval for the exact replacement; otherwise block. Never perform an automatic merge whose safety cannot be demonstrated. Do not silently overwrite any `.agents/*`, `AGENTS.md`, or `CLAUDE.md` file.

A temporary backup may exist outside the repository for recovery during this same setup session. It is not a handoff artifact and must not be referenced as durable state.

The approval pause remains in this session. Approval of repository drafts does not authorize external effects.

## 6. Write after approval

Only after the complete draft is approved:

1. update the selected root guidance block in place;
2. write the approved generated artifact-source index and source convention files, including `.agents/issue-tracker.md` when Linear is selected;
3. write `.agents/workflow.md` byte for byte from [`workflow.md`](workflow.md);
4. write `.agents/domain.md` and the approved selected issue-tracker and triage conventions byte for byte from their templates;
5. write provider-local non-secret selectors when approved and add only their declared local path to `.gitignore` when required.

Require byte identity only for files declared as literal copies: the workflow guide, domain guide, selected issue-tracker convention, and selected triage convention. The artifact-source template is a schema with placeholders; its projection must differ after rendering. Use seed templates only for selected branches. Write only portable projections under `.agents/`; do not copy package paths into them. Do not stage, commit, push, install dependencies, or create a transient handoff file.

## 7. Verify and finish

Verify:

1. `ROUTES.md` is readable from the discovered `wayfinder` provider and every cited skill and capability ID is available, resolves its declared fallback, or is explicitly blocked;
2. every packaged source, projected index, YAML file, and relative Markdown link is a regular file contained by its owning root after realpath resolution;
3. discovery includes winning provider or location only when the client exposes it and contains no inferred static presence claim;
4. literal-copy template/projection pairs are byte-identical, while `.agents/artifact-sources.md` contains no template placeholder;
5. the artifact index records explicit, non-overlapping ownership, source types, safe project-relative local locations, presence contracts, and operable convention owners; optional paths may be absent, while present or required paths exist;
6. Linear selection projected `.agents/issue-tracker.md`;
7. required runtime blockers are reported, especially Hunk `>=0.18.1` and exactly two background subagents for `code-review`;
8. optional local configuration, when present, is a contained regular file and contains no credential; its absence does not block a clean clone or CI;
9. customized user content remains preserved;
10. only intended repository files changed.

Report selected sources and locations, discovered skill and capability IDs, any winning-provider or location details the client exposed, blocked routes, and the exact repository state. Setup is complete only when the generated artifact-source index and approved guidance projections exist. Thereafter, workflow work starts with `wayfinder`; rerun this bootstrap only when configuration changes materially.
