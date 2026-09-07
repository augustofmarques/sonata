# System — Data Display

## Status

Decided: data-display component catalog, density/customization/editing/selection models, Inspector/Master-Detail/Split View as official, responsive transformation, expression restraint, active-vs-historical priority, virtualization, workspace integration (D-065–D-077). Open: exact anatomy for each component, filter-builder complexity, pagination controls (see Open questions).

## Purpose

Data Display defines the semantic and compositional systems used to present structured information, collections, records and relationships. Sonata treats data-heavy interfaces as first-class application environments (D-065) and must support them ranging from simple lists and tables to highly complex professional software — see [Complexity accommodation](../foundation/layout.md) (D-057, Principle 19); the system must not assume that a single narrow vertical column is inherently superior.

## Core data-display components

Official Sonata data-display components include:

- List
- Table
- Grid
- Tree
- Data Table
- Master-Detail
- Split View
- Inspector
- Data Summary
- Grouped Collection
- Timeline where appropriate

The catalog remains extensible (D-031).

## Table

Table is a first-class Sonata component. Tables should support, depending on the application's domain:

- sorting
- filtering
- grouping
- selection
- resizing
- reordering
- visibility control
- pinning/freezing where appropriate
- inline editing
- row-level actions
- cell-level actions
- contextual actions

## Density

Tables participate directly in Sonata's global density system (D-066; see D-012, D-020, D-050, D-064), supporting Comfortable, Balanced, Compact and Dense profiles. Changing density should coordinate row height, cell padding, typography, spacing, icon size where appropriate and control dimensions — density must not independently compress individual table elements.

## Column customization

Users may be allowed to resize, reorder, show/hide, pin/freeze, sort, group and filter columns (D-067). Applications should provide rapid mechanisms for common configuration changes, and, where appropriate, configuration should be easily reversible (Principle 22): undo, reset, restore previous arrangement, restore defaults.

## Selection

Official selection models (D-068): single selection, multi-selection, range selection, select all. Selection behavior must remain explicit and accessible.

## Editing

Official editing patterns (D-069): inline editing, row editing, cell editing, inspector/form editing. The editing mechanism should reflect the complexity and risk of the operation — inline editing should not be used where it would obscure important validation or workflow requirements.

## Search and filtering

Data collections may expose contextual search using the shared Sonata text-input infrastructure — text search, filters, autocomplete, suggestions, structured query controls — without becoming a command-palette surface. This follows the same semantic-input-distinction and command-surface-scarcity principles already established for text fields generally (D-042, D-043) and their relationship to navigation (D-062); no separate decision is needed here.

Filtering is a first-class Sonata data pattern. Filters should communicate active state, scope, current criteria and result impact, and how to clear or modify the filter; where practical, users should be able to undo or quickly clear recent filtering operations.

## Grouping

Data may be grouped when grouping improves comparison, scanning, comprehension or workflow organization — not merely for decorative hierarchy.

## Master-Detail

Master-Detail is an official Sonata pattern (D-071):

```text
Master
   ↓
Selection
   ↓
Detail
```

The detail may be presented as an adjacent panel, inspector, modal, sheet, floating surface, expanded region or dedicated view, depending on context and interaction class.

## Inspector

Inspector is an official Sonata component/pattern (D-070) providing contextual information or editing tools associated with the currently selected object. Inspector visibility is contextual — persistent, collapsible, hidden, or invoked on demand — and should be exposed when simultaneous access to contextual information materially improves the workflow. It is not mandatory in every data interface.

## Split View

Split View is an official Sonata pattern (D-072) combining, for example, list + detail, table + inspector, master + detail, navigation + content, or content + contextual information. The number of panes is determined by workflow utility rather than screen size alone.

## Real estate

Available space should be used when simultaneous visibility materially improves comparison, comprehension, navigation, editing, task completion or contextual awareness — this is the general Space-as-a-resource principle (D-056, Principle 18) applied to data: do not artificially collapse useful simultaneous context merely to preserve a narrow central column. Examples:

```text
Navigation | Table | Inspector
Navigation | List  | Detail
Filters    | Data  | Context
Form       | Preview
```

## Responsive transformation

Data representations may transform between interaction classes (D-073; see D-063):

