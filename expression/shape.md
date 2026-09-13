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

## Shape and surface independence

Shape does not imply a particular material.

A rounded rectangle may be:

- solid
- translucent
- glass-like
- outlined
- flat
- elevated

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
