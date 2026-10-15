# Mobile Web

## Scope

Use this reference when a web app is built for or reviewed on phones and touch devices: hover on touch, tap feedback, viewport height, input zoom and keyboards, overscroll, safe areas, touch gestures, text selection, and browser chrome color. It covers the platform layer that decides whether a web app feels installed or embedded. It does not cover native or React Native rewrites. Motion design stays in `motion-and-interaction.md`, and frame cost in `animation-performance.md`.

## Rules

- **Apply each fix where its reason applies.** `user-select: none` is correct on a button and a defect on body text.
- **Gate by capability, not device.** Use `(hover: hover)`, `(pointer: fine)`, `(pointer: coarse)`, `env()`, and viewport units; never branch on user-agent strings or screen width to guess at touch.
- **Write for touch and mouse at once.** Tablets with trackpads, laptops with touchscreens, and phones with mice all exist.
- **Preserve zoom.** Keep pinch zoom available, including on custom touch surfaces; address unwanted input zoom through the input's font size, not by disabling zoom.
- **Prefer CSS and meta tags to scripts.** Almost every fix here is one declaration; a script that detects touch to hide hover styles is the wrong tool.
- **Verify on hardware.** Desktop device emulation helps check layout, viewport sizes, and media-query branches, and some tools emulate touch events or safe-area insets. It does not replace a real device for the mobile browser's own gestures and chrome, the software keyboard, tap feel, overscroll, or performance.

## Symptom → fix

| Symptom | Fix | Boundary |
| --- | --- | --- |
| Hover state sticks after a tap | Put hover styles inside `@media (hover: hover) and (pointer: fine)` | Give touch users press feedback through `:active`; discoverability must not depend on hover |
| Gray or blue flash on tap | `-webkit-tap-highlight-color: transparent` on `html` | Only when every tappable element has its own `:active` and focus styles |
| Layout is taller than the visible screen | `100dvh` for app shells and bottom-pinned UI; `100svh` for heroes and first screens | `dvh` resizes as browser chrome moves, which shifts marketing content mid-scroll; `svh` stays stable |
| Page zooms into a focused input | Form controls at a computed font size of 16px or larger | iOS Safari zooms into inputs below 16px. Gating the size on `(pointer: coarse)` can miss hybrid devices, such as a tablet with a trackpad, so apply it to all form controls or verify on those devices. Never `user-scalable=no` or `maximum-scale=1` |
| Tap feels laggy | Press feedback on `:active` or `pointerdown`; `touch-action: manipulation` on controls | Commit the action on release according to native control semantics |
| Pull-to-refresh or rubber-banding hijacks an app | `overscroll-behavior: none` on `html, body` for app shells; `contain` on inner scroll areas | Keep pull-to-refresh on scrolling documents where it helps |
| Content stops short of the notch, or fixed bars sit under it | `viewport-fit=cover` plus `env(safe-area-inset-*)` padding with a `0px` fallback | On iOS Safari the insets usually resolve to `0` unless the page opts in with `viewport-fit=cover`; check each supported platform and display mode. Pad fixed headers, tab bars, toasts, and sheets |
| Long-press selects a button label | `user-select: none` and `-webkit-touch-callout: none` on controls only | Prose, addresses, error messages, and order numbers stay selectable |
| Carousel or drag surface fights page scroll | Native scroll snapping where it fits; for a custom horizontal drag, `touch-action: pan-y pinch-zoom` | `pan-y` alone also blocks pinch zoom. Reserve `none` for specialized surfaces, such as a drawing canvas or map, whose owner defines zoom behavior and an accessible alternative |
| Status bar color does not match the page | A `theme-color` meta tag for each color scheme the product supports; per-`prefers-color-scheme` tags only when it supports both | Match the color at the top of the page, not the brand color |

## Details

**Viewport units.** `lvh` and legacy `vh` measure the viewport with browser chrome collapsed, so a `100vh` element overflows on load and bottom-pinned buttons sit under the browser bar. Keep a `100vh` fallback line only if the support matrix requires it.

**Inputs and keyboards.** Set the keyboard to match the field: `inputmode="numeric"` for codes, `inputmode="decimal"` for amounts, `type="email"` and `type="tel"` for those fields, `autocapitalize="none"` and `autocorrect="off"` for usernames and codes, and `enterkeyhint` (`send`, `search`, `done`) so the return key says what it does. The viewport option `interactive-widget=resizes-content` makes the software keyboard shrink the layout viewport in browsers that support it, so dynamic-height layouts and bottom-pinned inputs respond to it; check what it does to fixed elements before adopting it.

**Overscroll.** Use `none` on the root and `contain` on children such as sheet content, chat lists, and sidebars: `contain` keeps the container's own bounce but stops the page behind it from moving. A `touchmove` listener that calls `preventDefault()` blocks scrolling entirely and makes the listener non-passive, which costs frames.

**Touch axes.** `touch-action` lists what the browser may still do, and anything not listed is blocked: `pan-y pinch-zoom` on a custom horizontal carousel keeps vertical page panning and pinch zoom while the script handles horizontal drags. For native-scroll carousels, `scroll-snap-type: x mandatory` on the track and `scroll-snap-align: start` on slides use the browser's own physics and need no `touch-action` override.

**Browser chrome.** Declare only the color schemes the product actually supports in `<meta name="color-scheme">`: `light` for a light-only product, `light dark` only when both themes exist. Declaring `dark` without a dark theme can darken native controls and scrollbars on a light page. Keep the declaration and the `theme-color` tags in sync with the app's current theme — whether that follows the OS setting, an app setting, or a class — and update them when the theme changes. For an installed web app, the manifest's `theme_color` and `background_color` and the Apple status-bar meta tag are the same decision.

## Verify on hardware

- Serve the dev server on the local network and open it on a phone by the machine's IP address.
- Inspect with Safari's Web Inspector for iOS or `chrome://inspect` for Android.
- Test on a phone a few years old, with the keyboard open, and once in landscape.
- Test as an installed web app if that is a target; standalone mode changes the viewport, safe areas, and status bar.
- A simulator is better than desktop emulation but still misses touch feel.

**Complete when:** every applicable symptom has been checked, each fix states its reason, and each result is marked as verified on a named device or as verified from code only and still needing a device check.
