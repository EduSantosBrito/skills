---
name: setup-skills
description: Configure a repository for the Wayfinder-led workflow, including its issue tracker, triage vocabulary, domain docs, workflow contract, and Hunk review integration. Run once before first use.
disable-model-invocation: true
---

# Setup Skills

Scaffold the per-repo configuration that the Wayfinder-led workflow assumes:

- **Workflow** — Wayfinder as the universal entry point, stage depth, automatic research, localized handoffs, and custom-skill priority
- **Issue tracker** — where maps, decisions, specs, and tickets live
- **Triage labels** — the strings used for the five canonical triage roles
- **Domain docs** — where `CONTEXT.md` and ADRs live, and the consumer rules for reading them
- **Review integration** — Hunk as the interface for `code-review`

This is a prompt-driven skill, not a deterministic script. Explore, present what you found, confirm with the user, then write.

## Process

### 1. Explore

Look at the current repo to understand its starting state. Read whatever exists; don't assume:

- `git remote -v` and `.git/config` — is this a GitHub repo? Which one?
- `AGENTS.md` and `CLAUDE.md` at the repo root — does either exist? Is there already an `## Agent skills` section in either?
- `CONTEXT.md` and `CONTEXT-MAP.md` at the repo root
- `docs/adr/` and any `src/*/docs/adr/` directories
- `.agents/` — does this skill's prior output already exist, including `workflow.md` and an optional gitignored `issue-tracker.local.md`?
- `.scratch/` — sign that a local-markdown issue tracker convention is already in use
- Are the custom `wayfinder`, `explore`, `you-lost-me`, `product-design`, and `code-review` skills available, and do they take precedence over conflicting global skills?
- Run `hunk skill path` to verify that the Hunk review skill is available; record a missing command as a setup gap rather than installing it silently.
- Is the `triage` skill installed? (a `triage` skill folder alongside this one, or `triage` in your available skills.) This decides whether Section B runs at all.
- Monorepo signals — a `pnpm-workspace.yaml`, a `workspaces` field in `package.json`, or a populated `packages/*` with its own `src/`. Present only in a genuinely large multi-package repo; their absence means single-context, which is almost every repo.

### 2. Present findings and ask

Summarise what's present and what's missing. Then take the sections in order — one section, one answer, then the next.

Lead each section with the recommended answer so the user can accept it in a word. Give a one-line explainer only when the choice genuinely branches; skip the section entirely when exploration already settled it (Section B when `triage` isn't installed, Section C when there's no monorepo).

**Section A — Issue tracker.**

> Explainer: The "issue tracker" is where issues live for this repo. Skills like `to-tickets`, `triage`, and `to-spec` read from and write to it — they need to know whether to call `gh issue create`, write a markdown file under `.scratch/`, or follow some other workflow you describe. Pick the place you actually track work for this repo.

Default posture: these skills were designed for GitHub. If a `git remote` points at GitHub, propose that. If a `git remote` points at GitLab (`gitlab.com` or a self-hosted host), propose GitLab. Otherwise (or if the user prefers), offer:

- **GitHub** — issues live in the repo's GitHub Issues (uses the `gh` CLI)
- **GitLab** — issues live in the repo's GitLab Issues (uses the [`glab`](https://gitlab.com/gitlab-org/cli) CLI)
- **Linear** — issues live in a configured Linear workspace and team; use the official Linear MCP server by default
- **Local markdown** — issues live as files under `.scratch/<feature>/` in this repo (good for solo projects or repos without a remote)
- **Other** (Jira, Shortcut, etc.) — ask the user to describe the workflow in one paragraph; the skill will record it as freeform prose

For Linear, read [issue-tracker-linear.md](./issue-tracker-linear.md), then invoke `/wizard` to generate a **temporary** setup wizard in the operating system's temp directory. The wizard guides the human through the official MCP OAuth flow, workspace/team/project selection, capability verification, and any approved label or state setup. After selecting the team, derive a proposed project name from the repository, list the team's active existing projects, and offer three explicit choices: create the proposed project, use an existing project, or use no project. Ask before creating a project. Prefer `https://mcp.linear.app/mcp`; use a scoped personal API key and `https://api.linear.app/graphql` only when the current client cannot use the required MCP operation. Keep credentials out of repository docs and the generated script, verify the configured access, then delete the wizard. Do not commit it.

