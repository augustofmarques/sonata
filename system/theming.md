# System — Theming

Sonata themes are token configurations, not replacements for the component architecture.

This file describes **Axis B (Precedence)** of the Sonata token resolution model — which source wins when more than one wants to set the same token's value. For how this combines with token abstraction (Axis A) and interaction state (Axis C), see [`resolution-model.md`](resolution-model.md).

Theme sources conceptually inherit through:

```text
Sonata defaults
    ↓
Application theme
    ↓
User preferences
    ↓
Accessibility constraints
```

Domain-specific generation algorithms (e.g. color's source-color → tonal → palette pipeline, see [`../expression/color.md`](../expression/color.md)) run inside the "Sonata defaults" and "Application theme" steps — they produce the value a step contributes, they are not an additional precedence level.

Accessibility constraints are the last step, which is the structural basis for their final authority (Principle 7, D-018): later always overrides earlier.

Interaction state (hover, pressed, disabled, …) is **not** a precedence level — it is a separate axis (Axis C) applied after this cascade resolves a value. See [`components.md`](components.md).

User customization changes token values and profiles while preserving semantic structure.