```text
Desktop:
Table

Mobile:
List → Detail
```

or:

```text
Desktop:
Master | Inspector

Mobile:
Master → Detail
```

The semantic information remains available even when the presentation changes. Mobile may require additional navigation steps when those steps avoid overwhelming the user with information — additional interaction is acceptable when it materially improves comprehension and reduces cognitive or visual overload. See [Mobile Class](../adaptive/mobile.md) and [Desktop Class](../adaptive/desktop.md).

## Information prioritization

Sonata should distinguish active, pending, in-progress, upcoming, completed, historical and archived information (D-075, Principle 20). Current and actionable information should generally receive greater spatial and interaction priority than historical information, which should remain available when useful but should not automatically consume the same visual prominence as active work. This principle is contextual rather than universal.

## Long collections

Long collections may use pagination, continuous scrolling, infinite scrolling or virtual scrolling, depending on collection size, task type, navigation needs, ability to retain context, and platform. Sonata does not mandate one mechanism.

## Virtualization

Large collections should support virtualization when appropriate (D-076). Virtualization is an implementation capability; the semantic presentation of the collection must remain consistent regardless of whether virtualization is used.

## Empty and exceptional states

Collections must distinguish at least:

```text
Loading
Empty
No results
Filtered out
Error
Permission restricted
Unavailable
```

Errors and unexpected outcomes must explicitly communicate what happened, what the user can do next, and whether data was changed or lost. The UI should not reduce meaningful failures to a generic empty state.

## Long content

Data display should account for truncation, wrapping, expansion, tooltip/preview, copying, selectable text and overflow, depending on the semantic importance of the content. Critical identifiers should not be truncated in ways that prevent users from identifying or copying them.

## Numeric data

Data presentation should support the Sonata numeric typography architecture ([`../expression/typography.md`](../expression/typography.md), D-009): proportional numerals, tabular numerals, lining figures, locale-aware numerals, or monospace presentation where semantically appropriate. Tables containing aligned numeric values should generally prefer tabular figures where supported.

## Accessibility

Data displays must meet Sonata's general accessibility invariants ([`../foundation/accessibility.md`](../foundation/accessibility.md), Principle 7, D-018) as applicable: keyboard navigation, focus, selection semantics, screen readers, contrast, text scaling, reduced motion, and appropriate reflow or alternative presentation. Keyboard users should be able to navigate, inspect and operate data without pointer interaction.

## Expression

Dense data interfaces generally use restrained visual expression (D-074). Expression remains important for selected state, active state, errors, warnings, primary actions, important status, contextual controls, and hero or summary regions — color, motion and decorative surfaces should not overwhelm large quantities of data.

## Workspace integration

Table and data-layout configuration may be stored as part of a Sonata Workspace (D-077; see D-060): visible columns, column order, column sizes, filters, sorting, grouping, visible panels, inspector state, layout and selected tools. Users should be able to switch between contextually meaningful workspace configurations when the application supports workspaces.

## Mobile data display

Mobile should not merely compress desktop tables until they become unreadable. Appropriate transformations may include table → list, multi-column record → stacked information, persistent inspector → detail screen, visible secondary fields → progressive disclosure, and simultaneous comparison → sequential inspection. Important information should not be discarded merely to simplify the layout. See [Mobile Class](../adaptive/mobile.md).

## Desktop data display

Desktop may use greater information density and simultaneous context: multi-pane composition, persistent inspectors, contextual tool panels, dense tables, wide comparison views, advanced filtering, and simultaneous form/data layouts, exploiting available space when doing so materially benefits the workflow. See [Desktop Class](../adaptive/desktop.md).

## Platform adaptation

Data-display semantics remain consistent across platforms (D-034); implementation details — scrolling behavior, native table infrastructure, selection mechanics, keyboard conventions, touch interactions, virtualization implementation — may follow platform conventions. Sonata defines the semantic and design intent, not a single implementation technology.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Data Display) for what remains open: exact Table anatomy, column-resize interaction, column customization UI, pinning behavior, grouping presentation, row/cell editing behavior, selection visualization, Inspector anatomy and transition behavior, Split View collapse rules, exact mobile transformations, virtualization integration, pagination controls, filter-builder complexity, and Timeline anatomy.
