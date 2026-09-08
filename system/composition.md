# System — Composition

## Status

Decided: Content Space and Region/Pane/Panel as official concepts, composition modes, context preservation, region expansion, user-resizable/customizable composition, fragmentation restraint, composition-vs-navigation distinction, and adaptive composition across Desktop/Mobile (D-108–D-117). Simultaneous-presentation and space-as-a-resource are the general Foundation principle this domain applies (D-056, Principle 18, [`../foundation/layout.md`](../foundation/layout.md)) rather than a separately restated rule. Open: exact pane dimensions, resize/collapse mechanics, floating-region anchoring, modal-vs-non-modal thresholds, mobile transformation rules, workspace layout serialization (see Open questions).

## Purpose

Composition defines how multiple interface regions are arranged within an application or content context.

Sonata supports complex compositions without requiring those regions to become separate conceptual pages or fragmented experiences.

## Content Space

Content Space is the primary semantic working context of a screen or application state (D-108).

A Content Space may contain multiple coordinated regions while remaining one coherent user context.

Example:

```text
Content Space
├── Main Region
├── Inspector Region
└── Contextual Region
```

The presence of multiple regions does not imply multiple navigation destinations.

## Region

A Region is a functional subdivision of a Content Space (D-109).

A Region should have a meaningful relationship to the other regions around it.

Examples:

- primary content
- supporting content
- contextual information
- inspector
- tool area
- preview

## Pane

A Pane is a Region with a relatively persistent spatial allocation (D-109).

Panes are particularly useful in:

- split views
- master-detail
- multi-column workflows
- data/inspector layouts

## Panel

A Panel is a functional surface that may be (D-109):

- persistent
- contextual
- collapsible
- floating
- transient

A Panel may occupy part of a Content Space or temporarily appear above it.

## Composition principle

Sonata prefers simultaneous presentation when it materially improves (D-056, Principle 18):

- comparison
- comprehension
- editing
- navigation
- contextual awareness
- task efficiency

Sequential navigation is appropriate when simultaneous presentation would create excessive cognitive or spatial complexity.

## Preserve context

When two regions represent related aspects of the same context, changing one region should preserve the others when practical (D-110).

Example:

```text
Table + Inspector
        ↓
selection changes
        ↓
Table remains
Inspector updates
```

A contextual change should not unnecessarily replace the primary context with another page.

## Composition modes

Official composition mechanisms include (D-111):

- horizontal split
- vertical split
- stacked regions
- overlay
- floating region
- modal region
- split view
- master-detail
- multi-column composition

Applications may combine these mechanisms. Split View and Master-Detail are the data-specific instances of these general mechanisms — see [`data-display.md`](data-display.md) (D-071, D-072).

## Spatial relationships

Composition should communicate relationships through:

- proximity
- alignment
- shared surfaces
- visual hierarchy
- separators
- whitespace
- containment
- motion

Regions should not appear unrelated when they participate in the same workflow.

## Horizontal composition

Horizontal composition is encouraged when simultaneous side-by-side information materially improves a workflow.

Examples:

```text
Navigation | Main | Inspector
List       | Detail
Table      | Context
Form       | Preview
```

Desktop and large adaptive contexts may use substantial horizontal space.

## Vertical composition

Vertical composition is appropriate when content has a natural reading or sequential relationship.

It should not be used merely because a one-column layout is easy to implement.

## Expansion

A Region may temporarily expand to occupy most or all of the Content Space (D-112).

Examples:

```text
Table | Inspector
       ↓
Table maximized
       ↓
Table | Inspector
```

or:

```text
Preview panel
       ↓
Preview maximized
       ↓
Preview panel
```

Expansion should preserve a clear way to return to the previous composition.

## Resizing

Where appropriate, users may resize (D-113):

- panes
- panels
- columns
- inspectors
- split regions

Resizing should respect:

- minimum usable dimensions
- readability
- accessibility
- content constraints

User-defined dimensions may be persisted in Workspace state when appropriate (D-060, D-077).

## Collapse

Regions may be collapsible when (D-114):

- the information is secondary
- temporary additional space is useful
- the user benefits from reducing visual presence

