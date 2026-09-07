# Expression — Typography

## Status

Architecture decided; exact scale remains open.

Typography is a readability, accessibility and expression system.

## Semantic roles

- Display
- Hero
- Heading
- Title
- Body
- Label
- Caption
- Code
- Numeric

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

Sonata currently recommends the Red Hat family architecture:

- Red Hat Display for headings/display.
- Red Hat Text for UI/body text.
- Red Hat Mono for code/technical text.
- Noto-based locale fallbacks for scripts requiring dedicated coverage.

This is a default, not a mandatory identity. The Red Hat Design System itself documents Display, Text, Mono and locale-specific Noto families as distinct roles. [Reference](../references/typography.md)

## Mono

Monospace is a first-class semantic capability.

`Code` and `Numeric` are not synonyms:

- Code uses mono where it improves code distinction and technical scanning.
- Numeric may use mono or tabular figures depending on data context.

## Numeric typography

Sonata should support, where font features permit:

- proportional figures
- tabular figures
- lining figures
- oldstyle figures
- locale-aware numerals

## Customization

See [`../customization/typography.md`](../customization/typography.md) for the user/product-facing exposure surface (text size, interface scale, typeface, line spacing, advanced typography). This file covers the semantic role and family architecture that surface configures.

## Multilingual behavior

Typography must accommodate script-specific fallback without forcing the application to manually choose a font per string. Sonata should support locale/script family mappings and fallback stacks.

## Desktop / Mobile

Both classes use the same semantic type roles. Mobile generally uses tighter display hierarchy; Desktop may use larger display sizes and richer data typography.

## Open decisions

- exact scale
- variable-font policy
- final fallback stacks
- numeric defaults
