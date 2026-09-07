# Customization — Overview

Customization is a first-class Sonata capability.

The system distinguishes:

```text
Capability
    vs
Exposure
```

Sonata may support a customization capability without requiring every application to expose it.

## High-priority candidates

- theme
- accent
- typography scale
- interface scale
- spacing/density
- motion

## Secondary candidates

- shape
- surface style
- translucency
- contrast
- font family
- line spacing

## Per-domain detail

- [Color](color.md)
- [Typography](typography.md)
- [Density](density.md)
- [Shape & Surface](shape-surface.md)
- [Motion](motion.md)
- [Accessibility](accessibility.md)

Each of these files describes the user/product-facing exposure surface for its domain. The corresponding `expression/*.md` file describes the underlying technical mechanism the exposure surface controls — see the [Token Resolution Model](../system/resolution-model.md) for how a user's choice here becomes a rendered value.

## System-component customization

Actions, Inputs, Navigation and Data Display are System-layer components rather than Expression domains, so they do not get a separate `customization/*.md` counterpart (see [D-025](../governance/decision-log.md#d-025--expressioncustomization-split-of-authorship)) — each documents its own customization surface inline in its `system/*.md` file. For Data Display, that includes columns, column order, column size, visible data, sorting, grouping, filters, visible panels, inspector visibility and workspace-specific data presentation (see [`../system/data-display.md`](../system/data-display.md)). These configurations use Sonata's token and workspace systems rather than arbitrary per-component styling.
