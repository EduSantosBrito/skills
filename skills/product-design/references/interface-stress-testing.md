# Interface Stress Testing

## Scope

Use this reference to test whether a component or screen survives realistic extreme content: long, short, missing, or localized text; unbreakable identifiers; extreme numbers; empty and huge collections; time edge cases; broken media; mixed states; and narrow, wide, zoomed, dark, right-to-left, or touch environments. Visual critique stays in `foundations.md` and `visual-direction-and-anti-defaults.md`; motion stays in `motion-and-interaction.md`.

Demo data is usually chosen, without anyone noticing, to make the design look good: names that fit on one line, counts that need no separator, every optional field filled. Stress testing undoes that choice one field at a time.

## Rules

- **Plausible or schema-backed values.** Each worst-case value is something a real user could produce, or the actual limit from the validation schema, database column, or API contract. Random filler such as `aaaaaaaa…` proves nothing. Record the limit that applies to each field — a schema, an API contract, or a product policy. A field with no explicit limit is not automatically a defect; note it, and test a long but believable value.
- **Go beyond long text.** The breaks that ship are often the short name that leaves an orphaned separator, the missing avatar, "1 members", the empty list, or a translated badge.
- **Change the data, not the component.** When you are allowed to inject data, inject worst-case values through the same boundary as demo data: the fixture, mock, props, or API stub. Editing markup or CSS to produce a break tests the edit, not the component.
- **One dataset, many failures.** Spread different failures across the first visible rows, as real data does, instead of stacking them into row one.
- **Respect the session's write permission.** In a read-only review, observe with tools that write nothing — existing stories, previews, fixtures, dev tools, and code reading — and do not create fixtures, toggles, tests, or fixes. Create a worst-case fixture, a Demo / Worst case switch, or a fix only when the owning workflow authorizes writes; keep any switch behind the development environment or in a throwaway prototype route.
- **Report before fixing in reviews.** Some breaks are design decisions, such as truncating or wrapping. In a review, list every break with a proposed fix, list the cases you could not run and why, and leave the decisions to the owner; in authorized implementation, fix and re-verify.

## Procedure

1. **Map the surface.** List every rendered value with its source, type, applicable limit, and whether it is optional. Include values people forget: counts in headers, relative timestamps, badge and status text, button labels that come from data, tooltips, avatar images, and the list length itself. Look up limits in validation schemas, migrations, API types, form `maxLength`, and product policy; note where the frontend and backend disagree, because the longer limit can arrive through an import or the API. **Complete when:** every rendered value has a source and either an applicable limit or a note that none was found.
2. **Choose the worst case.** Pick values from the catalog below, shaped like the demo data. Also cover **Empty** (zero items and no results), **One** (a single item and every count at exactly 1), and **Huge** (the realistic upper bound, such as 1,000+ rows for an unpaginated list, which is a performance break as well as a visual one). With write permission, assemble them as one fixture next to the demo data; without it, run what existing tooling allows and list the rest as cases not executed.
3. **Break it.** Start from the product's support matrix: the component's real container width and its widest supported layout. Candidates to add when the product supports them: 320 CSS pixels wide (the WCAG reflow width, which 400% zoom on a 1280px screen produces), 200% browser zoom or a larger root font size, dark mode, right-to-left, and touch. Screenshot and compare where tooling allows; otherwise say which findings were seen and which were inferred from code.
4. **Report.** Order breaks by their effect on users of this product, worst first: **Broken** (content unreadable, action unreachable, wrong data), **Ugly** (readable but visibly wrong), or **Fragile** (fine now, one realistic step from breaking, such as a missing fallback). Give each the field, the value, what happens, the fix, and its location. Then list the decisions with a recommendation each, the cases not executed, and the cases that already held up.
5. **Fix and re-check, when authorized.** After fixing, re-check every state, including the demo data, so a fix does not regress the normal case. Whether the worst-case fixture is kept as an automated regression test is decided by the owning workflow's test-authoring gate, not by default.

**Complete when:** every applicable catalog row has been tried, or listed as not executed with a reason, at every width and environment the product supports; and every break has a signature, a cause, and a fix or an explicit decision.

## Realistic worst-case catalog

Use `example.com`, `example.org`, or `.test` domains so fixtures never point at a real inbox or site.

