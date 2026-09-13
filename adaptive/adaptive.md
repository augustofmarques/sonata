# Adaptive — Adaptive Class

Adaptive Class describes transitions between Mobile and Desktop compositions.

Preferred transformations:

- reflow
- reveal
- collapse
- substitute
- split
- merge

A layout should respond to available space and input environment rather than to product/device branding.

## Tablet and intermediate environments

Tablet and other intermediate environments may combine touch-first interaction with flexible, desktop-like spatial composition rather than simply inheriting either extreme wholesale (D-170, Principle 54).

Example:

```text
┌──────────────────────────────────────────────┐
│                  Content Space                │
│                                              │
│  Floating / docked tool surface              │
│  ┌──────────┐                                │
│  │ Tool     │          Main Content          │
│  │ Panel    │                                │
│  └──────────┘                                │
│                                              │
└──────────────────────────────────────────────┘
```

Supporting regions (tool panels, secondary navigation, contextual panels) may temporarily move out of the way — collapsing, docking, floating or hiding — when the user needs maximum space for manipulating the primary content, then return without forcing the user to reconstruct the previous arrangement. See [Composition](../system/composition.md) and [Containers](../system/containers.md) for the underlying mechanisms.
