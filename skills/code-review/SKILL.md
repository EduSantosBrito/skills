---
name: code-review
description: Review a working tree in Hunk on independent Standards and Spec axes.
disable-model-invocation: true
license: MIT
metadata:
  opencode/autoinvoke: false
  adapted-from: "mattpocock/skills code-review"
  source-commit: "84fdeffd12f2ee307994d1eb6feb48173b6e0502"
  informed-by: "cursor/plugins pstack interrogate"
  pstack-source: "https://github.com/cursor/plugins/blob/46125561306434d8a1d7745d540d8932ab0cd2a2/pstack/skills/interrogate/SKILL.md"
  pstack-source-license: "MIT"
---

This is a routed workflow stage, not a competing workflow entrypoint. Enter it when `wayfinder` routes a ready change to review; it never edits, stages, commits, or auto-fixes source code.

Review the working tree against a fixed point the user supplies on exactly two axes:

- **Standards** — does the code conform to this repo's documented coding standards?
- **Spec** — does the code faithfully implement the originating issue / spec?

The axes run in exactly two independent background subagents. Hunk `0.18.1` or newer and both background subagents are hard requirements. Missing either requirement blocks the review; there is no serial, single-agent, or non-Hunk fallback.

Require `.agents/artifact-sources.md` and every convention file needed by its selected artifact sources. If configuration is missing or invalid, stop with a diagnostic that names the missing files and explains that explicit repository bootstrap must happen in a separate session. Do not invoke `setup-skills` from review.

## Process

### 1. Fail-fast preflight

Treat the supplied fixed point as untrusted input. If none was supplied, ask for one; do not infer it.

Before discovering standards or spec:

1. Parse the candidate without running Git. Accept only either an ASCII hexadecimal SHA of 7–40 characters or a ref matching `[A-Za-z0-9._/-]+`. Reject every candidate that starts with `-`, contains whitespace, `..`, `@{`, or any character outside that allowlist. Values such as `HEAD~5`, shell syntax, option-like strings, and reflog expressions are invalid.
2. Resolve the accepted candidate exactly once as a commit. Prefer a structured argv API with arguments equivalent to `git`, `rev-parse`, `--verify`, `--end-of-options`, and `<candidate>^{commit}`. If a shell is unavoidable, pass the constructed candidate as one safely quoted argument; never interpolate raw text into a command.
3. Require successful output containing exactly one lowercase value matching `[0-9a-f]{40}`. The `^{commit}` peel both verifies that the object exists and that it is a commit. Store that full SHA as the immutable fixed point and discard the candidate for command construction.
4. From this point onward, use only the stored 40-character SHA anywhere the fixed point appears in Git or Hunk arguments. Never re-resolve the original text.
5. Run `hunk --version`; require semver `>=0.18.1`.
6. Run `hunk skill path`, read the returned `SKILL.md`, and follow its session workflow throughout the review.
7. Confirm the runtime can launch two independent background subagents concurrently.

Stop immediately with the failed prerequisite when any check fails. Do not substitute an interactive Hunk command, a serial review, or an owner-authored axis.

### 2. Load the working-tree review

The review source is exactly:

```bash
hunk diff <fixed-point-sha> --no-exclude-untracked
```

The user runs that interactive command in their terminal; the agent controls it only through `hunk session *`. This source compares the fixed point directly with the current working tree and therefore includes committed changes after the fixed point, staged changes, unstaged changes, and untracked files without requiring a new commit. Ignored files are outside the review; never add them explicitly.

Resolve the live Hunk session as directed by the loaded Hunk skill. If none exists, ask the user to launch the command above in the repository and stop. If multiple live sessions match, require the user to provide a session ID; use that ID for every subsequent session command.

Reload the selected session with the equivalent non-interactive source, then inspect file and hunk structure before requesting patches:

```bash
hunk session reload --repo . -- diff <fixed-point-sha> --no-exclude-untracked
hunk session review --repo . --json
```

With multiple sessions, replace `--repo .` with the required `<session-id>`. Use `--include-patch` only for files or hunks the review needs. The reloaded review model—not `git diff` alone—is the non-empty check because it also accounts for untracked files. Fail before spawning reviewers when the review contains no files.

Record the full fixed-point SHA, `git log <fixed-point-sha>..HEAD --oneline`, exact session selector, and reviewed file/hunk inventory once. Both agents receive that immutable scope. If the Hunk source does not match that SHA or its file/hunk inventory changes before dispatch, stop and establish a new review rather than widening scope silently.

### 3. Identify the spec source

Look for the originating spec, in this order:

1. Issue references in the commit messages (`#123`, `Closes #45`, GitLab `!67`, etc.) — fetch via the workflow in `.agents/issue-tracker.md`.
2. A path the user passed as an argument.
3. A spec file in the configured specification location matching the changed path or feature described by durable evidence.
4. A spec or acceptance criteria supplied in the conversation.

If nothing is found, set the source status to exactly `no spec available`. This does not remove or replace the Spec agent.

### 4. Identify the standards sources

