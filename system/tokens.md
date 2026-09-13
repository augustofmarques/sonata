# System — Tokens

## Status

Decided: the four-layer abstraction hierarchy (Primitive/Semantic/Component/Rendered UI), semantic tokens as the stable design API, State tokens as independently themeable Component-token variants rather than a fifth layer (D-197), application token extensibility, and the Stable/Controlled/Internal API tiers (D-193–D-195, D-197, D-204). Open: exact primitive/semantic/component token naming conventions (see Open questions).

## Purpose

Tokens provide Sonata's shared vocabulary for visual and compositional variables. They form the contract between semantic design decisions and implementation, allowing the same semantic system to support product identity, adaptive interfaces, accessibility, user customization, component consistency and multiple platform implementations.

This file describes **Axis A (Abstraction)** of the Sonata token resolution model — which layer of specificity a token lives at. It does not say which source wins when several want to set a token's value (Axis B, see [`theming.md`](theming.md)) or which interaction-state variant renders (Axis C, see [`components.md`](components.md)). For the combined model, see [`resolution-model.md`](resolution-model.md).

## Token layers

```text
Primitive
  ↓
Semantic
  ↓
Component
  ↓
Rendered UI
```

Components should consume semantic tokens rather than raw primitive values wherever practical.

## Primitive tokens

Primitive tokens represent low-level values (formerly described as "raw values" and "foundation/system tokens" — the same Axis A step, one name).

Examples:

```text
color.*
space.*
radius.*
type.*
motion.*
elevation.*
```

Primitive token names are implementation-level details and may evolve. Applications should avoid coupling directly to primitive tokens when a semantic token exists.

## Semantic tokens

Semantic tokens express meaning.

Examples:

```text
color.accent
color.surface
color.text
space.control
shape.control
type.body
motion.interaction
elevation.floating
```

Semantic tokens are the primary stable Sonata design API (D-193).

## Component tokens

Component tokens connect semantic roles to component-specific implementation.

Examples:

```text
button.background
button.foreground
button.shape
button.padding

dialog.surface
dialog.shape
dialog.elevation
```

Component tokens may be exposed to implementers (D-204). They are not automatically user-facing preferences.

## State tokens

State tokens express interaction or operational states.

Examples:

```text
button.hover
button.focus
button.pressed
button.disabled

selection.active
selection.selected

feedback.error
feedback.success
```

State tokens are not a fifth Abstraction layer: they are the concrete, independently themeable Component-token names that **Axis C (State)** selects among once Axis A + B have resolved a base value (D-197) — this resolves the open question in [`resolution-model.md`](resolution-model.md) about whether state variants are independently themeable or fixed transforms. See [`components.md`](components.md) for the state list itself and [`state.md`](state.md) for the semantic state model these tokens present.

## Token independence

Token values should remain independent from semantic meaning.

A component must not assume that:

```text
accent = blue
danger = red
```

Those relationships may be generated or mapped by the active theme.

## Token extensibility

Applications may define additional semantic tokens when their domain requires them (D-195).

Examples:

```text
app.diagram.selection
app.audio.playhead
app.cad.snap-guide
app.editor.syntax-keyword
```

Application-specific tokens should remain namespaced and should not modify the meaning of core Sonata tokens.

## Token customization

User customization should operate primarily through semantic theme controls and preferences rather than arbitrary component-level overrides.

Examples:

```text
user.accent
user.neutral
user.typography.scale
user.interface.scale
user.spacing
user.density
user.shape
user.motion
user.surface
```

These values modify the visual expression of the interface while preserving its semantic and spatial architecture (D-194).

## Component-token access

Implementers may consume or override component tokens where application requirements justify it (D-204).

However, product/application code should prefer semantic tokens when defining new components.

## Stable vs implementation API

### Stable

Semantic tokens and documented user-facing preferences.

### Controlled

Component tokens and implementation-facing mappings.

### Internal

Primitive values and generated intermediate values.

The distinction is about stability and intended usage, not access restrictions.

## Principle

> User customization should change expression without breaking structure. (Principle 62)
