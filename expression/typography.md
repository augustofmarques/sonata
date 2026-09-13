# Expression — Typography

## Status

Decided: the family architecture (D-008), semantic type roles, a v1 candidate concrete scale for Body/Heading/Display/Label/Caption/Code, the Body baseline (16/24) and minimum ordinary text size, numeric typography modes, the weight vocabulary, typography-vs-interface-scale independence, typography expression levels, optical alignment as a first-class principle, locale-aware typography dimensions, variable-font and optical-sizing preference, rendering independence, hyphenation, and the typography contract for alternative font systems (D-212–D-230). Open: exact letter-spacing values, exact weight mapping per default family, exact Display/Heading transition rules, exact font preset catalog, exact locale/script fallback matrix, exact hyphenation policy per platform, exact optical-alignment heuristics, exact Interface Scale multipliers (see Open questions).

Typography is a readability, accessibility and expression system.

## Semantic roles

Official Sonata semantic typography roles (D-213):

- Display
- Hero
- Heading
- Title
- Body
- Label
- Caption
- Code
- Numeric

These roles describe purpose, not implementation-specific font names.

## Family roles

```text
Text/UI family
Display family
Mono family
Numeric family (optional)
Locale/script fallback families
```

A product may use the same family for several roles.

## Recommended default

Sonata currently recommends the Red Hat family architecture (D-008):

- Red Hat Display for headings/display.
- Red Hat Text for UI/body text.
- Red Hat Mono for code/technical text.
- Noto-based locale fallbacks for scripts requiring dedicated coverage.

This is a default, not a mandatory identity. The Red Hat Design System itself documents Display, Text, Mono and locale-specific Noto families as distinct roles. [Reference](../references/typography.md)

## Concrete typography scale (v1 candidate)

Sonata adopts the following v1 candidate typography scale — concrete enough to build against, subject to component validation before final freezing (D-214). Format is `font-size / line-height`.

### Body / UI scale

```text
type.body.xs    = 12 / 18
type.body.sm    = 14 / 21
type.body.md    = 16 / 24
type.body.lg    = 18 / 27
type.body.xl    = 20 / 30
type.body.2xl   = 24 / 36
```

`type.body.md` at `16 / 24` is the default Body baseline (D-215), aligning with Red Hat's current 16px base and body scale.

### Heading scale

```text
type.heading.xs    = 20 / 26
type.heading.sm    = 24 / 31
type.heading.md    = 28 / 36
type.heading.lg    = 32 / 40
type.heading.xl    = 36 / 46
type.heading.2xl   = 40 / 52
type.heading.3xl   = 48 / 62
```

The first six levels are intentionally close to Red Hat's current heading system, with a larger upper range for Sonata.

### Display scale

```text
type.display.sm    = 48 / 56
type.display.md    = 56 / 64
type.display.lg    = 64 / 72
type.display.xl    = 80 / 88
type.display.2xl   = 96 / 106
```

Display is intended for high-level composition, major titles and expressive contexts — intentionally closer to expressive ranges seen in Red Hat and Material rather than treating every heading as a display style.

### Hero

Hero is a semantic role rather than a single fixed size. Hero may use 64, 80 or 96, and may combine larger size, stronger weight, tighter or expressive tracking, modified line-height, the Display family and animation where applicable. Hero typography is contextual.

### Label scale

```text
type.label.sm    = 12 / 16
type.label.md    = 14 / 20
type.label.lg    = 16 / 24
```

Labels may use Medium or another suitable emphasis weight. Labels should not be reduced below their minimum practical size merely to conserve layout space.

### Caption

```text
type.caption = 12 / 18
```

Caption remains secondary information. Do not use Caption as a general-purpose compact body style.

### Code scale

Code follows the body size relationship:

```text
type.code.xs    = 12 / 18
type.code.sm    = 14 / 21
type.code.md    = 16 / 24
type.code.lg    = 18 / 27
type.code.xl    = 20 / 30
type.code.2xl   = 24 / 36
```

Recommended default family: Red Hat Mono. Code remains semantically distinct from ordinary UI text even where they share the same nominal size.

## Separate semantic scales

