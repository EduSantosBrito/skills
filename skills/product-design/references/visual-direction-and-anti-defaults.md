# Visual Direction and Anti-Defaults

Use this reference when a templated visual result is a material risk in landing pages, portfolios, campaigns, expressive product surfaces, or reviews. It adapts selected ideas from Taste Skill without importing that framework’s defaults or blanket aesthetic bans.

**Anti-default:** find decisions made by habit rather than by the brief. This is a diagnostic pass, not a house style. A familiar pattern is correct when it serves the content, audience, system, and outcome.

## Workflow

1. **Establish direction.** Read the artifact and choose the three qualitative axes in [Direction evidence](#direction-evidence). **Complete when:** type, color, space, shape, imagery, and motion can all be explained by the same direction.
2. **Identify the system authority.** Distinguish an owned design system, an aesthetic reference, and a platform material using [System or aesthetic](#system-or-aesthetic). **Complete when:** the visual source is classified as a design system, an aesthetic reference, or a platform material; any approximation is labeled, and any new-library evaluation is explicitly authorized.
3. **Run the anti-default pass.** Start only after the page has a coherent content and journey structure. Apply every relevant check in [Anti-default checks](#anti-default-checks), and correct a pattern only when both the observation and its consequence are real. **Complete when:** every applicable check has been run, and every correction is tied to a real observation and consequence.
4. **Specify responsive composition.** Cover every non-trivial layout with [Responsive checks](#responsive-checks). **Complete when:** width, height, text size, input method, and content-length changes each have an intentional, legible result.
5. **Verify the rendered endpoint.** Apply [Endpoint verification](#endpoint-verification). **Complete when:** all six questions pass and the result is coherent and specific to its context, rather than merely different from common templates.

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

**Check:** name the job and layout family of each section. Repeated families need a structural reason. Replace accidental runs with a composition suited to the next content job rather than arbitrary decoration.

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
