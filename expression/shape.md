# Expression — Shape & Geometry

## Status

Decided: the shape scale token names, the semantic-role list, the five named shape personalities (Subtle/Soft/Rounded/Expressive/Organic), personalities as role→geometry mappings rather than fixed values, and shape/surface independence (D-209–D-211). Open: exact radius values per token/personality, organic-shape vocabulary (see Open questions).

Shape is an expressive and semantic dimension, not a single global border radius.

## Shape scale

Sonata maintains a base geometric scale (D-210):

```text
shape.none
shape.xs
shape.sm
shape.md
shape.lg
shape.xl
shape.2xl
shape.full
```

Do not equate these tokens with a single universal radius across all components — exact per-token, per-personality values remain open.

## Semantic geometry

Components consume semantic shape roles such as (D-210):

```text
shape.control
shape.control-compact
shape.container
shape.card
shape.panel
shape.popover
shape.dialog
shape.floating
shape.hero
shape.indicator
```

The component consumes the role; the active shape personality supplies the resulting geometry.

## Shape Profiles

Sonata defines five named shape personalities (D-209):

- **Subtle** — minimal geometric emphasis. (Previously referred to as "Geometric" in this file and in `governance/glossary.md`; renamed for clarity — "Geometric" read as "more shape," when the intent is the opposite: restrained, low-ornamentation geometry.)
- **Soft** — moderately rounded geometry with restrained character.
- **Rounded** — clearly rounded controls and containers.
- **Expressive** — more pronounced geometric hierarchy and shape contrast.
- **Organic** — shape may incorporate softer or non-rectangular geometry where context permits.

These are personality/profile concepts that map semantic shape roles to concrete geometry, not raw radius values themselves (D-210). See [`../governance/glossary.md`](../governance/glossary.md) for the canonical **Shape Profile** definition.

## Organic geometry

Organic geometry may include:

- asymmetrical corners
- custom silhouettes
- irregular masks
- expressive large-radius surfaces
- morphing shapes

It should be concentrated in expressive contexts and not undermine dense functional interfaces.

Appropriate contexts include hero surfaces, expressive controls, onboarding, empty states, decorative regions and highly expressive product-specific components; use in dense data interfaces should generally be restrained.

## Pill rule

Pill geometry is contextual and semantic. Not every component should become a pill simply because a theme is rounded.

## Nested geometry

Nested surfaces should preserve coherent geometric relationships rather than independently choosing unrelated radii.

## Shape and surface independence

Shape and surface/material are independent dimensions and may be combined freely within accessibility and semantic constraints (D-211).

A rounded rectangle may be:

- solid
- translucent
- glass-like
- outlined
- flat
- elevated

A material surface may in turn be rounded, subtle, organic or custom without requiring one specific geometry.

Similarly, a surface does not require rectangular geometry.

## Rounded floating geometry

Sonata explicitly permits rounded floating rectangles as a common expressive surface (D-171).

These may be used for:

- panels
- menus
- sidebars
- inspectors
- popovers
- tool surfaces
- contextual controls

## Non-rectangular expression

Sonata permits non-rectangular expressive forms where appropriate.

These may include:

- organic shapes
- asymmetrical geometry
- masked surfaces
- custom silhouettes

The shape system must remain coherent with the surrounding interface.

## Platform-inspired material expression

Sonata may draw visual inspiration from contemporary platform material systems, including translucent and layered surfaces, without becoming platform-specific. See [Apple HIG](../references/apple-hig.md) as a secondary reference (D-173).

Shape remains a Sonata semantic/expression concern.

## Customization

See [`../customization/shape-surface.md`](../customization/shape-surface.md) for the user/product-facing exposure surface. This file covers the shape scale, semantic geometry and personalities that surface selects from.

## Open decisions

- exact values
- profile transform rules
- organic-shape vocabulary