Sonata uses distinct Body/UI, Heading, Display and Code scale families rather than one universal size ladder (D-217). `Body` and `UI/Label` remain separate semantic systems even when their concrete size is identical — e.g. `body.md = 16/24` and `label.lg = 16/24` share a size but evolve independently because their semantic roles differ.

## Minimum ordinary text

12px is the minimum recommended ordinary text size (D-216). Smaller type requires strong contextual justification and should not be used simply to recover layout space.

## Kbd / shortcut typography

Keyboard shortcut and `kbd` presentation should use Sonata UI typography by default, not automatically switch to monospace (D-230). Monospace may be used when the visual semantics of a technical representation justify it.

## Mono

Monospace is a first-class semantic capability.

`Code` and `Numeric` are not synonyms (D-009):

- Code uses mono where it improves code distinction and technical scanning.
- Numeric may use mono or tabular figures depending on data context.

## Numeric typography

Numeric typography is a distinct semantic concern with proportional, tabular and monospace modes and locale-aware numeral support (D-218, D-009):

```text
numeric.proportional
numeric.tabular
numeric.monospace
```

Defaults: use proportional numerals for ordinary prose; tabular numerals for tables, aligned metrics, counters, dashboards, financial values and repeated numeric columns; monospace when technical identity or fixed-width presentation is semantically useful. Numeric typography is separate from Code even when both use a monospaced family.

## Weight vocabulary

Sonata defines semantic weight roles (D-219):

```text
Regular
Medium
Bold
```

Additional weights are permitted when the selected typeface supports them and the context benefits from them.

Default guidance:

```text
Body            → Regular
UI / labels     → Regular or Medium
Headings        → Medium or stronger as appropriate
Hero / emphasis → Medium / Bold / family-specific expressive weight
```

Bold is permitted in body text when useful, but Red Hat's current body guidance recommends Medium and italics for emphasis and avoids indiscriminate Bold use; Sonata retains this as the default recommendation while allowing contextual variation.

## Tracking

Tracking is part of each semantic type style and must be defined per style rather than globally.

```text
small text      → neutral or slightly positive tracking
body            → near-neutral tracking
large headings  → neutral to slightly negative tracking when optically appropriate
display / hero  → context-dependent
```

Tracking may be adjusted by the selected typeface. Tracking must be judged visually rather than only numerically — the same numeric letter-spacing value may not produce equivalent results across fonts or scripts.

## Line height

Every semantic style must define its own line height rather than applying one universal ratio (1.2, 1.4, 1.5, ...) to all typography. Line height should reflect size, family, language/script, text length, density and container width. Large multi-line text must not use excessively tight leading merely to save vertical space.

## Typography scale customization

Official text-scale profiles: Small, Standard, Large, Extra Large, with Standard as default. Changing text scale must trigger layout adaptation (D-220):

```text
Reflow → wrap → increase container → increase region height → progressive disclosure → alternate composition
```

Do not simply reduce typography until enlarged user text fits. When large text causes wrapping: wrapping is acceptable, increased height is acceptable, hyphenation may be used where language rules support it (D-228), horizontal reflow is preferred over clipping, and truncation should not be used merely to preserve a fixed height. See [`../customization/typography.md`](../customization/typography.md).

## Interface Scale

```text
Text Scale       → typography only
Interface Scale  → typography + control dimensions + icon sizing + relevant spacing
```

These remain independent user preferences (D-220).

## Density relationship

Density does not automatically modify typography size (D-220):

```text
Density          → spacing / dimensions / information packing
Typography Scale → text size and typographic metrics
```

Small contextual adjustments may exist where necessary for a specific component, but density does not globally shrink type. See [Spacing & Density](spacing-density.md).

## Typography expression

Sonata defines an independent expressive typography axis (D-221):

```text
Standard
Expressive
Hero
```

Expression may alter scale, weight, tracking, line-height, family selection where allowed, display treatment and motion where applicable. Expressive typography should primarily affect headings, display content and hero contexts rather than turning ordinary UI text into decorative typography.

## Typography animation

Typography may participate in Sonata Motion when a semantic state transition benefits from it (D-222): number count transitions, expanding titles, state changes, hero transitions, onboarding demonstrations. Do not animate ordinary body text merely because animation is available.

