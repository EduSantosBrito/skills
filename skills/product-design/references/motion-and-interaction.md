# Motion and Interaction

**Contents:** [Governing principles](#governing-principles) · [Motion gate](#motion-gate-decide-whether-motion-belongs) · [Timing and easing](#timing-and-easing) · [Response and direct manipulation](#response-and-direct-manipulation) · [Interruptibility and springs](#interruptibility-and-springs) · [Velocity, projection, and boundaries](#velocity-projection-and-boundaries) · [Spatial behavior](#spatial-behavior) · [Common patterns](#common-patterns) · [Rendering and performance](#rendering-and-performance) · [Materials and depth](#materials-and-depth) · [Accessibility](#accessibility) · [Review and audit](#review-and-audit) · [Verification](#verification)

## Scope

Use this reference to:

- decide whether an interface should move;
- select and specify an implementation;
- review motion; or
- specify gesture behavior.

For reverse lookup when a user describes an effect without knowing its name, use `animation-vocabulary.md`.

This reference deduplicates motion guidance from Emil Kowalski's design-engineering and Apple-design skills.

## Governing principles

**Continuity** governs motion: an interaction should respond immediately, preserve spatial and velocity relationships, remain interruptible, and settle in a way that explains what changed. **Restraint** decides whether motion belongs at all.

Treat the exact values below as starting points rather than universal laws. First reuse product tokens and platform conventions; then test the actual interaction on the target hardware.

## Motion gate: decide whether motion belongs

Run every proposed animation through these questions in order.

### 1. Frequency

| Expected frequency | Default |
| --- | --- |
| Hundreds of times per day or keyboard-driven expert action | Immediate state change; normally no decorative transition |
| Tens of times per day | Near-imperceptible feedback or reduced motion |
| Occasional surface such as a modal, drawer, or toast | Standard functional motion |
| Rare or first-run moment | More room for explanation or delight |

Frequency is contextual. Label guessed counts as guesses rather than facts. The higher the repetition, the more every millisecond and flourish compounds.

### 2. Purpose

Motion needs at least one named job:

- **Feedback:** confirm that input was received.
- **State indication:** make a change legible.
- **Spatial consistency:** show where an element came from or went.
- **Continuity:** bridge a layout or content change that would otherwise jump.
- **Explanation:** demonstrate behavior in onboarding or marketing.
- **Delight:** reinforce a rare meaningful moment without delaying the task.

If “it looks cool” is the only reason and the interaction is frequent or information-dense, remove the animation.

### 3. Budget

The motion must fit the task's latency budget and remain operable while it runs. Typical starting ranges:

| Interaction | Starting range |
| --- | --- |
| Press feedback | 100–160ms |
| Tooltip or small popover | 125–200ms |
| Dropdown or select | 150–250ms |
| Modal or drawer | 200–500ms, depending on travel distance |
| Marketing explanation | May be longer; never block control unnecessarily |

Most compact UI transitions should settle in roughly 300ms or less. Distance, display size, platform convention, and continuity can justify a different result. Measure perceived and actual responsiveness rather than enforcing a magic number.

### 4. Function and preference

Move functional data while the user is trying to read or manipulate it only when motion explains the update. Define the reduced-motion equivalent before implementation. If motion cannot remain understandable and accessible, use a static state change.

The gate is complete when frequency is contextualized, motion has at least one named job, timing fits the task and remains operable, and an understandable accessible reduced-motion equivalent is defined.

## Timing and easing

Choose easing by the motion's role:

- Entering or responding directly to input: strong **ease-out** for immediate movement and gentle settlement.
- Moving or morphing between visible states: **ease-in-out** when acceleration and deceleration should both be visible.
- Color or subtle hover feedback: standard **ease** is often enough.
- Constant-rate progress or marquee motion: **linear**, only when constant speed carries meaning.

Useful candidate curves when the product has no established tokens:

```css
--ease-out: cubic-bezier(0.23, 1, 0.32, 1);
--ease-in-out: cubic-bezier(0.77, 0, 0.175, 1);
--ease-drawer: cubic-bezier(0.32, 0.72, 0, 1);
```

Avoid `ease-in` for direct UI responses because its slow start can make input feel ignored. Treat that as a strong heuristic, not a ban on every cinematic or exit sequence.

Use asymmetric timing when the phases have different meaning: a deliberate hold may fill slowly while release and cancellation snap back quickly. Enter and exit may use different durations while preserving the same spatial path.

## Response and direct manipulation

- Show press feedback on pointer-down, then commit the action on release according to native control semantics.
- During drag, keep content aligned 1:1 with the pointer and preserve the original grab offset.
- Use Pointer Events and pointer capture so tracking survives leaving the element bounds.
- Apply a small movement threshold before committing to a drag direction; continue evaluating plausible gestures until intent is clear.
- Ignore unrelated additional pointers once a single-pointer gesture owns the interaction, unless multi-touch is part of the design.
- Never disable all input merely because a transition is running. Define what retargeting, cancellation, or repeated input should do.

## Interruptibility and springs

Gesture-driven and rapidly reversible motion should begin from the current on-screen value rather than a stale logical start or prior target. Retargeting should preserve continuity and, where the API supports it, current velocity.

Use springs when the user can grab, flick, reverse, or redirect the object. Think in designer-facing terms:

- **Response:** how quickly the spring approaches the target.
- **Damping:** how much it overshoots and oscillates.

Start ordinary UI critically damped or with no visible bounce. Add subtle bounce only when momentum or product personality supports it. Candidate starting points:

| Interaction | Candidate |
| --- | --- |
| Reposition with no overshoot | response about `0.4s`, damping ratio `1.0` |
| Drawer or momentum release | response `0.3–0.4s`, damping ratio around `0.8` |
| Motion/Framer Motion ergonomic API | `{ type: "spring", duration: 0.4, bounce: 0 }` initially |
| Momentum-driven playful release | `{ type: "spring", duration: 0.4, bounce: 0.2 }` |

Library parameters do not map perfectly across implementations. Confirm the installed API and tune by observed behavior rather than copying values blindly.

For predetermined state transitions, CSS transitions are often simpler and naturally retarget from the current computed state. Keyframes fit authored sequences, but a restarted keyframe sequence may jump when repeatedly triggered. WAAPI can provide programmatic control for browser animations. Choose from the interaction contract rather than a blanket preference for CSS or JavaScript.

## Velocity, projection, and boundaries

### Velocity handoff

At release, continue with the pointer's velocity so drag and settling do not have a visible seam. Track a short position/time history rather than relying on one noisy event. Some APIs expect absolute velocity; others normalize it against remaining distance:

```text
relativeVelocity = gestureVelocity / (targetValue - currentValue)
```

Guard zero or tiny remaining distance and verify the library's units.

### Momentum projection

For a flick, choose the destination from the projected endpoint rather than only the release position, then animate toward the selected snap point with release velocity. Apple's exponential-decay example can be represented as:

```js
function project(initialVelocity, decelerationRate = 0.998) {
  return (initialVelocity / 1000) * decelerationRate / (1 - decelerationRate);
}

const projected = currentPosition + project(releaseVelocity);
const target = nearestSnapPoint(projected);
```

The rate is a feel parameter, not a universal constant. Use platform behavior or product tests to select it.

### Rubber-banding

At a boundary, progressive resistance preserves feedback better than a hard stop:

```js
function rubberband(overshoot, dimension, constant = 0.55) {
  return (overshoot * dimension * constant) /
    (dimension + constant * Math.abs(overshoot));
}
```

Keep the boundary and eventual state clear. Resistance must not imply that an unavailable action will succeed.

## Spatial behavior

- Enter and exit along paths that preserve where the surface belongs.
- Anchor popovers, menus, and tooltips to their trigger; centered modals are a legitimate exception.
- Set `transform-origin` from the owning component library when available.
- Start scale entrances from a subtle visible size such as `0.95–0.97` plus opacity rather than `scale(0)`.
- Use percentage translation when movement should scale with the element's own size, such as `translateY(100%)` for an off-canvas sheet.
- Let intermediate frames hint at the destination rather than interpolating without a spatial story.

## Common patterns

### Press feedback

```css
.button {
  transition: transform 160ms var(--ease-out);
}

.button:active {
  transform: scale(0.97);
}
```

Use subtle scale only where it does not move neighboring layout or conflict with native feedback.

### Origin-aware popover

```css
.popover {
  transform-origin: var(--transform-origin);
  transition: transform 180ms var(--ease-out), opacity 180ms var(--ease-out);
}

.popover[data-starting-style],
.popover[data-ending-style] {
  opacity: 0;
  transform: scale(0.97);
}
```

This origin variable is Base UI's API. Use the actual primitive's state and origin API; treat these attribute names as specific to Base UI rather than portable to another library.

### Tooltips

Delay the first tooltip enough to avoid accidental activation. Once a tooltip group is active, adjacent tooltips may skip delay and motion so scanning remains fast. Preserve an equivalent for keyboard focus.

### Hold to confirm

A hold affordance may reveal progress with `clip-path` or scale over a deliberate interval, then cancel quickly on release. Use it only when holding genuinely reduces accidental harm; never replace an accessible explicit confirmation with a gesture that some users cannot perform.

### Group entrance

Stagger can clarify order for a small, rare group. Start around 30–80ms between items, keep the total short, never delay interactivity, and remove movement under reduced-motion preferences.

### Reveal as progressive enhancement

Content is visible by default: without JavaScript, without browser support, under reduced motion, and when the script fails to initialize. Apply the hidden starting state only after the controller or observer is ready — for example, set the gating class from the same script that creates the observer. Copying a pattern that puts the gate class (such as `html.js`) in the markup or in an early inline script can leave content hidden when the later initialization fails.

For a one-shot scroll reveal, reveal the element once and stop observing it:

```css
@media (prefers-reduced-motion: no-preference) {
  .reveal-ready [data-reveal]:not(.is-in) { opacity: 0; transform: translateY(24px); }
  [data-reveal] { transition: opacity 600ms var(--ease-out), transform 600ms var(--ease-out); }
}
```

```js
const targets = document.querySelectorAll('[data-reveal]');
const io = new IntersectionObserver((entries) => {
  for (const entry of entries) {
    if (entry.isIntersecting) {
      entry.target.classList.add('is-in');
      io.unobserve(entry.target);
    }
  }
});
document.documentElement.classList.add('reveal-ready'); // hidden state applies only from here
targets.forEach((el) => io.observe(el));
```

The owning component disconnects the observer when it unmounts. Never animate required content while it is invisible or let a reveal stand between the reader and the text. Pause looping motion when it is off screen or the tab is hidden.

### Crossfade bridge

When two states visibly double-expose during a crossfade, a small transient blur may help them read as one transformation. Blur can be expensive and reduce legibility; keep it subtle, profile it (`animation-performance.md` carries starting thresholds), and prefer a cleaner structural transition when available.

### Clip and reveal

`clip-path: inset()` can create reveals, comparison sliders, and progress fills without changing layout. Compositor behavior varies by browser and effect; test rather than assuming it is free.

### Tab indicator with a color change

Separately timed color transitions across a tab list rarely land together. Instead, render a decorative copy of the tab list styled as the active state and clip it so only the active tab shows; animating the clip changes text and background in one motion:

```css
.tabs-active-copy {
  clip-path: inset(0 60% 0 20%); /* set from the active tab's measured position */
  transition: clip-path 250ms var(--ease-in-out);
}
```

Keep the semantic tab list as the only interactive one, with its roles, selected state, and keyboard behavior. Hide the copy from assistive technology and pointer input (`aria-hidden="true"`, `inert`, `pointer-events: none`), recompute the clip when tab widths change through resizing, zoom, or translation, and switch without movement under reduced motion.

### Entry without a mount flag

`@starting-style` defines the state an element transitions from when it first renders, so an entry needs no JavaScript mount flag:

```css
.toast {
  transition: opacity 400ms ease, transform 400ms ease;

  @starting-style {
    opacity: 0;
    transform: translateY(100%);
  }
}
```

Check support against the product's browser matrix. Where it is missing, set a mounted attribute after the first frame and transition from that, or let the element appear without an entry. A missing entry animation must never hide content.

### Accordion and collapse

Height has no transform equivalent here, so this is one of the few accepted layout animations. Keep it short (the source starts around 200ms) because every frame costs layout. Measure the content height, or use a headless primitive that exposes it, rather than animating to `auto`. An alternative that needs no measurement: transition the panel's `grid-template-rows` from `0fr` to `1fr`, with a single child that has `min-height: 0` and `overflow: hidden`; check browser support, interruption, and content that changes size while open. Use a transition so a toggle mid-animation retargets from the current height instead of restarting. Keep the trigger's expanded state in sync and remove collapsed content from focus order and the accessibility tree once it closes.

### Programmatic reveal without a library

When motion needs JavaScript control but not a dependency, the Web Animations API can match CSS performance:

```js
const reveal = element.animate(
  [{ clipPath: 'inset(0 0 100% 0)' }, { clipPath: 'inset(0 0 0 0)' }],
  { duration: 1000, fill: 'forwards', easing: 'cubic-bezier(0.77, 0, 0.175, 1)' }
);
```

Keep the returned animation so you can reverse or cancel it on interruption, and skip or shorten it under reduced motion.

## Rendering and performance

Prefer `transform` and `opacity`, name transitioned properties instead of `transition: all`, and judge smoothness from a trace on representative lower-end and high-refresh hardware. This is a default, not proof of performance. When motion drops frames, or when choosing a property, driver, or layer strategy on cost grounds, use `animation-performance.md`: it owns frame budgets, pipeline tiers, threads, framework pitfalls, paint-heavy effects, `will-change`, and jank diagnosis.

Smoothness includes more than FPS. Large per-frame travel can strobe even at the display refresh rate, and coordinated properties can drift visibly while each remains “smooth.”

## Materials and depth

Translucency can express a floating layer while preserving context. Use it according to hierarchy, not as a universal style:

- Pair modal surfaces with a scrim; use offset or translucency without a scrim for parallel non-blocking work.
- Increase separation for larger or busier floating surfaces.
- Avoid stacking several light translucent surfaces where text contrast becomes unpredictable.
- Animate blur only when materialization is part of the spatial story and performance remains acceptable.
- Support `prefers-reduced-transparency` with a more opaque or solid surface.
- Support increased-contrast and forced-color modes with explicit boundaries.

## Accessibility

Reduced motion means replacing vestibular movement with a gentler equivalent while preserving state feedback:

```css
@media (prefers-reduced-motion: reduce) {
  .sheet {
    transform: none;
    transition: opacity 160ms ease;
  }
}

@media (hover: hover) and (pointer: fine) {
  .interactive:hover {
    transform: scale(1.02);
  }
}

@media (prefers-reduced-transparency: reduce) {
  .toolbar {
    background: Canvas;
    backdrop-filter: none;
  }
}
```

- Keep meaningful status changes perceivable without motion.
- Do not make hover the only way to discover an action.
- Preserve focus visibility and native keyboard activation.
- Avoid large full-viewport movement, abrupt brightness changes, and unnecessary looping motion.
- Ensure a gesture has an accessible alternative.
- Do not block interaction until a decorative sequence finishes.

## Review and audit

Inspect every affected animation against these categories:

1. Purpose and frequency.
2. Input response and latency.
3. Easing and timing.
4. Spatial origin and continuity.
5. Interruptibility and repeated input.
6. Gesture velocity, projection, and boundaries.
7. Rendering cost under load.
8. Reduced motion, transparency, input alternatives, and focus.
9. Cohesion with product tokens and personality.
10. Missed motion only where a state change is otherwise confusing.

Escalate likely defects such as `transition: all`, unexplained long UI motion, `scale(0)` entrances, trigger-anchored surfaces growing from center, movement without reduced-motion handling, layout animation on a hot path, or gestures that jump when interrupted. Confirm context before reporting: a centered modal, authored marketing sequence, or measured layout transition may be correct.

Prefer remediation in this order:

1. Remove unjustified motion.
2. Reduce distance, duration, or animated properties.
3. Correct timing and spatial origin.
4. Make repeated and gesture-driven motion interruptible.
5. Move work off layout/paint hot paths where measurement supports it.
6. Add accessible preference and input alternatives.
7. Add polish only after the contract is correct.

## Verification

- Trigger the interaction slowly, rapidly, and in reverse.
- Interrupt it at several points and confirm there is no jump or input lockout.
- Inspect at reduced playback speed and frame by frame.
- Test keyboard, pointer, touch, and relevant assistive technology.
- Toggle reduced motion, reduced transparency, high contrast, and zoom/text scaling.
- Use a real device for touch and momentum.
- Record a performance trace under representative load.
- Revisit subjective feel with fresh eyes and state uncertainty when no runtime check was possible.

Motion is complete only when the interaction remains understandable, responsive, interruptible where required, accessible, and cohesive. A merely running animation is incomplete.
