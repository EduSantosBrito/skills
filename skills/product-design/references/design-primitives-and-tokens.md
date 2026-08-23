# Design Primitives and Tokens

## Scope

Use this reference when choosing or defining design tokens, spacing or type scales, color roles, radius and shadow vocabularies, or auditing hard-coded primitive values. It covers the value layer beneath components.

- For component contracts, states, and visual-craft principles, use `foundations.md`.
- For motion timing and easing values, `motion-and-interaction.md` is authoritative.
- For dependency choices, use `ui-library-selection.md`.

Treat every concrete value here as a candidate starting point. An installed design system outranks these defaults; extend it through its own contribution path rather than around it.

## Tokens own durable decisions

A token earns existence when a value is a deliberate decision reused across owners — not when two elements merely happen to match. Three tiers:

| Tier | Example | Consumed by |
| --- | --- | --- |
| **Primitive (global)** | `--blue-500`, `--size-4` | Semantic tokens and generators only |
| **Semantic (alias)** | `--color-accent`, `--space-inset`, `--text-body-size` | Components |
| **Component** | `--button-padding-x` | One component |

Rules:

- Components consume semantic tokens, never raw primitives; retheming then edits one tier.
- Name semantics by role and intent (`surface-raised`, `control-danger`), never by resolved value (`light-blue`).
- Every new token names its durable decision and its owners. A value used once stays local.
- The W3C Design Tokens Community Group format — typed groups, `$value` and `$type`, `{group.reference}` aliases — is the interoperability reference; verify the current spec version before importing or exporting token files.

## Spacing

- Pick one base step (4px is a common candidate; 8px for coarser systems) and build a small closed ladder from it (for example 4/8/12/16/24/32/48/64).
- Proximity expresses relationship: related items take the smallest gap that separates them; unrelated groups take the largest.
- Off-scale values need a stated reason. Audit by searching for raw pixel lengths outside the ladder.

## Type scale

- Start from the platform or installed product ramp. Without one, generate a modular scale (ratio candidates: 1.125, 1.25, 1.333) and name steps semantically (`body`, `heading`, `display`) rather than by pixel value.
- Body measure lands near 45–75 characters; line height sits around 1.4–1.6 for body text and tightens toward display sizes.
- Prefer relative units so text scaling and zoom survive; use tabular numbers where digits change in place.

## Color

- Define semantic roles first — text, surface, border, accent, status — and derive ramps second. Components bind to roles, not hex values.
- Contrast is relational: verify every text/control/background pair in its actual states, including dark, high-contrast, and forced-color modes.
- Pair color with a second signal (label, icon, weight); never let hue alone carry meaning.

## Radius, shadow, elevation

- Keep a small, explainable vocabulary — two or three radii, two or three elevations. Depth communicates hierarchy: a modal interruption differs from parallel floating surfaces.
- Blur and large shadows are the most expensive primitives to render; profile decorative depth on representative low-end hardware.

## Motion durations

Defer to `motion-and-interaction.md`. Duration and easing values belong to the same tier system: components consume semantic motion tokens, not ad-hoc milliseconds.

## Adoption and audit

- Change the smallest tier that owns the decision; prefer adding a semantic alias over overriding a primitive locally.
- Audit consistency mechanically: search for hard-coded colors, lengths, and durations that bypass the token tiers, and route each either to a token or to a documented exception.
- When contributing to an existing system, follow its governance; propose patterns where the maintainers own them.

**Complete when:** every shipped value traces to a semantic token or a documented exception, each scale has explicit steps with an owner, and contrast is verified per state rather than assumed.