| Kind | Values | What tends to break |
| --- | --- | --- |
| Names | `Aleksandra Wiśniewska-Kowalczyk`; `Christopher Alexander Montgomery III`; `Jo`; `J`; `Đặng Thị Ngọc Hân`; `王秀英`; `نور الهدى عبد الرحمن`; `María José de la Cruz y Fernández`; `dana`; `🦊 Fox`; `👩🏽‍💻 Priya`; `  Sam   Lee `; missing name | Wrapping, initials (`CI`, `J`, half an emoji), diacritics clipped by tight line height, CJK breaking anywhere, right-to-left punctuation, lowercase particles, grapheme length, empty words, a missing fallback |
| Identifiers | `bartholomew.fitzgerald@northwind-industries-holdings.example.com`; `a@b.test` (minimal plausible length; test the schema's minimum separately); `first.last+billing@example.com`; a long URL with query string; a UUID; `Q3 Board Deck — FINAL (revised) v12 [approved by legal].pdf` | No break opportunities, siblings pushed off the row, `+` rejected, end-truncation hiding the part that differs |
| Labels and copy | `Senior Product Design Engineer, Platform Infrastructure`; `Invitation expired 12 days ago`; `Benachrichtigungseinstellungen`; `Paramètres de confidentialité et de sécurité`; twelve tags on one item; an empty or whitespace title; `<script>alert(1)</script>`, `&amp;`, `**bold**`; a newline in a single-line field; a 2,000-character pasted description | Secondary slots wrapping to three lines, badges wrapping, unbreakable compounds, translation expansion (UI copy often runs about 30% longer), tag walls, collapsed headings, escaping, clamping |
| Numbers and money | `0`; `1`; `1284`; `1000000`; `12345678.9` as currency; `-42.5`; `0.1 + 0.2`; `142%` and `-3%`; `null`, `undefined`, `NaN`; `de-DE` versus `en-US`; a live `99` → `100` | Zero states, plurals, separators, column overflow, negative styling, float artifacts, meters past their bounds, literal nulls, locale formatting, width jitter |
| Collections | 0 items; 1 item; exactly page size and page size + 1; 1,000+ unpaginated; one item ten times larger; identical names | Missing empty state, lonely grids, off-by-one pagination, render and scroll cost, stretched rows, indistinguishable items |
| Time | now; 12 days, 11 months, 3 years ago; a future date; `1970-01-01`; `2025-12-31T23:30:00-08:00`; `1,284 hours` | "0 seconds ago", relative-time thresholds, negative "ago", zero timestamps, time-zone day shifts, durations that never roll up |
| Media | an avatar URL that returns 404; no avatar; a 4000×200 or 200×4000 image; a dark transparent logo in dark mode; a slow image | Broken-image icons, fallback parity, distortion, height blowouts, invisible logos, layout shift |
| States | loading; API error; partial data; every status value at once; no permission; the current user in the list | Mismatched skeletons, raw error text, misaligned rows, varying badge widths, disabled layouts, self-actions |

Format dates and times with `Intl.DateTimeFormat` and `Intl.RelativeTimeFormat`, numbers with `Intl.NumberFormat`, and plurals with `Intl.PluralRules` rather than hand-built strings.

## Failure signatures

| What you see | Likely cause | Fix |
| --- | --- | --- |
| Avatar or icon squished into an oval | A flex child shrinking | `flex-shrink: 0` on fixed-size boxes |
| Text overflows instead of wrapping or truncating | Flex or grid child with `min-width: auto` | `min-width: 0` on the text column; `minmax(0, 1fr)` in grid |
| Email or URL runs past the edge | No break opportunities | `overflow-wrap: anywhere` on that element |
| Trailing action pushed off-screen | The middle content took all the space | `min-width: 0` on the middle, `flex-shrink: 0` on the action |
| Badge wraps onto two lines | The badge is allowed to shrink | `white-space: nowrap` and `flex-shrink: 0`, then decide what yields |
| Avatar adrift beside a three-line name | Centered alignment on rows of varying height | Top-align once text can wrap |
| Last row cut mid-glyph at a hard edge | Fixed height with no scroll affordance | A visible scrollbar or fade, with intended `overflow` |
| Heading breaks mid-word | `word-break: break-all` | `overflow-wrap: anywhere`, which breaks only when needed |
| Wrong initials or a replacement character | Naive first-character code | Initials from grapheme clusters (`Intl.Segmenter`), first and last word, a fallback icon |
| Orphaned separator or empty line | A placeholder rendered for a missing optional field | Omit the line, or reserve its height on purpose |
| "1 members" | Hard-coded plural | `Intl.PluralRules` or separate strings per count |
| Numbers jitter when updating | Proportional figures | `font-variant-numeric: tabular-nums` |
| Raw or unformatted numbers | No locale formatting or null guard | `Intl.NumberFormat` with the user's locale; guard nulls |
| Translated button label overflows | A fixed-width button | Width from content with a `min-width` |
| Tall scripts clipped | Tight line height with `overflow: hidden` | Looser line height, no clipping on text boxes |
| Broken-image icon | No error fallback | Fall back to initials; `object-fit: cover` |
| Truncated text with no way to read it | Ellipsis alone | Make the full value reachable by keyboard, touch, and assistive technology: an expandable row, a detail view, or a copy action. An accessible tooltip can supplement these; `title` alone is not enough, because it is hard to reach without a mouse |
| Scrolling 1,000 rows stutters | Every row rendered | Virtualize or paginate, and say which |
| Literal markup or entities | The wrong escaping layer | Escape once, at render; never inject user data as HTML |

## Truncate, wrap, or clamp

Decide per field:

- **Wrap** what users need in full to identify something, such as names and titles in a detail view; two lines is usually fine, four suggests the column is too narrow.
- **Truncate at the end** secondary metadata whose start carries the meaning, such as a role or message preview, and keep the full value reachable without a pointer.
- **Truncate in the middle** values that differ at the end: file names, emails sharing a long domain, paths, and hashes.
- **Clamp** multi-line previews in cards so card heights stay predictable.
- **Never truncate** numbers, amounts, dates, or anything users compare; give them room.
