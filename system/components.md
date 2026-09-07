# System — Components & States

Components are semantic building blocks composed from primitives and Sonata tokens.

## Component hierarchy

1. Primitive
2. Component
3. Compound Component
4. Pattern
5. Template

## States

This is **Axis C (State)** of the Sonata token resolution model — applied after Axis A (abstraction, `tokens.md`) and Axis B (precedence, `theming.md`) resolve a component token's base value. See [`resolution-model.md`](resolution-model.md).

Where semantically applicable:

- default
- hover
- focus
- pressed
- active
- selected
- disabled
- loading
- error
- success
- warning
- read-only
- dragged
- expanded
- collapsed

State meaning belongs to Foundation/System. Visual representation belongs primarily to Expression.
