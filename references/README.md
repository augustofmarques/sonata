# Sonata References

Sonata is a composed design language. References are grouped by role rather than treated as equally normative.

## Normative foundation

- GNOME Human Interface Guidelines — the principal source for structure, interaction, accessibility, writing and content principles.

## System references

- Radix Primitives — composable, accessible, unstyled primitives suitable as the base of a design system.
- Radix Themes / Colors — reference for tokenized theming, color scales, alpha colors, radius, spacing, typography, scaling and panel translucency.

## Expression references

- **Material 3 Expressive** — the primary reference for Sonata's Expression layer: color, typography, shape, motion, animation, visual emphasis, expressive composition, hero moments and personalization (D-172). See `material-expressive.md`.
- Material 3 — supporting reference for the underlying color/tonal systems (source color, dynamic color, tonal palettes) that Material 3 Expressive builds on. See `material.md`.
- Material Color Utilities — reference implementation for HCT, tonal palettes and dynamic scheme generation.

## Adaptive/system-adjacent reference

- Apple Human Interface Guidelines — a secondary reference for platform-aware interaction, adaptive navigation, toolbars, sidebars, sheets, popovers and material/surface expression (D-173). Does not override GNOME HIG. See `apple-hig.md`.

## Typography reference

- Red Hat Design System — recommended default family architecture for Display, Text, Mono and non-Latin Noto fallbacks.

## Iconography reference

- Radix Icons — one optional, non-normative compatible icon source (see `radix.md`). Sonata specifies the iconography contract (`../expression/iconography.md`), not a mandatory icon family; Lucide, Phosphor, native platform iconography and custom iconography are equally compatible provided they satisfy that contract.

The Sonata specification adopts selected ideas from these sources. It does not inherit their complete UX or visual identity.
