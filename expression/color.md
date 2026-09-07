# Expression — Color

## Status

Architecture decided; exact generation algorithm remains open.

## Color model

This is color's domain-specific generation algorithm — it runs inside the "Sonata defaults" and "Application theme" steps of the token resolution model's Precedence axis (Axis B). See [`../system/resolution-model.md`](../system/resolution-model.md).

Sonata uses a hybrid architecture:

```text
Source Color
   ↓
Tonal / perceptual generation
   ↓
Sonata palette scale
   ↓
Semantic roles
   ↓
Components
```

The scale anatomy is inspired by Radix's multi-step semantic color scales and alpha variants. The generation logic is inspired by Material's source-color → tonal palette → semantic role model, including HCT concepts and explicit contrast constraints. [Radix Colors](https://www.radix-ui.com/themes/docs/theme/color) [Material Color Utilities](https://github.com/material-foundation/material-color-utilities/blob/main/concepts/dynamic_color_scheme.md)

## Palette families

- Accent
- Secondary
- Tertiary
- Neutral
- Success
- Warning
- Danger
- Info

## Scale

Primary palette families should expose a consistent multi-step scale and alpha/translucent variants.

## Semantic roles

Components must consume semantic roles, not raw palette steps.

Examples:

- `color.background`
- `color.surface`
- `color.text`
- `color.border`
- `color.accent`
- `color.selection`
- `color.focus`
- `color.overlay`

## Personalization

See [`../customization/color.md`](../customization/color.md) for the user/product-facing exposure surface (curated accent, advanced custom input, neutral identity). This file covers the generation mechanism that surface relies on.

## Semantic safety

Success, warning, danger and info retain their semantic distinctions. Customization may change tone/chroma within accessible limits but should not destroy semantic recognition.

## Modes

- Light
- Dark
- System
- High Contrast / accessibility transformations

Light and dark use distinct mappings; dark mode is not simple color inversion.

## Expressiveness

Color intensity may vary by composition or theme without changing semantic structure.

## Future source modes

Potential source color inputs:

- application theme
- curated preset
- user-selected color
- image-derived color

## Open decisions

- exact generation algorithm
- exact scale values
- curated palette
- secondary/tertiary generation
- image extraction rules
