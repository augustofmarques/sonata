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