Collapsed regions should remain discoverable.

## Floating regions

Floating regions may temporarily detach from the main composition.

They are appropriate when:

- the user needs additional space
- the content is contextual
- the region is used intermittently
- persistent occupation of layout space is undesirable

Floating regions must retain clear relationship to their originating context.

## Modal regions

Modal presentation is appropriate when interaction with the underlying context should be temporarily constrained.

Modal presentation should not be used merely because a secondary region exists.

Use non-modal composition when simultaneous interaction materially benefits the workflow.

## Fragmentation

Sonata explicitly discourages unnecessary fragmentation of the Content Space (D-115).

Multiple regions are justified when they represent meaningful relationships or simultaneous work.

Do not divide the Content Space merely to accommodate individual components.

Bad composition:

```text
Region | Card | Card
       | Widget
       | Widget
```

when the elements have no meaningful spatial relationship.

Good composition:

```text
Table | Inspector
```

when the inspector directly describes the selected table item.

## Composition vs navigation

Changing or updating a Region does not inherently constitute navigation (D-116).

A user may remain within the same Content Space while:

- changing selection
- changing inspector content
- opening a contextual panel
- changing a preview
- expanding a region

This reduces unnecessary navigation and preserves context.

Expanding or collapsing content locally is Disclosure, not Composition or navigation — see [`disclosure.md`](disclosure.md) (D-130).

## Composition vs workspace

Composition defines the current arrangement.

Workspace may persist or restore that arrangement (D-060, D-077).

Example:

```text
Workspace
    ↓
Content Space
    ↓
Navigation | Data | Inspector
```

Users may save different compositions for different workflows.

## Composition and data

Data-heavy workflows may benefit from:

- table + inspector
- list + detail
- master + detail
- navigation + data + context
- form + preview

The appropriate composition depends on the relationship between the information. See [`data-display.md`](data-display.md).

## Composition and forms

Complex forms may use (D-051):

- multi-column layouts
- sections
- side-by-side contextual information
- preview
- persistent summary
- supporting reference information

A form should not automatically become a single vertical sequence simply because the implementation is simpler.

## Composition and real estate

Available screen space is a resource (D-056, Principle 18).

Sonata should allocate space according to workflow needs.

Do not:

- waste large desktop areas with unnecessary empty margins
- force complex workflows into narrow columns
- fill every available region without functional justification

## Adaptive composition

Composition may transform across interaction classes (D-117).

Examples:

```text
Desktop:
Navigation | Main | Inspector

Mobile:
Navigation
   ↓
Main
   ↓
Inspector / Detail
```

or:

```text
Desktop:
Form | Preview

Mobile:
Form
   ↓
Preview
```

The semantic relationship remains.

The spatial manifestation changes.

## Mobile composition

Mobile should favor:

- focused contexts
- progressive disclosure
- sequential presentation where necessary
- touch-appropriate regions

Mobile may add an interaction step when that avoids overwhelming the user. See [Mobile Class](../adaptive/mobile.md).

## Desktop composition

Desktop may favor:

- simultaneous contexts
- persistent panes
- inspectors
- multi-column forms
- wide tables
- tool areas
- contextual panels

The goal is not to maximize occupied space.

The goal is to maximize useful simultaneous context. See [Desktop Class](../adaptive/desktop.md).

## Accessibility

Composition must preserve:

- logical reading order
- logical focus order
- keyboard navigation
- sufficient target sizes
- usable text scaling
- high-contrast visibility
- reduced-motion alternatives

Spatial arrangement must not make the underlying semantics inaccessible.

## Platform adaptation

Composition semantics are platform-independent.

Platforms may implement:

- native split views
- docked panes
- sidebars
- sheets
- floating windows
- dialogs
- panels

according to their own conventions, provided Sonata's semantic relationships remain intact.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Composition) for what remains open: exact pane minimum/maximum dimensions, resize-handle behavior, collapse/expand controls, region-reordering mechanics, expansion/restoration behavior, floating-region anchoring, modal-vs-non-modal thresholds, mobile transformation rules, and workspace serialization of layout.
