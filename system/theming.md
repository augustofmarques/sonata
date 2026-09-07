# System — Theming

Sonata themes are token configurations, not replacements for the component architecture.

Theme sources conceptually inherit through:

```text
Sonata defaults
    ↓
Application theme
    ↓
User preferences
    ↓
Accessibility constraints
    ↓
Component state
```

User customization changes token values and profiles while preserving semantic structure.
