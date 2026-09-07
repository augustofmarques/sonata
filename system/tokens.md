# System — Tokens

Tokens form the contract between semantic design decisions and implementation.

This file describes **Axis A (Abstraction)** of the Sonata token resolution model — which layer of specificity a token lives at. It does not say which source wins when several want to set a token's value (Axis B, see [`theming.md`](theming.md)) or which interaction-state variant renders (Axis C, see [`components.md`](components.md)). For the combined model, see [`resolution-model.md`](resolution-model.md).

## Token hierarchy

```text
Raw values
  ↓
Foundation/system tokens
  ↓
Semantic tokens
  ↓
Component tokens
  ↓
Rendered UI
```

Components should consume semantic tokens rather than raw palette or spacing values wherever practical.

Examples:

- `color.accent`
- `color.surface`
- `shape.control`
- `space.control`
- `type.label`
- `motion.interaction`
- `elevation.overlay`
