# Visual Direction and Anti-Defaults

Use this reference when a templated visual result is a material risk in landing pages, portfolios, campaigns, expressive product surfaces, or reviews. It adapts selected ideas from Taste Skill without importing that framework’s defaults or blanket aesthetic bans.

**Anti-default:** find decisions made by habit rather than by the brief. This is a diagnostic pass, not a house style. A familiar pattern is correct when it serves the content, audience, system, and outcome.

**Removal is not enough.** Stripping familiar devices without putting content, hierarchy, or identity in their place can leave a thin page that is just as guessable — an "avoidance aesthetic" anyone could predict from the category plus a list of things to avoid. Generated-page tells are dated and contextual: most began as good ideas and became tells by appearing everywhere without a reason. Judge each device by what it explains or does in this context, not by a banlist. The generative step below comes first so that the checks have something specific to protect.

## Workflow

1. **Derive the subject idea.** Build the inventory and idea sentence in [Subject idea](#subject-idea) from the brief and the subject, inside any brand or system authority that already exists. **Complete when:** the idea traces to recorded facts, and each fact is marked as observed or assumed.
2. **Establish direction.** Read the artifact and choose the three qualitative axes in [Direction evidence](#direction-evidence). **Complete when:** type, color, space, shape, imagery, and motion can all be explained by the same direction.
3. **Identify the system authority.** Distinguish an owned design system, an aesthetic reference, and a platform material using [System or aesthetic](#system-or-aesthetic). **Complete when:** the visual source is classified as a design system, an aesthetic reference, or a platform material; any approximation is labeled, and any new-library evaluation is explicitly authorized.
4. **Run the anti-default pass.** Start only after the page has a coherent content and journey structure. Apply every relevant check in [Anti-default checks](#anti-default-checks), and correct a pattern only when both the observation and its consequence are real. **Complete when:** every applicable check has been run, and every correction is tied to a real observation and consequence.
5. **Specify responsive composition.** Cover every non-trivial layout with [Responsive checks](#responsive-checks). **Complete when:** width, height, text size, input method, and content-length changes each have an intentional, legible result.
6. **Verify the rendered endpoint.** Apply [Endpoint verification](#endpoint-verification). **Complete when:** all six questions pass and the result is coherent and specific to its context, rather than merely different from common templates.

## Subject idea

A direction is a way of composing; an idea is what makes the page belong to this subject and no other. Derive it from the subject before choosing styling.

**Inventory.** List facts that belong to this product, organization, or audience and not to its category: its name and what the name means; its place and what that place looks like; its materials and colors; the numbers in the brief; the constraint it lives with; its rituals and hours; its output; and the printed or physical things of its world, such as a ticket, a label, or a manual. Collect enough to choose from — the source works from eight to twelve, which is a recipe, not a minimum. Mark each fact as observed (from the brief, the product, or research) or assumed, and never invent history, places, or details to fill the list.

**Idea sentence.** Write it before styling:

> On this page, **[a fact about this subject]** becomes **[a visual or interaction device]**.

For example: on a page for a furniture maker that cuts each seat from one board, the grain of the customer's own board becomes the page's recurring image.

**Competitor test.** Put the nearest real competitor in the sentence. If it still works, the idea belongs to the category; look again at the inventory. Use the test to judge specificity, not as a gate: an app surface or a standard system screen, where consistency and familiarity win, need no distinctive idea, and brand or system authority still governs the result.

**One live thing.** A candidate, not a requirement: one interaction made from the idea, when it demonstrates value, proves a claim, or performs a real task — for example, choosing a wood and seeing the chair in it, or setting a loan amount and reading the real monthly figure. Build it only with truthful content, operable by keyboard and touch, with a plain fallback that works without script, and never blocking reading. It is not a minimum quantity of interaction or an excuse for more ornament or motion. An existing product can show a truthful preview of itself; never fake live data.

## Direction evidence

Read these sources before choosing a visual language:

- page kind and the job of each section;
- audience, buying or use context, and expected level of trust;
- words, references, screenshots, competitors, and brands named by the user;
- existing logo, type, palette, imagery, tokens, and component system;
- accessibility, regulatory, performance, content, and platform constraints.

Describe the direction on three qualitative axes:

| Axis | Restrained | Balanced | Expressive |
| --- | --- | --- | --- |
| **Visual variance** | Repeated grid, symmetry, predictable alignment | Selected offsets and mixed proportions | Strong asymmetry and deliberate compositional contrast |
| **Motion intensity** | Immediate state changes and functional feedback | Short transitions and a few explanatory sequences | Choreographed motion reserved for rare or narrative moments |
| **Information density** | Airy, one idea at a time | Normal product or marketing density | Compact comparison or expert scanning |

**Boundary:** the axes describe a direction; they are qualitative descriptors, not scores or acceptance metrics. Derive them from evidence rather than a universal preset.

**Responsive target:** collapse expressive compositions to an explicit, legible small-screen arrangement.

## System or aesthetic

Use the source’s actual authority:

- **Design system:** supplies components, tokens, interaction contracts, and accessibility behavior.
- **Aesthetic reference:** editorial, brutalist, bento, glass, dark-tech, kinetic type, or another aesthetic supplies visual inspiration rather than an official package.
- **Platform material:** a material such as Apple Liquid Glass may have no official web implementation. Label any web approximation honestly.

**Decision:** reuse a compatible installed system. Evaluate a new library only when the user explicitly asks for selection, installation, or replacement; then use `ui-library-selection.md` and current primary documentation.

**Boundary:** treat dependency migration as separately authorized. Visual resemblance alone does not authorize it.

## Anti-default checks

### Layout repetition

**Decision:** give each content job a fitting composition. Reuse a layout when repeated structure communicates a real relationship, such as comparable plans, records, steps, or products.

**Rationale:** mechanical repetition makes unrelated sections appear equivalent and exposes template-driven construction.

**Check:** name the job and layout family of each section. Repeated families need a structural reason. Replace accidental runs with a composition suited to the next content job rather than arbitrary decoration. To decide which sections exist and in what order on a marketing page, use **Section argument** in `conversion-and-landing-pages.md`.

### Hero discipline

**Decision:** keep the initial view focused on promise, supporting context, and the next meaningful action. Size copy and media together so the hierarchy works at relevant viewport heights.

**Rationale:** labels, proof, feature lists, pricing, and several actions in the hero make every element compete before the user understands the offer.

**Check:** inspect common desktop and mobile viewport heights. Keep the value proposition and primary action legible without clipping or accidental wrapping. Place secondary proof and detail in the section that can explain it.

**Override:** an editorial manifesto or launch can make typography itself the primary visual when that is the declared direction.

### Labels and metadata

**Decision:** use labels, eyebrows, pills, numbering, status dots, and separators when they classify content or convey real state.

**Rationale:** repeated micro-labels create synthetic complexity and a uniform AI-generated rhythm.

**Check:** remove each label mentally. If navigation, meaning, or state remains unchanged, treat the label as decoration. Prefer a clear heading, grouping, whitespace, or semantic status treatment instead.

### Cards, shape, and depth

**Decision:** use a card when containment or elevation communicates hierarchy. Otherwise, group with proximity, alignment, background, or a restrained separator. Keep radius and depth choices on a small, explainable scale.

**Rationale:** the same rounded rectangle around every item flattens hierarchy and makes unrelated content look interchangeable.

**Check:** every surface should explain why it is bounded or elevated. Exceptions to the radius or shadow system need a semantic or material reason.

### Typography

**Decision:** derive type from brand, content, platform, and legibility. Build hierarchy with size, weight, line height, tracking, and measure together.

**Rationale:** fashionable font swaps do not create direction and can damage loading, language coverage, or readability.

**Check:** verify body measure, uppercase tracking, display-line clipping, fallback metrics, text scaling, and font loading. Preserve underlines as a reliable link affordance; use weight or color for non-link interface emphasis where appropriate.

**Override:** an established product typeface remains authoritative even when it is common. Novelty is not a reason to replace it.

### Color and theme

**Decision:** use a coherent semantic palette whose accents, neutrals, and themes preserve hierarchy and contrast. Support the modes the product officially owns.

**Rationale:** arbitrary accent changes and unrelated section inversions make one page feel assembled from several templates.

**Check:** trace each color to a token, content meaning, brand role, or deliberate composition. Test text and controls against their actual backgrounds in every supported theme.

### Imagery and product proof

**Decision:** represent real products with approved assets, truthful screenshots, or functioning previews. Mark generated, stock, placeholder, and mock material honestly.

**Rationale:** fake dashboards, invented logos, and fabricated precision can be mistaken for product proof and weaken trust.

**Check:** every asset needs a source, permission or approved-placeholder status, suitable dimensions, alt treatment, and light/dark behavior where relevant. When a needed asset is missing, leave a precise placement requirement rather than disguising a fabrication as shipped reality.

**Override:** a clearly labeled prototype may use mock content to answer its question. Keep that mock content from becoming production evidence by accident.

**Open collections.** When the project has no imagery of its own, real pictures of the subject's world — its place, maps, materials, trade history, or museum objects of its kind — may exist in open collections such as Openverse, Wikimedia Commons, the Art Institute of Chicago, or the Metropolitan Museum of Art. These are examples, not endorsed sources. Search the inventory from [Subject idea](#subject-idea), not the category. For each candidate:

1. Open the original item page, not only a search result or an aggregator entry.
2. Check that its license allows the intended use, including commercial use and adaptation if you will crop, recolor, or combine it. CC0, public-domain, CC BY, and CC BY-SA items are candidates; attribution alone is not a license. CC BY-SA terms apply to the adapted image you publish, not automatically to the whole site.
3. Check for personality rights, trademarks, and jurisdiction limits, such as public domain only in the United States, and for archive statements that replace a license.
4. Record the creator, title, source URL, license and license link, version or retrieval date, and any edits you made; credit the item where the license requires it.
5. When implementation is authorized, store the file through the project's approved asset pipeline rather than hotlinking it from the archive.

A found picture shows the world around the subject. Never present it as the product, team, customers, place, or work of the organization the page is about; the truth boundary above remains authoritative. There is no minimum number of pictures, and a photograph is not always better than a drawing made for the subject.

### Copy register

**Decision:** use one voice appropriate to the audience and page. Prefer concrete claims, verbs, labels, and proof over category slogans or ornamental microcopy.

**Rationale:** forced metaphors, fake humility, unexplained precision, and abrupt register changes make content less credible and harder to scan.

**Check:** reread every visible string, including actions, labels, errors, captions, alt text, and footer text. Repair unclear referents, unsupported claims, broken grammar, duplicate action intent, and unlabeled mock data.

### Motion

**Decision:** give each animation a named job: feedback, state indication, continuity, explanation, or rare delight. Use `motion-and-interaction.md` for implementation and verification.

**Rationale:** ambient motion added to make a page feel premium competes with content and creates accessibility and performance cost.

**Check:** remove the animation mentally. If comprehension and feedback are unchanged, give the motion a stronger purpose or omit it. Verify reduced motion and interruption at the rendered endpoint.

## Responsive checks

Framework breakpoints are implementation tools; the rendered result is the evidence. For every non-trivial layout, check:

- reading and focus order after visual rearrangement;
- navigation fit and reachable controls;
- headlines, actions, and localized strings wrapping naturally;
- media cropping and reserved dimensions;
- touch targets and hover-independent discovery;
- large text, zoom, and narrow viewport behavior;
- wide layouts collapsing to an intentional single-column or grouped alternative.

## Endpoint verification

Use the shortest checklist that covers the selected direction:

1. Can every major section state its content job and visual hierarchy?
2. Are repeated patterns communicating real equivalence rather than convenience?
3. Do type, color, shape, depth, imagery, and motion follow one explainable language?
4. Are claims, proof, assets, and data truthful or clearly labeled as mock?
5. Does the composition remain understandable in relevant responsive, accessibility, and theme states?
6. Was feel observed in a rendered artifact rather than inferred from static code alone?

**Look and correct.** Answer the questions from rendered screenshots at the supported widths, not from the code's intent. Record what is visible separately from what the code was meant to do, and order problems by user impact using the direct review contract in `SKILL.md`. When implementation is authorized, fix the most important problems and look again at the new render; in a read-only review, report the fixes without editing. Screenshots cannot establish keyboard behavior, accessibility, interaction feel, or correctness; the runtime checks owned by the active workflow still apply.
