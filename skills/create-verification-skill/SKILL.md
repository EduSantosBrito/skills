---
name: create-verification-skill
description: Create or refresh a durable, project-local capability for driving and proving one real product endpoint.
argument-hint: "<endpoint capability or existing verification path>"
disable-model-invocation: true
license: MIT
metadata:
  opencode/autoinvoke: false
  adapted-from: "cursor/plugins pstack create-verification-skill and maintain-verification-skill"
  source-commit: "46125561306434d8a1d7745d540d8932ab0cd2a2"
---

# Create Verification Skill

This is an internal Wayfinder destination, not a public entrypoint. Use it only after Wayfinder finds that repeatable endpoint proof is missing or stale. Existing, current verification remains the source of truth.

## Ownership

Create a **durable external seam**: a project-local skill that can launch, health-check, drive, observe, and clean up the product surface a user or consumer actually reaches.

- `prototype` creates a throwaway artifact to reduce one uncertainty.
- `codebase-design` decides a module's interface and seam.
- `tdd` proves behaviour at an agreed local seam.
- `diagnosing-bugs` builds a red-capable loop for one defect.
- This skill creates repeatable capability for proving a real external endpoint. It does not replace those owners.

## 1. Ground the capability

Read repository guidance and `.agents/artifact-sources.md` when present, then follow its convention pointers. Tasks and maps prioritize the feature map; specs and docs supply intended behaviour and acceptance criteria. They orient verification but cannot prove success: only an observation at the real endpoint can.

Interview the repository before asking the user:

1. Identify the primary user or consumer surface and the requested endpoint.
2. Discover the project's local skill convention, launch commands, isolation controls, existing harnesses, fixtures, and evidence conventions.
3. Prefer a current existing harness. Add tooling only for a concrete uncovered operation, behind the generated skill's interface.
4. Select **create** when capability is absent. When an existing capability is stale, read [`references/MAINTENANCE.md`](references/MAINTENANCE.md) and run **maintain** under this same owner.
5. Stop when current verification already proves the endpoint; report its path and invocation instead of creating a parallel route.

Read only the relevant branch in [`references/SURFACES.md`](references/SURFACES.md) for web, API, CLI, library, desktop, or mobile. If no project-local skill root is established, ask the user to select a path recognized by their active client rather than choosing a client-specific directory.

Real-browser driving and any external effect require explicit authorization. Finish all independent discovery first, then ask once with the exact surface and effects. Without required authorization, leave an honest blocker, not an unexecuted deliverable.

## 2. Build the project-local skill

Keep the generated skill behind the repository's established project-local skill and harness conventions. It must contain these exact operational sections:

- **Launch** — exact isolated startup/build command, readiness signal, instance identity, owner, and teardown handle.
- **Doctor** — one read-only check that proves this is the intended build and instance and is worth driving.
- **Drive** — literal user-path recipes using stable handles from the repository.
- **Evidence** — capture the action, resulting endpoint state, and material side effects in a named location; redact secrets and personal data.
- **Cleanup** — stop only instances the run owns and remove scratch state while preserving evidence.

Make effects, blocking, suspension, and remote I/O visible. Never kill by broad process name or drive a shared instance whose ownership is uncertain. Helpers must be deterministic, executable, documented at their call site, and narrower than the product; otherwise use literal existing commands.

## 3. Seed a small feature map

Read [`references/FEATURE-MAP.md`](references/FEATURE-MAP.md). Map only the 3–5 highest-priority user-visible features needed to make the endpoint capability useful. Every mapped proof starts from the user or consumer surface and ends at an observable outcome; internal setters, private imports, test-only routes, and database inspection alone are proxies.

## 4. Prove one feature end to end

Run the generated instructions, not an improvised substitute:

1. **Launch** an isolated instance or consumer run.
2. Run **Doctor** and require a healthy, correctly identified target.
3. **Drive** one mapped feature through its real endpoint.
4. Capture **Evidence** of the action, result, and material side effects.
5. Run **Cleanup**, including after every failed attempt.
6. Confirm after cleanup that the evidence still exists and no owned process or scratch state remains.

Fix the capability and repeat until this sequence passes. A skill that has not completed it is a draft. A browser-only or effectful path without authorization is blocked, not passed.

## 5. Finish

Check generated frontmatter, relative links, feature index, helper invocations and permissions, diff scope, and cleanup ownership. Re-read the final diff. Do not install, commit, publish, open a PR, or exercise an external effect without explicit authorization.

Report separately:

- what the skill's construction guarantees;
- the exact feature and endpoint actually observed, with evidence paths;
- cleanup results and evidence survival;
- unverified paths, assumptions, and residual risk.
