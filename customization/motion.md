# Customization — Motion

Motion is a high-priority customization category because it directly affects comfort and user experience.

## Motion preference levels

- Full
- Reduced
- Minimal
- Off

Applications may expose fewer levels than the full set.

See [`../expression/motion.md`](../expression/motion.md) for the underlying Sonata motion architecture, including motion levels, priority, organic motion, morphing, adaptive behavior and haptic interaction.

## Constraint

System-level reduced-motion requirements are an accessibility constraint (see [Accessibility](accessibility.md)), not merely a preference.

They must be respected even when an application does not expose its own motion control.

## Principle

Customization changes the amount and intensity of motion; it must not remove necessary state communication or make essential interactions ambiguous.
