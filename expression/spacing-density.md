# Expression — Spacing & Density

## Status

Working specification; exact values remain open.

Spacing defines spatial relationships. Density defines how much information and interaction surface is presented within available space.

## Core principle

> **Density is compositional, not merely reduced padding.**

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

Typography scale and interface scale remain related but distinct concerns.

## Reference scale

Initial reference rhythm:

`4 / 8 / 12 / 16 / 24 / 32 / 40 / 48 / 64`

This is a starting scale inspired by the systemic spacing approach of Radix Themes. Exact Sonata values remain open.

## Density profiles

- Comfortable — generous spacing and lower information density.
- Balanced — default general-purpose mode.
- Compact — increased information efficiency.
- Dense — specialized power-user mode, primarily Desktop.

## User customization

See [`../customization/density.md`](../customization/density.md) for the user/product-facing exposure surface (density profiles). This file covers the reference spacing scale and compositional model that surface configures.

## Desktop

Desktop may expose all density profiles when the workflow benefits from them.

## Mobile

Mobile should normally constrain density to Comfortable through Compact. Dense presentation must not violate touch usability, readability or focus requirements.

## Scale relationship

Interface scale may change typography, control dimensions, spacing and icon proportions together. It is not synonymous with density.

## Open decisions

- exact token values
- transform tables for each profile
- whether spacing and density are exposed separately
- exact mobile limits
