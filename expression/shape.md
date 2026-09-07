# Expression — Shape & Geometry

## Status

Architecture decided; exact values remain open.

Shape is an expressive and semantic dimension, not a single global border radius.

## Shape scale

Conceptual scale:

- none
- xs
- sm
- md
- lg
- xl
- 2xl
- full

## Semantic geometry

Components may map to roles such as:

- control
- container
- surface
- overlay
- indicator
- hero

The component consumes the role; the theme supplies the resulting geometry.

## Shape Profiles

Sonata supports named visual directions such as:

- Geometric
- Soft
- Rounded
- Expressive
- Organic

These are personality/profile concepts, not raw radius values. See [`../governance/glossary.md`](../governance/glossary.md) for the canonical **Shape Profile** definition.

## Organic geometry

Organic geometry may include:

- asymmetrical corners
- custom silhouettes
- irregular masks
- expressive large-radius surfaces
- morphing shapes

It should be concentrated in expressive contexts and not undermine dense functional interfaces.

## Pill rule

Pill geometry is contextual and semantic. Not every component should become a pill simply because a theme is rounded.

## Nested geometry

Nested surfaces should preserve coherent geometric relationships rather than independently choosing unrelated radii.

## Customization

See [`../customization/shape-surface.md`](../customization/shape-surface.md) for the user/product-facing exposure surface. This file covers the shape scale, semantic geometry and personalities that surface selects from.

## Open decisions

- exact values
- profile transform rules
- organic-shape vocabulary
