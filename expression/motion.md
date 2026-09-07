# Expression — Motion & Animation

## Status

Architecture decided; exact timings remain open.

Motion communicates causality, continuity, hierarchy, state and feedback.

## Motion levels

- Instant
- Fast
- Standard
- Emphasized
- Expressive

## Motion preference

See [`../customization/motion.md`](../customization/motion.md) for the user/product-facing exposure surface (Full/Reduced/Minimal/Off) and its relationship to the system reduced-motion accessibility constraint.

## Priority

```text
Functional
  ↓
Supportive
  ↓
Expressive
  ↓
Decorative
```

Reduced-motion modes should remove decorative motion first and replace essential movement with static or low-motion equivalents.

## Adaptive motion

Desktop and Mobile may use different motion amplitudes, durations and interaction feedback while preserving semantic intent.

## Open decisions

- duration table
- easing functions
- spring model
- reflow/reveal animation rules
- haptic integration