## Optical alignment

Optical alignment is a first-class Sonata principle: perceived alignment takes precedence over mathematical bounding-box alignment when the two conflict (D-223, Principle 67). This generalizes the icon-specific Optical Alignment already defined in [`../governance/glossary.md`](../governance/glossary.md) to typography and UI generally.

Geometric and optical alignment are not always identical. The implementation must consider glyph shapes, italic overhangs, ascenders/descenders, punctuation, font metrics, icon geometry, container geometry, corner/radius perception, visual center and stroke distribution.

Examples: italic text may extend beyond its nominal box; icon + label may require optical rather than mathematical centering; pill + text baseline and visual mass may require compensating alignment. Text should not automatically be aligned solely according to glyph bounding boxes when the surrounding container, pill, button, icon, border or baseline appears visually misaligned — the goal is perceived alignment.

## Customization

See [`../customization/typography.md`](../customization/typography.md) for the user/product-facing exposure surface (text size, interface scale, typeface, line spacing, advanced typography). This file covers the semantic role and family architecture that surface configures.

## Multilingual behavior

Typography must accommodate script-specific fallback without forcing the application to manually choose a font per string. Locale/script-specific typography is official (D-224, D-019):

```text
type.family.locale.latn
type.family.locale.cyrl
type.family.locale.arab
type.family.locale.hebr
type.family.locale.hans
type.family.locale.hant
type.family.locale.jpan
type.family.locale.kore
type.family.locale.deva
...
```

Fallback must be predictable. Locale-specific families may differ in font family, weight, line-height, tracking, optical sizing and metrics when required for equivalent legibility. See [`../foundation/i18n.md`](../foundation/i18n.md).

## RTL

Typography must participate in RTL layout: alignment, direction, punctuation, numeric behavior where applicable, icon placement when directionally meaningful, indentation and navigation. Do not treat RTL as simply mirrored typography.

## Font features

Where supported, Sonata may use tabular figures, lining figures, localized forms, stylistic alternatives, kerning and optical sizing. Applications should not require these features when the selected platform/font cannot provide them.

## Variable fonts

Variable fonts are preferred when available (D-225), enabling more precise weight, optical size, width and interpolation, without requiring Sonata to mandate them.

## Optical sizing

When the selected font supports optical sizing, Sonata may enable it (D-226). Optical sizing should be preferred over manually approximating large/small text through arbitrary tracking or scaling.

## Rendering

Font rasterization and anti-aliasing remain platform implementation concerns (D-227). Sonata does not mandate a specific rasterizer. Sonata's visual reference baseline favors smooth, high-quality, high-fidelity text rendering resembling contemporary macOS-quality typography where the platform permits it. The implementation must adapt to platform capabilities rather than attempting to force a single rasterization technology.

## Typography presets

Applications may expose additional font presets in Settings (D-212). A preset should define a coherent UI family, Display family, Mono family, numeric behavior and locale fallback — rather than changing only the body font.

Recommended baseline:

```text
Sonata → Red Hat Display → Red Hat Text → Red Hat Mono → Noto / locale fallbacks
```

Other curated presets may be offered when they maintain the Sonata contract. Users may also choose a custom font where the application supports it.

## Typography contract

Any font system compatible with Sonata must provide or map UI, Display, Mono, Numeric and Locale fallback roles and support the semantic type roles (D-229). A family does not need to literally provide separate Display/Text/Mono faces if the application can map the roles coherently.

## Foundation writing relationship

Typography does not override Foundation writing rules. Sentence case, terminology, clarity and other writing decisions remain governed by the Foundation.

## Desktop / Mobile

Both classes use the same semantic type roles. Mobile generally uses tighter display hierarchy; Desktop may use larger display sizes and richer data typography. See [`../adaptive/mobile.md`](../adaptive/mobile.md) and [`../adaptive/desktop.md`](../adaptive/desktop.md).

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Typography) for what remains open: exact letter-spacing values, exact weight mapping per default font family, exact Display/Heading transition rules, exact font preset catalog, exact locale/script fallback matrix, exact hyphenation policy per platform, exact optical-alignment heuristics, and exact Interface Scale multipliers.
