# System — Theming

## Status

Decided: the Axis B precedence chain, the Theme/Preference/Preset distinction, theme presets as token configurations, and the user-customization boundary (D-194, D-196). Open: custom-theme validation criteria, theme import/export, scope of preferences across apps/devices/accounts (see Open questions).

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

## Theme model

A Theme is a coordinated mapping of semantic tokens (D-196).

Theme composition includes:

```text
Color
Typography
Shape
Surface
Density
Spacing
Motion
Elevation
```

## Preference vs Theme vs Preset

A **Preference** is an individual user or system choice. A **Theme** is the resulting coordinated visual configuration. A **Preset** is a predefined Theme (D-196).

Example:

```text
User preference:
Accent = Green

          ↓

Theme:
accent tones
surface relationships
contrast mappings
component appearance
```

## Theme inheritance

Conceptually, illustrating this file's Axis B chain together with the Axis C step that follows it (see [`resolution-model.md`](resolution-model.md)):

```text
Sonata Default
      ↓
Application Theme
      ↓
User Preferences
      ↓
Accessibility Constraints
      ↓
State (Axis C)
```

## User customization boundary

User customization may modify the visual expression of components without modifying their semantic role, information architecture or fundamental interaction model (D-194).

Applications may expose only the subset of these capabilities that is useful for their context.

## Theme presets

Applications may provide curated presets.

Examples:

```text
Sonata Default
Soft
Compact
Expressive
High Contrast
```

Presets are token configurations rather than independent component libraries.
