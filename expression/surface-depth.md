# Expression — Surface & Depth

## Status

Working specification; exact tiers remain open.

## Principle

> **Depth communicates structure, not decoration.**

## Surface hierarchy

Conceptual semantic surfaces:

- Background
- Surface
- Raised
- Floating
- Overlay
- Modal
- Hero

## Surface vs elevation

**Surface** describes the material treatment.

**Elevation** describes spatial layer.

They are independent:

```text
Surface + translucent
Raised + translucent
Overlay + translucent
```

## Surface treatments

Supported treatments may include:

- solid
- tinted
- outlined
- elevated
- translucent
- glass
- flat

Not every treatment is appropriate everywhere.

## Translucency

Translucency is a supported Sonata treatment, inspired in part by Radix's solid/translucent panel model. It may be useful for toolbars, overlays, dialogs, navigation surfaces and floating controls.

It must preserve contrast and clarify layering.

## Glass

Glassmorphism is not a default identity. Glass is a contextual surface treatment, not an aesthetic mandate.

## Elevation

Conceptual levels:

- 0 — flat
- 1 — separated
- 2 — raised
- 3 — floating
- 4 — modal/hero

Shadow is an implementation of elevation, not the definition of elevation.

Dark-mode implementations may rely more heavily on surface contrast and borders than large shadows.

## Borders

Semantic border strengths:

- none
- subtle
- default
- strong

Borders may communicate separation, geometry or state.

## Material surfaces

Sonata permits surfaces that combine translucency, blur, background interaction, elevation, shape, border and specular/highlight effects where appropriate — this extends the existing translucency and glass decisions (D-011) rather than restating them; the overlay-specific instance is decided in [`../system/overlays.md`](../system/overlays.md) (D-154).

These effects are especially useful for:

- sidebars
- floating panels
- menus
- popovers
- tool surfaces
- sheets
- contextual controls

## Floating material surfaces

A surface may visually float above Content Space while remaining part of the same semantic context.

The background relationship should remain legible.

## Material as optional treatment

Material effects should be strongly supported by Sonata but remain contextual.

They may be widely used when they improve visual hierarchy and spatial understanding.

They must not impair:

- text contrast
- control recognition
- selection
- focus
- data comprehension

## Glass-like treatment

Glass-like visual treatment is an official supported Sonata expression (D-011).

It is not a mandatory appearance for every component.

Its primary purposes are:

- layering
- contextual separation
- visual continuity
- floating relationship

not decoration alone.

## Customization

See [`../customization/shape-surface.md`](../customization/shape-surface.md) for the user/product-facing exposure surface. This file covers the surface hierarchy, treatments and elevation model that surface selects from.

## Open decisions

- blur amounts
- exact elevation mapping
- translucency tiers
- reduced-transparency substitutions
