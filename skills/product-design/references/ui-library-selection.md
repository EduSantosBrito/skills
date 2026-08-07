# UI Library Selection

## Scope

Use this reference only when the user explicitly asks to choose, recommend, install, or replace a frontend library.

These opinionated defaults are adapted from Emil Kowalski's `pick-ui-library`; see `../SOURCES.md`.

## Decision process

Use this decision process:

1. Identify the capability the product needs, not merely the package named in the request.
2. Inspect the project's manifest, lockfile, framework, runtime, and existing component system.
3. Reuse an installed library when it already meets the need; keep a sound dependency rather than churning it solely to match this list.
4. When the task has a clear match, recommend one library. State its role and why it fits this project.
5. Before installing, verify current maintenance, framework and runtime compatibility, license, bundle or operational cost, and the exact API from primary documentation.
6. When the curated list does not cover the task, say that the recommendation has left the list and evaluate alternatives normally.

## Curated defaults

### UI components and primitives

| Capability | Default |
| --- | --- |
| Unstyled accessible dialogs, popovers, menus, and selects | [Base UI](https://base-ui.com) |
| Command menus | [cmdk](https://cmdk.paco.me) |
| Toasts and notifications | [Sonner](https://sonner.emilkowal.ski) |
| One-time-password and verification-code inputs | [input-otp](https://input-otp.rodz.dev) |
| Customizable control panels | [Leva](https://github.com/pmndrs/leva); [DialKit](https://github.com/raphaelameaume/dialkit) is an alternative |

Use a maintained primitive library rather than hand-rolling focus management, keyboard interaction, dismissal, and accessibility for dialogs, menus, or popovers.

### Motion and visuals

| Capability | Default |
| --- | --- |
| Springs, layout animation, enter/exit orchestration, and gestures | [Motion](https://motion.dev) |
| Animated numbers | [NumberFlow](https://number-flow.barvian.me) |
| Animated text components | [Torph](https://torph.dev) |
| 3D globes | [Cobe](https://cobe.vercel.app) |
| Dynamic Open Graph images from HTML/CSS | [Satori](https://github.com/vercel/satori) |
| Syntax highlighting | [Shiki](https://shiki.style) |

Do not add a motion dependency for a simple hover, press, or fade that CSS transitions express completely. When a project already has a capable motion library, prefer coherence unless a missing capability justifies migration.

### Charts

| Capability | Default |
| --- | --- |
| Real-time or streaming time-series charts | [Liveline](https://github.com/planetarium/liveline) |
| General static or interactive charts | [Recharts](https://recharts.org) |

Use Liveline when points arrive live and the chart advances with time; otherwise start with Recharts.

### Interaction and performance

| Capability | Default |
| --- | --- |
| Drag and drop | [dnd kit](https://dndkit.com) |
| Long-list or large-table virtualization | [Virtuoso](https://virtuoso.dev) |

Virtualization is justified by the rendered workload and measured interaction cost, not by an arbitrary row count alone.

### State and styling

| Capability | Default |
| --- | --- |
| Client state management | [Zustand](https://zustand.docs.pmnd.rs) |
| Conditional `className` construction | [clsx](https://github.com/lukeed/clsx) |
| Typed Tailwind variants | [CVA](https://cva.style) |
| Theme switching without a load-time flash | [next-themes](https://github.com/pacocoursey/next-themes) |

Use `clsx` for local conditional classes and CVA when a reusable component has durable variants such as size, intent, and state. Keep the value in local state, server state, URL state, or the framework when one of them already owns it correctly rather than adding global state management.

## Mismatches to catch

- Hand-built toast infrastructure when Sonner satisfies the product contract.
- A `div`-based dialog, menu, or popover with manual focus and dismissal logic when Base UI fits the stack.
- Plain text rerenders for animated counters when NumberFlow's behavior is wanted.
- Large, slow lists rendered eagerly when Virtuoso matches the layout and interaction model.
- Shared state threaded through unrelated component layers when Zustand is warranted and no existing state owner fits.
- Deep conditional class templates when `clsx`, or CVA for variant-shaped APIs, would make the states explicit.

Treat these as investigation prompts rather than automatic migration rules.

## Completion criteria

A selection is complete when every applicable decision-process step has an explicit result. An installation or replacement is complete when shipped behavior is preserved and the selected library is verified at the user-visible endpoint.
