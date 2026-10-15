# Animation Performance

## Scope

Use this reference when web motion drops frames, when choosing which property to animate on cost grounds, when choosing an animation driver for performance, or before reaching for `will-change` or GPU layers. Whether motion belongs, its timing, easing, springs, and accessibility stay in `motion-and-interaction.md`.

The question here is whether every frame finishes in time, not whether the motion looks right. Browser and library behavior changes between versions: treat every threshold and acceleration claim below as a starting hypothesis, and confirm it against the installed implementation and a profile on representative hardware.

## Frame budget

At 60Hz the browser has about 16.7ms per frame; at 120Hz, about 8.3ms. Design against the refresh rates of the devices the product supports, and profile on representative hardware for that audience as well as on a development machine. A long layout or script task costs one missed frame for every budget it overruns.

Two things decide whether motion stays inside the budget: **what** is animated (the cost of each frame) and **where** the work runs (whether other page work can block it).

## What you animate: pipeline tiers

To show a visual change the browser may run layout (size and position), paint (draw into layers), and composite (put layers on screen). Each property usually enters at one of these points:

| Tier | Properties | Typical cost |
| --- | --- | --- |
| Usually composite candidates | `transform`, `opacity`; in some engines also `filter`, `clip-path`, `background-color` | Often cheapest, when the engine can promote the element to its own layer |
| Paint + composite | `box-shadow`, `border-radius`, `color` | No re-measuring, but usually a redraw every frame |
| Layout + paint + composite | `width`, `height`, `padding`, `margin`, `top`, `left`, `border-width` | Usually most expensive; one growing element can move everything around it |

`transform` and `opacity` are the most widely compositable candidates, but whether a given animation is composited depends on the browser, the element's content, and its layers. Even a `transform` animation can regress when the moving area is large or creates many layers. Confirm the tier in each supported browser's performance trace.

Swap down a tier only when the cheaper property preserves what the user relies on:

| Instead of | Candidate | Swap only if |
| --- | --- | --- |
| `width`, `height`, or `padding` to grow or shrink | `scale()` | Surrounding layout need not reflow, and geometry, hit targets, text rendering, and focus indicators stay correct; scaling also scales text and borders |
| `top`, `left`, or `margin` to move | `translate()` | Neighboring content should not move with it; percentages are relative to the element's own size |
| a `display` or `visibility` swap | `opacity` | The hidden state is still removed from interaction and the accessibility tree |
| `box-shadow` | `filter: drop-shadow(…)` | The rendered result matches: drop-shadow follows the element's alpha shape and has no spread or inset |

When the reflow is the point — an accordion opening, content making room — a layout animation is legitimate; keep it short and measure it. Otherwise prefer the cheaper candidate even when the expensive one seems fine on your machine: a `padding` animation that looks identical to a `scale()` one is the likelier of the two to regress on slower hardware. Layout properties can also move the wrong things — animating a sidebar's `margin-left` re-lays out the content beside it every frame, while `translateX` leaves it in place.

Name each transitioned property instead of `transition: all`, which animates whatever changes next, layout properties included.

## Where it runs: drivers and threads

| Driver | Where the work runs |
| --- | --- |
| `requestAnimationFrame` callbacks that write styles each frame | Main thread |
| Web Animations API (`element.animate()`) | May run off the main thread when the engine accelerates it |
| CSS transitions and keyframes | May run off the main thread when the engine accelerates it |

Classify the effective driver of each animation, not the library as a whole: a library such as Motion or GSAP may drive one animation from a `requestAnimationFrame` loop and hand another to the Web Animations API or native CSS, depending on the API, the properties, and the installed version. Check the version's documentation or a trace before stating which. Main-thread motion only suffers when the page is busy during it, so watch for motion that plays alongside navigation, data fetching, hydration, or long tasks — a tab indicator during a route change is a common case. Consider moving that motion to CSS or the Web Animations API, then confirm in a trace.

Acceleration is progressive enhancement that the browser may decline, and its conditions change between versions. Correctness wins: percentage transforms such as `translateY(100%)` remain right for elements of unknown size even where an engine declines to accelerate them.

