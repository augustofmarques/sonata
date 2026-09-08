# System — Overlays

## Status

Decided: Overlays as a first-class system (Popover, Tooltip, Contextual Surface, Dialog, Modal, Sheet, Drawer, Floating Panel, Full-screen Overlay), Tooltip/contextual-assistance restraint, Dialog restraint, modal scope, Inspector presentation independence, user-controlled floating surfaces, overlay-to-persistent promotion, no arbitrary overlay nesting, focus restoration, platform-consistent dismissal, mobile adaptation, expression permissions and context preservation (D-141–D-155). Open: exact Popover sizing, Tooltip timing/placement, Dialog size classes, Sheet-vs-Drawer terminology, Floating Panel docking model, stacking/z-order implementation (see Open questions).

## Purpose

Overlays present contextual, temporary or focused content above the current Content Space without necessarily changing the underlying semantic context.

## Core distinction

```text
Overlay
    ↓
temporarily presented above the current context

Navigation
    ↓
moves to a different destination/context

Region / Panel
    ↓
becomes part of the persistent composition
```

An overlay should not be used merely because another component exists.

## Overlay types

Official Sonata overlay mechanisms include (D-141):

- Popover
- Tooltip
- Contextual Surface
- Dialog
- Modal
- Sheet
- Drawer
- Floating Panel
- Full-screen Overlay

## Popover

Popover presents contextual interactive content associated with an origin.

Appropriate for:

- short actions
- compact controls
- contextual options
- focused temporary interaction

Popover content should remain reasonably bounded.

A Popover should not become a disguised application window.

## Tooltip

Tooltip provides supplementary information that is useful when an element's meaning or function can be clarified without changing the current workflow.

Tooltip content must not contain information required to complete an essential task (D-142). This narrows the general hover-disclosure rule ([`disclosure.md`](disclosure.md), D-137) to the Tooltip component specifically.

Tooltip is one mechanism within Sonata's broader contextual-assistance model.

## Contextual assistance

Sonata may communicate additional information through (D-143):

- visible labels
- supporting text
- inline explanations
- previews
- hover/focus hints
- tooltips
- contextual status
- accessible descriptions

The application should choose the least intrusive mechanism that still provides the needed explanation. This complements, rather than restates, the self-explanatory-interface decision in [`actions.md`](actions.md) (D-038), which is about preferring in-interface cues over external documentation.

Important information must not depend exclusively on hover or tooltip availability.

## Dialog

Dialog is a focused temporary interaction surface.

Use Dialog when:

- the user must make a focused decision
- a short focused task requires temporary isolation
- confirmation is necessary
- a concise form or action requires temporary concentration

Dialogs may contain:

- information
- confirmation
- forms
- multiple related choices
- short multi-step flows

However, complex workflows should not be compressed into large or deeply branched dialogs merely to avoid changing context (D-144).

## Dialog complexity

Avoid dialogs that require excessive:

- navigation
- configuration
- scrolling
- nested choices
- unrelated controls
- multi-stage workflows

When a task becomes substantial, prefer:

- Content Space composition
- Inspector
- Panel
- Sheet
- dedicated view
- Workspace context

rather than accumulating complexity inside one dialog.

## Modal vs non-modal

Modal state is a behavioral property, not a visual style.

### Modal

The underlying context is temporarily constrained.

Use when the current task requires concentrated attention or the user must resolve a condition before continuing.

### Non-modal

The underlying context remains available.

Use when the user benefits from simultaneous access to the originating context.

The degree of blocking should match the task.

## Modal scope

A modal overlay should block only the context that actually requires blocking (D-145).

It should not automatically block the entire application when only a local context needs attention.

## Sheet

Sheet is an official Sonata overlay/composition mechanism (D-146).

A sheet may appear:

- from a side
- from the bottom
- from another contextually appropriate direction

according to platform, available space and workflow.

Sheets are useful for:

- contextual editing
- secondary tasks
- compact workflows
- mobile adaptation
- temporary extended controls

## Drawer

Drawer is an official Sonata pattern for contextual or tool-oriented content that occupies part of the available space (D-146).

A drawer may remain open while the user continues working in the underlying context where appropriate.

## Floating Panel