Anything in the repo that documents how code should be written, such as `CODING_STANDARDS.md` or `CONTRIBUTING.md`.

On top of whatever the repo documents, the Standards axis always carries the **smell baseline** below — a fixed set of Fowler code smells (_Refactoring_, ch.3) that applies even when a repo documents nothing. Two rules bind it:

- **The repo overrides.** A documented repo standard always wins; where it endorses something the baseline would flag, suppress the smell.
- **Always a judgement call.** Each smell is a labelled heuristic ("possible Feature Envy"), never a hard violation — and, like any standard here, skip anything tooling already enforces.

Each smell reads *what it is* → *how to fix*; match it against the diff:

- **Mysterious Name** — a function, variable, or type whose name doesn't reveal what it does or holds. → rename it; if no honest name comes, the design's murky.
- **Duplicated Code** — the same logic shape appears in more than one hunk or file in the change. → extract the shared shape, call it from both.
- **Feature Envy** — a method that reaches into another object's data more than its own. → move the method onto the data it envies.
- **Data Clumps** — the same few fields or params keep travelling together (a type wanting to be born). → bundle them into one type, pass that.
- **Primitive Obsession** — a primitive or string standing in for a domain concept that deserves its own type. → give the concept its own small type.
- **Repeated Switches** — the same `switch`/`if`-cascade on the same type recurs across the change. → replace with polymorphism, or one map both sites share.
- **Shotgun Surgery** — one logical change forces scattered edits across many files in the diff. → gather what changes together into one module.
- **Divergent Change** — one file or module is edited for several unrelated reasons. → split so each module changes for one reason.
- **Speculative Generality** — abstraction, parameters, or hooks added for needs the spec doesn't have. → delete it; inline back until a real need shows.
- **Message Chains** — long `a.b().c().d()` navigation the caller shouldn't depend on. → hide the walk behind one method on the first object.
- **Middle Man** — a class or function that mostly just delegates onward. → cut it, call the real target direct.
- **Refused Bequest** — a subclass or implementer that ignores or overrides most of what it inherits. → drop the inheritance, use composition.

### 5. Spawn exactly two background subagents

Launch Standards and Spec concurrently as background work. They share no mutable state, do not see each other's output, and do not edit source or publish comments. Spawn no third reviewer.

If either agent cannot launch or complete, stop with the blocker. Do not publish a partial review or let the owner replace the missing axis.

**Standards sub-agent prompt** — include:

- The fixed point, commit list, reviewed inventory, and resolved Hunk session selector.
- The instruction: "Run `hunk skill path`, load the returned Hunk skill, and inspect the live review with `hunk session review`; request patch text only as needed."
- The list of standards-source files you found in step 4, **plus the smell baseline from step 4** pasted in full — the sub-agent has no other access to it.
- The brief: "Report—per file/hunk where relevant—(a) every place the diff violates a documented standard: cite the standard (file + rule); and (b) any baseline smell: name it and cite the changed lines. Distinguish hard violations from judgement calls; documented repo standards override the baseline. Skip anything tooling enforces. Return evidence, not a claim that you reviewed it. Under 400 words."

**Spec sub-agent prompt** — include:

- The fixed point, commit list, reviewed inventory, and resolved Hunk session selector.
- The instruction: "Run `hunk skill path`, load the returned Hunk skill, and inspect the live review with `hunk session review`; request patch text only as needed."
- The path or fetched contents of the spec, or the exact source status `no spec available`.
- When a spec exists, the brief: "Report: (a) requirements missing or partial; (b) behavior not requested; (c) requirements whose implementation is wrong. Cite the spec and changed lines for every finding. Return evidence, not a claim that you reviewed it. Under 400 words."
- When no spec exists, the brief: "Inspect the assigned review scope, then report exactly `no spec available`; do not infer requirements from code shape or replace the Spec axis with a general review."

### 6. Verify and publish

Wait for both agents. A subagent report is a lead, not proof: use the Hunk review model and cited standards/spec sources to verify every finding's changed-line target, quoted rule or requirement, and consequence. Reject unsupported findings.

Keep `## Standards` and `## Spec` separate. Deduplicate repeated descriptions within their originating axis without voting, consensus scoring, or reranking. Preserve a finding on both axes when it independently violates both contracts; do not merge the rationales.

Turn every verified, actionable, location-specific finding into a focused Hunk comment labelled by its originating axis. Validate and publish all comments in one `hunk session comment apply <session-id> --stdin` batch (or the single-session `--repo .` equivalent). Comments explain the violated contract and consequence; they do not prescribe an auto-fix. Keep findings without a valid changed-line target in the report instead of forcing an inline note.

Report both axes side by side, including the formal `no spec available` result when applicable. End with finding counts per axis and the number of Hunk comments published. Do not modify source, stage files, commit, or apply reviewer suggestions.

## Why two axes

A change can pass one axis and fail the other:

- Code that follows every standard but implements the wrong thing → **Standards pass, Spec fail.**
- Code that does exactly what the issue asked but breaks the project's conventions → **Spec pass, Standards fail.**

Reporting them separately stops one axis from masking the other.
