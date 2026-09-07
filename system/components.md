# System — Components & States

## Status

Decided: catalog architecture and graduation ladder. Open: final component inventory, exact APIs (see Open questions).

Components are semantic building blocks composed from primitives and Sonata tokens.

## Component catalog

Sonata defines a normative base catalog that applications may extend with product-specific components (D-031). Official Sonata components are opinionated — each should provide a preferred solution for a common interaction problem, not merely an unstyled shell (D-032).

```text
COMPONENTS
│
├── Primitives
│
├── Core Components
│
├── Compound Components
│
├── Patterns
│
└── Application Components
```

### Graduation ladder

Complexity is a valid reason to introduce a new abstraction rather than forcing every interaction to fit an existing component (Principle 16). A component must not be artificially simplified when doing so would create inconsistency, obscure semantics or fail to represent a genuinely more complex interaction (D-033).

```text
Primitive
   ↓
Core Component
   ↓
Compound Component
   ↓
Pattern
   ↓
Application-specific Component
```

Each step down represents greater contextual complexity:

- **Primitive** — low-level interaction behavior and accessibility infrastructure. See [`primitives.md`](primitives.md).
- **Core Component** — an official, opinionated Sonata component solving a common interaction problem.
- **Compound Component** — multiple coordinated primitives/core components composed into one semantic unit.
- **Pattern** — a recurring, complex workflow assembled from components. See [`../patterns/overview.md`](../patterns/overview.md); optional unless justified by application complexity.
- **Application Component** — a product-specific component that extends the base catalog rather than replacing it.

Search, command palettes and power-user workflows are Patterns for this reason — they are not forced into a single flat component just to avoid growing the catalog.

## Cross-platform implementation

Sonata components preserve semantic identity and design-language intent across platforms without requiring pixel-identical rendering (D-034).

## Component APIs

Component APIs should prefer orthogonal semantic properties and token-driven composition over combinatorial variant proliferation (D-035). Components consume Sonata semantic tokens and do not expose arbitrary independent visual styling as their normal customization mechanism (D-036).

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

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Components) for what remains open: final component inventory, detailed component APIs, the concrete compound-component list, and cross-platform implementation strategy.