Floating Panel is an official Sonata component/pattern for tool or contextual surfaces that need temporary spatial independence.

It may be movable, resizable, pinnable, collapsible and dismissible when the application supports these capabilities (D-148) — resizing and collapsing follow the same rules as any other Panel ([`composition.md`](composition.md), D-113, D-114); movable, pinnable and dismissible are specific to overlay-class floating surfaces.

## Inspector as overlay

An Inspector retains its semantic role even when presented as (D-147):

- floating panel
- overlay
- sheet
- modal
- docked panel

The presentation may change without changing the underlying semantic concept. See [`data-display.md`](data-display.md) (D-070, D-071).

## Overlay and Content Space

Overlay must preserve clear relationship with its originating Content Space.

When the user closes an overlay, the originating context should remain intact unless the operation intentionally changes it (D-155).

## Overlay anchoring

Where possible, contextual overlays should retain a clear spatial relationship with their origin.

Examples:

```text
Control
  ↓
Popover

Selection
  ↓
Inspector

Action
  ↓
Contextual confirmation
```

The relationship may be represented spatially or semantically depending on platform.

## Focus

When an overlay opens, focus should move appropriately to the overlay when required.

When the overlay closes, focus should return to the originating control or logical context where applicable (D-151).

## Escape

Dismissible overlays should support standard platform dismissal conventions (D-152).

On Desktop, Escape should dismiss a dismissible overlay when consistent with the platform and task.

Applications should not override Escape for arbitrary purposes when it would violate predictable dismissal behavior.

## Overlay persistence

An overlay may become persistent when the user repeatedly needs it (D-149).

Applications may provide an easy transition from:

```text
temporary overlay
    ↓
persistent floating/docked region
```

without requiring the user to reconstruct the previous configuration.

## Promotion to persistent workspace UI

When an overlay becomes a repeated or sustained part of a workflow, the application may offer to preserve it as part of the workspace.

The transition may be subtle and optional.

Example:

```text
"This panel appears often."
[Keep open] [Later]
```

The user must not be forced to make the decision immediately.

## No nested overlays

Sonata does not permit arbitrary overlay nesting (D-150).

An overlay should not normally open another overlay on top of itself.

Avoid:

```text
Dialog
  → Popover
      → Dialog
```

or equivalent chains.

When additional complexity appears, move the workflow into a more appropriate composition.

## Mobile

Mobile may use larger overlay presentations when needed (D-153).

However, an overlay should not automatically become full-screen merely because the viewport is small.

Use the presentation that best preserves:

- context
- task focus
- touch usability
- comprehension

Full-screen treatment is appropriate when the task genuinely requires most of the available space. See [Mobile Class](../adaptive/mobile.md).

## Desktop

Desktop may use:

- floating panels
- docked drawers
- persistent inspectors
- non-modal contextual surfaces

when simultaneous access to the originating content improves the workflow. See [Desktop Class](../adaptive/desktop.md).

## Translucency

Overlay surfaces may use Sonata translucency and blur (D-154, D-011).

This treatment should be encouraged when it improves spatial separation and preserves the relationship between overlay and underlying content.

It must not compromise readability or task clarity.

## Shape

Overlay geometry follows the Sonata shape system (D-154, D-010).

Different overlay classes may use different semantic shape roles.

## Motion

Overlay transitions should use Sonata Motion to communicate (D-154, D-026):

- origin
- destination
- layering
- appearance
- dismissal
- continuity

Morphing may be used where it improves continuity (D-029).

## Accessibility

Overlays must expose:

- semantic role
- focus behavior
- dismissal behavior
- labeling
- relationship to originating content

Modal overlays must trap or constrain focus appropriately.

Non-modal overlays must remain accessible without requiring pointer interaction.

## Writing

Overlay text follows Sonata's Foundation writing principles.

Labels and actions should be specific and understandable.

Avoid large paragraphs when concise contextual information would suffice.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Overlays) for what remains open: exact Popover sizing rules, Tooltip timing/placement, Dialog size classes, Sheet-vs-Drawer terminology, the Floating Panel docking model, overlay-promotion interaction, full-screen-overlay thresholds, overlay stacking/z-order implementation, accessibility announcement behavior, and platform-specific dismissal mappings.
