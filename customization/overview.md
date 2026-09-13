# Customization — Overview

Customization is a first-class Sonata capability.

> Users may customize the expression of the interface without breaking its structure. (D-194, Principle 62)

The system distinguishes:

```text
Capability
    vs
Exposure
```

Sonata defines capabilities globally; applications decide which capabilities to expose (Principle 9, D-017, D-023). Sonata may support a customization capability without requiring every application to expose it.

## High-priority candidates

- theme / theme mode
- accent
- neutral color
- typography scale
- interface scale
- spacing/density
- motion

## Secondary candidates

- shape
- surface style
- translucency
- contrast
- font family
- line spacing
- workspace composition
- navigation visibility
- tool visibility

## Customization packages

Related values should preferably be changed together rather than independently, so a single user choice produces a coherent result.

Examples:

```text
Density
→ spacing + control dimensions + row heights + related typography

Interface scale
→ typography + controls + icons + spacing

Shape
→ control + container + surface + overlay geometry

Accent
→ accent palette + interactive emphasis + selected states
```

## Structural invariants

Customization must not break (D-194):

- hierarchy
- semantic meaning
- navigation
- accessibility
- minimum usable targets
- required interaction behavior

## Advanced implementation customization

Implementers may access component tokens where necessary (D-204, [`../system/tokens.md`](../system/tokens.md)).

This is distinct from ordinary user-facing customization.

## Per-domain detail

- [Color](color.md)
- [Typography](typography.md)
- [Density](density.md)
- [Shape & Surface](shape-surface.md)
- [Motion](motion.md)
- [Accessibility](accessibility.md)

Each of these files describes the user/product-facing exposure surface for its domain. The corresponding `expression/*.md` file describes the underlying technical mechanism the exposure surface controls — see the [Token Resolution Model](../system/resolution-model.md) for how a user's choice here becomes a rendered value.

## System-component customization

Actions, Inputs, Navigation, Data Display, Selection, Feedback, Composition, Application Shell, Disclosure, Overlays, Containers, State and Operations are System-layer components/systems rather than Expression domains, so they do not get a separate `customization/*.md` counterpart (see [D-025](../governance/decision-log.md#d-025--expressioncustomization-split-of-authorship)) — each documents its own customization surface inline in its `system/*.md` file. For Data Display, that includes columns, column order, column size, visible data, sorting, grouping, filters, visible panels, inspector visibility and workspace-specific data presentation (see [`../system/data-display.md`](../system/data-display.md)). These configurations use Sonata's token and workspace systems rather than arbitrary per-component styling.

## Feedback and notification preferences

Feedback presentation itself is generally not user-customized at the individual-message level.

Applications may expose notification-level preferences such as:

- notification categories
- persistence
- grouping
- sound
- haptic feedback
- delivery preferences

Accessibility preferences such as reduced motion and reduced transparency remain higher-priority constraints. See [`../system/feedback.md`](../system/feedback.md).

## Composition customization

Applications may allow users to show, hide, collapse, reorder, resize and otherwise configure contextual regions (panes, panels, inspectors) when application complexity justifies it, with layout preferences persisted as Workspace state where appropriate. See [`../system/composition.md`](../system/composition.md).

## Application shell customization

Applications may expose customization of navigation visibility/order, toolbar contents, tool-area visibility/position, panel dimensions, docking and overall workspace arrangement when application complexity justifies it. See [`../system/application-shell.md`](../system/application-shell.md) and [`../system/toolbar.md`](../system/toolbar.md).

## Disclosure customization

Applications may allow users to configure default expanded state, visible sections and disclosure behavior when application complexity justifies it, with these preferences eligible for Workspace state. See [`../system/disclosure.md`](../system/disclosure.md).

## Overlay customization

Applications may allow users to move, resize, pin, collapse or dismiss appropriate floating panels, and may offer to promote a repeatedly used temporary overlay into a persistent workspace region. See [`../system/overlays.md`](../system/overlays.md).

## State-dependent customization

User customization changes presentation, not semantic state.

For example:

- Accent changes selected-state expression.
- Density changes spatial presentation.
- Typography changes readability.
- Motion preference changes transition expression.

Customization must not alter the underlying semantic interpretation of states such as:

- selected
- disabled
- error
- locked
- offline
- syncing

See [`../system/state.md`](../system/state.md).
