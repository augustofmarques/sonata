# Expression — Motion & Animation

## Status

Architecture decided; exact timings remain open.

Motion communicates causality, continuity, hierarchy, state and feedback.

Sonata has a distinct motion language characterized by:

- smooth transitions
- organic continuity
- subtle transformations
- spatial coherence
- restrained use of spring-like behavior
- expressive motion when semantic importance justifies it

Material motion is a source of reference and inspiration, not a normative implementation.

## Motion levels

- Instant
- Fast
- Standard
- Emphasized
- Expressive

These levels describe motion intensity and communicative importance.

They do not prescribe a universal duration table yet.

## Motion priority

```text
Functional
  ↓
Supportive
  ↓
Expressive
  ↓
Decorative
```

Functional motion communicates required state or interaction changes.

Supportive motion improves comprehension or orientation.

Expressive motion provides character or reinforces hierarchy.

Decorative motion exists primarily for visual personality.

Reduced-motion modes should remove or simplify lower-priority motion first.

## Motion principles

### Causality

Motion should help explain what caused a state or spatial change.

### Continuity

Related content should appear to remain part of the same spatial context when appropriate.

### Hierarchy

More important transitions may receive stronger or more expressive motion.

### Feedback

Motion may confirm activation, completion, failure, loading, selection or other interaction states.

### Restraint

Motion should not compete with content or become continuous visual noise.

### Organic continuity

Sonata favors smooth, natural-feeling transitions rather than mechanically abrupt or excessively theatrical motion.

Spring-like motion may be used where it reinforces physical continuity or direct manipulation.

## Spatial motion

When an element changes position, size, visibility or containment, motion should preserve the user's understanding of:

- origin
- destination
- relationship
- hierarchy
- cause

Movement should not be arbitrary.

## Morphing

Sonata permits semantic morphing between related states.

Shape and motion may be combined when an element changes role or state.

Examples include:

- action → loading
- loading → success
- collapsed → expanded
- inactive → selected
- compact control → contextual control

Morphing should preserve semantic continuity and should not obscure the state change being communicated.

## Adaptive motion

Desktop and Mobile share the same Sonata motion language.

The system may adapt implementation details such as:

- available animation space
- technical duration constraints
- interaction-specific feedback
- platform-specific capabilities

but these adaptations must preserve the same underlying motion principles and personality.

Sonata should not maintain separate desktop and mobile motion aesthetics.

## Haptics

Haptic feedback is an optional modality of Sonata interaction.

Where the platform supports haptics, Sonata may use them to reinforce semantic events such as:

- activation
- selection
- completion
- warning
- error
- direct manipulation boundaries

Haptics must not be required to understand an interaction.

Applications should provide equivalent visual or auditory feedback where appropriate.

Haptics should remain subtle and semantically meaningful.

## Reduced motion

Reduced-motion preferences must preserve:

- state recognition
- feedback
- hierarchy
- causality
- continuity where possible

Motion may be replaced with:

- opacity changes
- color changes
- static state transitions
- focus changes
- instantaneous spatial changes

Decorative motion should be reduced before functional motion.

## Customization

See [`../customization/motion.md`](../customization/motion.md) for the user/product-facing motion-preference levels (Full/Reduced/Minimal/Off) this architecture supports, and their relationship to the system reduced-motion accessibility constraint.

## Open decisions

The following remain implementation-level decisions:

- duration table
- easing functions
- spring model
- motion tokens
- reflow/reveal animation rules
- haptic vocabulary and platform mappings
- exact morphing constraints
