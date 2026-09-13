# Adaptive — Desktop Class

Desktop Class prioritizes:

- pointer
- keyboard
- higher information density
- simultaneous contexts
- persistent navigation where useful
- multi-pane layouts
- contextual toolbars
- power-user workflows

Desktop supports all four density profiles — Comfortable, Balanced, Compact and Dense — the only class where Dense is unconditionally available (D-208). See [Spacing & Density](../expression/spacing-density.md).

## Multi-pane examples

Desktop should take advantage of available space when persistent orientation or rapid switching materially improves productivity (D-056); it should not fill space merely for the sake of filling it.

- Navigation | Content
- Navigation | Content | Inspector
- Navigation | Workspace | Contextual panel
- Master | Detail
- Master | Detail | Properties

## Data display

Desktop may use greater information density and simultaneous context — dense tables, persistent inspectors, wide comparison views, advanced filtering — exploiting available space when it materially benefits the workflow. See [Data Display](../system/data-display.md).

## Selection

Desktop selection should support pointer, keyboard and modifier-based selection, Shift-based range selection and other standard platform conventions, keeping spreadsheet-like row/cell selection efficient. See [Selection](../system/selection.md).

## Feedback

Desktop may take advantage of persistent feedback regions and simultaneous status visibility:

- status areas
- background-operation indicators
- notification center
- persistent contextual banners
- non-blocking progress

These surfaces should not monopolize space when the information is not relevant to the current workflow. See [Feedback](../system/feedback.md).

## Composition

Desktop should favor simultaneous contexts, persistent panes, inspectors, multi-column forms, wide tables, tool areas and contextual panels — maximizing useful simultaneous context, not merely occupied space. See [Composition](../system/composition.md).

## Application shell

Desktop-class applications may use a rich shell — persistent navigation, toolbars, multiple tool areas, inspectors, status, multiple windows across multiple monitors — relying on native window chrome rather than duplicating it. See [Application Shell](../system/application-shell.md).

## Disclosure

Desktop should favor simultaneous visibility for repeatedly needed information or tools, reserving disclosure (Accordion, Collapsible, Menu) for advanced options and secondary tool areas rather than as a substitute for using available space well. See [Disclosure](../system/disclosure.md).

## Overlays

Desktop may retain more contextual information simultaneously through floating panels, drawers, inspectors, non-modal overlays and persistent tool regions when this materially improves workflow efficiency, rather than defaulting to modal interruption. See [Overlays](../system/overlays.md).

## Containers

Desktop may use more generous indentation where screen space permits — tree and hierarchy-heavy interfaces may use substantial indentation when it meaningfully improves scanning. See [Containers](../system/containers.md).

## State

Desktop applications with persistent background work (sync, export, long-running jobs) should keep operations non-blocking and expose their state through persistent status rather than forcing the user to wait. See [State](../system/state.md) and [Operations](../system/operations.md).

## Typography

Desktop may use larger display sizes and richer data typography than Mobile while sharing the same semantic type roles and scale. See [Typography](../expression/typography.md).
