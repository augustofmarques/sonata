# System — Tokens

Tokens form the contract between semantic design decisions and implementation.

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