Record the choice in `.agents/issue-tracker.md`. For Linear, keep public conventions there and write concrete workspace, team, project, actor, state IDs, and capability results to `.agents/issue-tracker.local.md`; add only that local file to `.gitignore`. Keep credentials in the client's secret store, never in either file. The GitHub and GitLab templates carry a "PRs as a request surface" flag, defaulted **off** — leave it off and don't raise it; a user who wants external PRs in the triage queue can flip the flag in the file later.

**Section B — Triage label vocabulary.** Skip this section entirely if the `triage` skill isn't installed (exploration told you) — an uninstalled skill needs no labels.

If it is installed, ask exactly one question:

> Do you want to keep the default triage labels? (recommended: **yes**)

The defaults are the five canonical roles, each label string equal to its name: `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`. On **yes**, write them as-is. Only if the user says no — usually because their tracker already uses other names (e.g. `bug:triage` for `needs-triage`) — collect the overrides so `triage` applies existing labels instead of creating duplicates.

**Section C — Domain docs.** Default to **single-context** — one `CONTEXT.md` + `docs/adr/` at the repo root. This fits almost every repo; write it without asking.

Offer **multi-context** — a root `CONTEXT-MAP.md` pointing to per-context `CONTEXT.md` files — only when exploration found monorepo signals. Then confirm which layout they want.

### 3. Confirm and edit

Show the user a draft of:

- The `## Agent skills` block to add to whichever of `CLAUDE.md` / `AGENTS.md` is being edited (see step 4 for selection rules)
- The contents of `.agents/workflow.md`, `.agents/issue-tracker.md`, `.agents/domain.md`, and `.agents/triage-labels.md` (the last only when `triage` is installed)
- For Linear, the concrete non-secret configuration to write to gitignored `.agents/issue-tracker.local.md`

Let them edit before writing.

### 4. Write

**Pick the file to edit:**

- If `CLAUDE.md` exists, edit it.
- Else if `AGENTS.md` exists, edit it.
- If neither exists, ask the user which one to create — don't pick for them.

Never create `AGENTS.md` when `CLAUDE.md` already exists (or vice versa) — always edit the one that's already there.

If an `## Agent skills` block already exists in the chosen file, update its contents in-place rather than appending a duplicate. Don't overwrite user edits to the surrounding sections.

The block:

```markdown
## Agent skills

### Workflow

Start every piece of work with the `wayfinder` skill, using the active client's invocation syntax. See `.agents/workflow.md`.

### Issue tracker

[one-line summary of where issues are tracked]. See `.agents/issue-tracker.md`.

### Triage labels

[one-line summary of the label vocabulary]. See `.agents/triage-labels.md`.

### Domain docs

[one-line summary of layout — "single-context" or "multi-context"]. See `.agents/domain.md`.
```

Include the `### Triage labels` sub-block, and write `.agents/triage-labels.md`, only when `triage` is installed and Section B ran. When it isn't, both are omitted.

Then write the docs files using the seed templates in this skill folder as a starting point:

- [workflow.md](./workflow.md) — Wayfinder-led workflow, stage ownership, handoffs, research, and review integration
- [issue-tracker-github.md](./issue-tracker-github.md) — GitHub issue tracker
- [issue-tracker-gitlab.md](./issue-tracker-gitlab.md) — GitLab issue tracker
- [issue-tracker-linear.md](./issue-tracker-linear.md) — public Linear conventions through official MCP with GraphQL fallback
- [issue-tracker-linear.local.md](./issue-tracker-linear.local.md) — gitignored concrete Linear identifiers and verified capabilities
- [issue-tracker-local.md](./issue-tracker-local.md) — local-markdown issue tracker
- [triage-labels.md](./triage-labels.md) — label mapping (only if `triage` is installed)
- [domain.md](./domain.md) — domain doc consumer rules + layout

For Linear, write both tracker files and add the exact path `.agents/issue-tracker.local.md` to `.gitignore`; keep the rest of `.agents/` versioned.

For "other" issue trackers, write `.agents/issue-tracker.md` from scratch using the user's description.

### 5. Done

Tell the user the setup is complete and which skills will now read from these files. Confirm whether Hunk was found and that custom skills take precedence in the configured installation. Mention they can edit `.agents/*.md` directly later — re-running this skill is only necessary when the tracker, workflow contract, review integration, or domain layout changes materially.
