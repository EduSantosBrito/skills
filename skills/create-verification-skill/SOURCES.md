# Sources and license

## pstack verification skills

- Repository: <https://github.com/cursor/plugins/tree/46125561306434d8a1d7745d540d8932ab0cd2a2/pstack>
- Revision: `46125561306434d8a1d7745d540d8932ab0cd2a2`
- Source files: `skills/create-verification-skill/SKILL.md` and `skills/maintain-verification-skill/SKILL.md`.
- Adaptation: preserves the Launch, Doctor, Drive, Evidence, Cleanup, feature-map, live-proof, and drift-triage contracts. It replaces Cursor-specific paths and tooling with repository discovery, folds maintenance into the same Wayfinder-owned skill, integrates the repository's artifact-source index, and requires explicit authorization for real-browser driving and external effects.
- License: MIT. The complete upstream notice is preserved in `LICENSE-pstack`.

## Editorial references

- Local Wayfinder workflow and artifact-source conventions at revision time: `.agents/workflow.md`, `.agents/artifact-sources.md`, `skills/wayfinder/SKILL.md`, and `skills/wayfinder/references/ROUTES.md`.
- Matt Pocock's `prototype`, `codebase-design`, `tdd`, `diagnosing-bugs`, and `writing-for-agents` skills informed ownership distinctions, seam vocabulary, and progressive disclosure. No source file from those skills is copied here.

## Adaptation record

- Adapted: 2026-08-22
- Intended runtime: portable Agent Skills installations with a Wayfinder-led workflow
- Invocation: user-invoked destination routed only by Wayfinder when repeatable endpoint proof is missing or stale
