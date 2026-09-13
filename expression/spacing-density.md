# Expression — Spacing & Density

## Status

Decided: the v1 candidate spacing baseline, semantic spacing aliases, Balanced as the default density, the Comfortable/Balanced/Compact/Dense profile taxonomy, density-by-class availability, and the density-vs-scale independence (D-205–D-209). Open: exact per-profile transform tables (see Open questions).

Spacing defines spatial relationships. Density defines how much information and interaction surface is presented within available space.

## Core principle

> **Density is compositional, not merely reduced padding.** (D-012, D-208)

Density may coordinate:

- spacing
- control height
- row height
- grouping
- toolbar density
- navigation density
- information exposure
- panel spacing
- content separation
- related icon sizing
- contextual typography metrics where appropriate

Typography scale and interface scale remain related but distinct concerns.

## Spacing scale

Sonata adopts the following spacing baseline (D-205):

```text
space.0   = 0
space.1   = 2
space.2   = 4
space.3   = 6
space.4   = 8
space.5   = 12
space.6   = 16
space.7   = 20
space.8   = 24
space.9   = 32
space.10  = 40
space.11  = 48
space.12  = 64
space.13  = 80
space.14  = 96
```

This is a **Sonata v1 candidate baseline** — concrete enough to build against, not frozen forever. It deliberately includes 2 and 6 for optical alignment and micro-spacing while retaining the familiar 4/8/12/16/24/32/40/48/64 rhythm this file previously described only as a reference rhythm.

## Semantic spacing aliases

Components and layout should prefer semantic aliases over raw scale values (D-205):

```text
space.control
space.control-inline
space.group
space.section
space.panel
space.content-gutter
space.page
```

## Density profiles

Sonata defines four official density profiles (D-207):

- **Comfortable** — generous spacing and lower information density; prioritizes breathing room and relaxed scanning. Increases surrounding spacing, group separation and control breathing room without unnecessarily increasing every visual dimension.
- **Balanced** — the default Sonata density (D-206). Balances readability, efficiency, available information and spatial clarity.
- **Compact** — prioritizes information density while preserving comfortable interaction. Reduces secondary spacing, control padding, row height and group gaps before reducing essential readable typography or interaction targets.
- **Dense** — prioritizes high information throughput for professional workflows. May substantially reduce non-essential spacing and row heights while preserving readable text, semantic clarity, accessibility and minimum usable targets appropriate to the interaction modality. Primarily intended for Desktop Class and selected large Adaptive/Tablet contexts.

This is the general decision Data Display's own density decision already applies to tables (D-066).

## Density by interaction class

Sonata's adaptive classes are Mobile, Adaptive and Desktop (D-015); "Tablet" below refers to Adaptive-Class environments large enough for it, not a fourth class name (D-208):

```text
Mobile:
    Comfortable
    Balanced
    Compact

Adaptive (incl. Tablet):
    Comfortable
    Balanced
    Compact
    Dense (conditional)

Desktop:
    Comfortable
    Balanced
    Compact
    Dense
```

Tablet/Adaptive `Dense` availability depends on window size, input modality, application complexity and interaction target requirements.

## Density and scale independence

Density is independent from Interface Scale and Typography Scale:

```text
Density ≠ Interface Scale
Density ≠ Typography Scale
```

Valid combinations include:

```text
Compact + Large Text
Dense + Standard Scale
Comfortable + Small Interface Scale
```

Applications must ensure these combinations remain usable.

## User customization

See [`../customization/density.md`](../customization/density.md) for the user/product-facing exposure surface (density profiles). This file covers the reference spacing scale and compositional model that surface configures.

## Desktop

Desktop may expose all density profiles when the workflow benefits from them.

## Mobile

Mobile should normally constrain density to Comfortable through Compact. Dense presentation must not violate touch usability, readability or focus requirements.

## Alignment

Spacing and shape must preserve shared alignment contexts. Changing density must not cause visually related controls to lose alignment.

## Scale relationship

Interface scale may change typography, control dimensions, spacing and icon proportions together. It is not synonymous with density.

## Open decisions

- exact density transform tables per profile (which spacing-scale step each profile maps each token to)
- whether spacing and density are exposed separately
- exact mobile limits