**Working split.** Use CSS for simple motion and for anything that plays while the page is busy; use a JavaScript library for what CSS cannot do well — real springs, shared layout animations, exit animations for unmounting elements, and momentum gestures.

## Framework pitfalls

- **State updated every frame.** A hand-rolled animation that sets component state on each frame re-renders the component every frame, and the render alone can blow the budget. Write the value directly to the element's style, or to a library motion value, instead. Look for state updates inside `requestAnimationFrame`, pointer, scroll, and drag handlers.
- **Inherited CSS variables.** Writing a per-frame value to a custom property on a parent recalculates style for every descendant, so a `transform` animation degrades as content grows (Vaul's drawer drag slowed once it held more than about 20 items). Set `transform` on the moving element itself. Suspect this whenever motion gets worse with more content.
- **Motion and Framer Motion shorthands.** The source (Emil Kowalski's `animation-performance` skill, revision `2d22863`) reports that `x`, `y`, `scale`, and `rotate` were implemented with CSS variables and not hardware-accelerated, while a full `transform` string could be. Treat this as a version-specific claim to check, not as the current API contract:

  ```jsx
  // Per the source revision above; verify in the installed version.
  <motion.div animate={{ x: 100 }} />                         // reported: main thread
  <motion.div animate={{ transform: "translateX(100px)" }} /> // reported: may be accelerated
  ```

  Keep the readable shorthands by default. If the motion must survive a busy main thread, check the installed version's documentation or a trace, and switch to the string form only when it shows a difference.

## Paint-heavy effects

- **Shadows** usually repaint the element every frame. Candidates: `filter: drop-shadow()` when it renders the same result, or animating the opacity of a pre-rendered shadow layer.
- **Blur** gets expensive quickly, especially in Safari. The source's starting points: keep animated `blur()` under 20px, and 2–5px is enough to soften a crossfade. Profile larger values instead of assuming they are free or forbidden.
- **Large filtered or blurred surfaces** cost the most; keep the animated layer as small as the effect allows.

## Layers and `will-change`

A browser can move an animation between rendering paths at its start or end, and the hand-off can shift the element by a pixel. `will-change: transform` is a hint that may lead the browser to promote the element ahead of time and avoid that hand-off; the browser may also ignore it.

Add it only after you observe that shift or measure dropped frames, and confirm in a trace that it helped. Browsers often promote elements while they animate `transform` or `opacity`, so on the common path the hint may change nothing, while any layer it does create costs GPU memory. Put it on the animating element only, never on `*` or large containers; set it shortly before the motion and remove it once the motion ends, unless the element animates continuously. It is most likely to earn its place on an expensive paint, such as a large blurred or filtered element; keep that layer small.

## Diagnose jank

List every animation in scope with its element, driver, properties (expand `transition: all` and library shorthands), and what plays at the same time. Then work down the causes, most common first:

1. Which properties animate? Layout properties first, then `box-shadow` and `border-radius`, which are easy to miss.
2. Does the jank coincide with the page being busy? Check the effective driver; consider CSS or the Web Animations API.
3. Does a framework re-render every frame?
4. Does it get worse as content grows? Look for an inherited CSS variable or too many nodes animating at once.
5. Is a CSS variable animated, directly or through library shorthands?
6. Is a large blur animated?
7. Still shifting or stuttering? Only now try `will-change` on the animating element.

Confirm with a recording, not by feel: the browser's performance panel for dropped frames and long tasks, and its animations panel to slow motion down. Profile on a real mid-range phone through remote debugging; desktop CPU throttling models a slow CPU, not a weak GPU or a small memory budget.

For each finding, report the element and location, the cause from the list above, the change (before and after), and whether it was verified from code or still needs a device recording. Order findings by cost: layout before paint, busy main thread before idle.

**Complete when:** every animation in scope has a named driver and property list, every finding names its cause, and each fix is either verified by a recording on representative hardware or marked as needing one.
