# System — Selection

## Status

Decided: selection as a first-class semantic system, the model taxonomy (single/multi/range/select-all/toggle), the distinction between selection and other interaction states, shared selection across views, selection summary/contextual actions, persistence, spreadsheet workflows, Selection Mode (including mobile), undo integration, and visual-expression constraints (D-068, D-078–D-088). Open: exact selected-row/cell treatment, selection-mode transition detail, selection action bar anatomy, exact keyboard mappings per platform (see Open questions).

## Purpose

Selection represents the user's current selection of one or more semantic items, records or objects.

Selection is a semantic state associated with the underlying data or object model.

Visual components present and manipulate that state; they do not independently own unrelated copies of it.

## Selection models

Official Sonata selection models include (D-068, D-078):

- single selection
- multi-selection
- range selection
- select all
- toggle selection

The applicable model depends on the underlying interaction and data semantics.

## Selection vs related states

Selection must remain distinct from (D-079):

- focus
- hover
- active
- checked
- highlighted

These states may coexist.

```text
selected ≠ focused
selected ≠ hovered
selected ≠ active
selected ≠ checked
selected ≠ highlighted
```

A component must not rely on one state to communicate another.

## Single selection

Single selection represents one currently selected object.

It is appropriate when:

- one object is the current context
- an inspector or detail view is associated with the selected object
- actions operate on one object

## Multi-selection

Multi-selection permits multiple objects to participate in the same operation.

It is appropriate for workflows such as:

- bulk editing
- moving
- deleting
- exporting
- tagging
- organizing
- batch operations

## Range selection

Range selection allows users to select a contiguous range of items.

Where appropriate on Desktop, standard platform conventions such as Shift-based range selection should be supported.

## Multi-selection modifiers

Where applicable on Desktop, standard platform conventions such as modifier-click selection should be supported.

The exact modifier follows platform conventions.

## Select all

Where the context represents a collection, Select All should be available when semantically appropriate.

Applications should expose clear feedback about what collection is affected.

## Selection state and data

Selection is associated with the underlying data/object model (D-080).

Multiple views may observe and manipulate the same selection.

Example:

```text
Selection
    ↓
┌─────────┬──────────┬────────────┐
│ Table   │ List     │ Inspector  │
└─────────┴──────────┴────────────┘
```

The same selected object remains selected when represented through another compatible view.

## Selection and navigation

Selection must not automatically imply navigation.

An item may be:

- selected
- focused
- inspected
- opened

as distinct operations.

Applications may choose to associate selection with detail presentation when the workflow benefits from it.

## Selection summary

For meaningful multi-selection, the interface should expose a clear selection summary (D-081).

Examples:

```text
1 item selected
12 items selected
All 48 visible items selected
```

The summary should communicate the scope of the selection when that scope is not obvious.

## Selection actions

Actions operating on the selection should become contextually available or more prominent when appropriate (D-082).

Example:

```text
12 items selected

[Move] [Export] [Archive] [Delete]
```

The selection context should make the scope of the action clear.

## Destructive selection actions

Destructive actions applied to a selection must communicate (D-039):

- what will be affected
- approximate scope when useful
- consequence
- recovery availability

Applications should provide undo where practical.

## Selection and undo

Operations performed on selections should integrate with the application's undo system when reversible (D-087).

Users should be able to undo the resulting operation rather than manually reconstructing the previous state.

Global undo/redo mechanisms may be used where supported by the application.

## Selection persistence

Selection may persist across (D-083):

- views
- filtering
- sorting
- pagination
- virtualized collections
- inspector transitions

when the underlying data model and task semantics permit.

Applications must make selection scope clear.

For example, selecting all visible results is not necessarily equivalent to selecting every item in the underlying collection.

## Selection across pages and filters

Applications may preserve selection while:

- changing page
- changing sort order
- changing filters

when doing so supports the workflow.

The UI should clearly communicate when the current selection extends beyond the currently visible subset.

## Selection in tables and spreadsheets

Table and spreadsheet-style interfaces are first-class Sonata use cases (D-084).

Selection should support efficient workflows including:

- row selection
- cell selection where appropriate
- multi-row operations
- range selection
- select all
- keyboard navigation
- keyboard modification
- bulk actions

The visual treatment should remain consistent with Sonata while accommodating high-efficiency workflows.

## Row selection

Row selection is an official Sonata capability.

Rows may expose selection through:

- direct row interaction
- checkbox selection
- modifier-based selection
- keyboard selection

The appropriate mechanism depends on the task.

## Cell selection

Cell selection is permitted where the application behaves like a spreadsheet or other grid-oriented editor.

Cell selection must remain distinguishable from:

- cell focus
- cell editing

## Selection mode

Selection Mode is an official Sonata pattern when the platform or application benefits from temporarily changing the interaction context (D-085).

Example:

```text
Normal
   ↓
Select
   ↓
Selection Mode
   ↓
Bulk actions
```

The application may temporarily emphasize selection-related actions.

## Mobile selection mode

On touch-first interfaces, selection mode may be entered using platform-appropriate gestures such as long press (D-086).

The interface may temporarily transform into a selection-focused mode.

Typical changes may include:

- contextual action bar
- selection counter
- explicit selected states
- exit/cancel affordance

The semantic selection model remains the same.

## Selection visualization

Selection should be:

- unmistakable
- visually coherent
- accessible
- spatially efficient

Selection must remain distinguishable from hover and focus.

Dense interfaces should avoid excessive decoration.

Accent color may be used to communicate selection, but selection must not rely exclusively on color (D-088).

## Desktop

Desktop selection should support:

- pointer selection
- keyboard selection
- modifier-based selection
- range selection
- bulk interaction
- keyboard shortcuts
- efficient spreadsheet-like operation

Standard platform conventions should be respected.

See [Desktop Class](../adaptive/desktop.md).

## Mobile

Mobile selection should support touch-efficient interactions while preserving the same semantic model.

The presentation may temporarily change during selection mode.

See [Mobile Class](../adaptive/mobile.md).

## Accessibility

Selection must expose appropriate semantics to:

- keyboard users
- screen readers
- assistive technology
- high-contrast modes

Selected state must not be communicated solely through color.

## Customization

Selection consumes Sonata semantic tokens.

Applications may customize the visual expression through:

- accent
- contrast
- density
- shape
- emphasis

but should not independently restyle each selectable item.

## Motion

Selection may use Motion to communicate:

- entering selection mode
- selecting an item
- changing selection
- applying an action to the selection

Motion should remain subordinate to comprehension.

## Selection and workspaces

Selection may be part of workspace state when the application workflow benefits from preserving it (D-060, D-077).

The application must decide whether selection persistence is appropriate.

## Complexity boundary

Selection should remain simple at the component API level while allowing rich underlying behavior (D-033).

Do not create numerous selection components for every combination of:

- single/multi
- row/cell
- keyboard/touch
- filtered/unfiltered

These are capabilities and contexts of a shared selection model.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Selection) for what remains open: exact selected-row/cell treatment, selection summary placement, selection-mode transition, selection action bar anatomy, cross-page selection model, select-all scope communication, and exact keyboard mappings per platform.
