# System — Containers

## Status

Decided: Containers as a first-class system, the Container/Group/Section/Card/Panel/Stack/Cluster/Grid/Inset-Well/Separator taxonomy, surface-independence, full-bleed, sticky regions, indentation (including its semantic-plus-visual requirement), tablet/intermediate composition, and rounded floating surfaces as legitimate geometry (D-156–D-171, D-174). Token consumption follows the general D-036 rather than a container-specific restatement; material/translucent surface support follows D-011 and D-154 rather than a third restatement; supporting simple-to-complex software without forced fragmentation follows the general complexity stance in D-057. Open: exact Container/Grid/Stack APIs, minimum indentation unit, tree/list indentation behavior, full-bleed containment rules, sticky-region constraints, tablet-specific composition heuristics (see Open questions).

## Purpose

Containers provide semantic and compositional structure for grouping, arranging and presenting related content.

A Container is not inherently a visual surface.

Containers may be:

- visually prominent
- subtly separated
- visually neutral
- transparent
- nested
- spatially adaptive

## Core distinction

A Container establishes structure.

A Surface establishes visual material.

A Container may therefore exist without:

- background
- border
- shadow
- radius

Conversely, a Surface may exist as part of a Container without determining its semantic grouping.

## Core container concepts

Official Sonata container concepts include (D-156):

- Container
- Group
- Section
- Card
- Panel
- Stack
- Cluster
- Grid
- List Section
- Inset / Well
- Separator / Divider

## Container

Container provides generic spatial and semantic grouping.

It should not imply a particular visual treatment.

## Group

Group represents elements that belong together semantically (D-160).

Grouping should make relationships explicit and reduce redundancy or duplication.

Use Group when the elements:

- share a conceptual purpose
- represent related controls
- form one logical unit
- should be perceived together

## Section

Section represents a meaningful division within a larger context (D-159).

A Section may be used in:

- websites
- application pages
- panels
- forms
- settings
- inspectors
- dashboards
- documents

Section does not imply a particular surface treatment.

A Section may contain:

- heading
- supporting description
- controls
- content
- actions
- nested groups

## Card

Card is an official Sonata component for self-contained content or interaction.

Cards may be:

- informational
- interactive
- selectable
- expandable

Card is not the universal grouping mechanism (D-157).

Use semantic Groups and Sections when a card-like surface would add unnecessary visual fragmentation.

## Panel

Panel represents a functional region or supporting area. Panel and Card serve different purposes: Panel is a functional/spatial region, Card is a self-contained content or interaction grouping (D-158).

Panels may contain:

- tools
- inspectors
- properties
- contextual information
- navigation
- supporting content

Panels belong strongly to the Composition and Application Shell systems. See [`composition.md`](composition.md) (D-109) and [`application-shell.md`](application-shell.md).

## Stack

Stack provides simple one-dimensional composition (D-161).

It may arrange elements:

- vertically
- horizontally

Stack should be used for straightforward repeated spatial relationships. This is a layout primitive for elements within a container — distinct from Composition's region-level horizontal/vertical/stacked composition modes ([`composition.md`](composition.md), D-111).

It must not become a substitute for meaningful semantic grouping.

## Cluster

Cluster groups related elements that may wrap or rearrange.

Cluster is useful for:

- controls
- tags
- metadata
- actions
- compact responsive groups

## Grid

Grid provides two-dimensional composition (D-161).

It is an official Sonata composition mechanism.

Grid may be used for:

- complex forms
- dashboards
- data layouts
- settings
- comparison interfaces
- responsive desktop compositions

Grid should support semantic alignment rather than arbitrary visual placement.

## Inset / Well

Inset or Well provides a visually differentiated nested region with lower emphasis than a Card or elevated Panel (D-165).

It is useful for:

- secondary information
- contextual notes
- supporting controls
- contained subsections

## Containers without surfaces

Containers may remain visually transparent (D-162).

Example:

```text
Section
├── Heading
├── Group
│   ├── Field
│   └── Field
└── Group
    ├── Field
    └── Field
```

No visible card or panel is required.

## Separators

Separator/Divider is an official container concept, but should not replace meaningful spacing and grouping as the primary way to communicate structure (D-163).

## Card nesting

Cards may be nested when their semantic relationship justifies it (D-164).

Avoid unnecessary nested surfaces.

Do not introduce cards merely because content needs grouping.

## Surface inheritance

Visual containers consume Sonata Surface, Shape, Elevation, Color and Density tokens rather than defining independent visual systems — this is the general component/token decision (D-036) applied to containers, not a separate rule.

## Density

Containers participate in the global density system.

Changing density should maintain alignment between:

- groups
- controls
- labels
- headings
- panels
- cards
- sections

## Alignment

Containers should establish alignment contexts (D-174).

Related content should align consistently even when distributed across multiple containers or regions.

Examples:

```text
Label       Control
Label       Control
Description Control
```

and:

```text
Heading
───────
Content
```

Alignment should be treated as structural information.

## Full-bleed

Containers may permit selected children to extend beyond the container's normal inner padding (D-166).

Full-bleed is useful for:

- images
- tables
- graphs
- media
- code
- edge-to-edge contextual elements

Full-bleed content should remain semantically associated with its originating container.

## Sticky regions

Containers may contain sticky regions where useful (D-167).

Examples:

- section headers
- table headers
- action bars
- filter controls
- form action areas
- navigation elements

Sticky behavior should preserve context without obscuring content.

## Responsive containers

Containers may:

- reflow
- change columns
- collapse
- reveal
- merge
- split

across adaptive classes. See [`../adaptive/adaptive.md`](../adaptive/adaptive.md).

The semantic relationship between contents remains stable.

## Tablet and intermediate layouts

Intermediate environments may combine properties of Desktop and Mobile (D-170).

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

Supporting regions may temporarily move out of the way to provide additional manipulation space.

Users may collapse, hide, dock or float such regions when the application supports it. See [`../adaptive/adaptive.md`](../adaptive/adaptive.md).

## Spatial manipulation

Where appropriate, users may:

- resize
- move
- collapse
- expand
- dock
- undock
- hide
- show
- pin

containers and associated regions. This extends the Composition and Application Shell customization decisions ([`composition.md`](composition.md) D-113–D-114; [`application-shell.md`](application-shell.md) D-127) to Container-level primitives specifically.

These preferences may be persisted in Workspace state.

## Semantic nesting

Nested containers should communicate actual semantic nesting.

Avoid using indentation or nested surfaces merely to make an interface appear more structured.

## Indentation

Indentation is an official Sonata structural pattern (D-168).

When content is hierarchically nested, visual indentation may communicate that relationship.

Examples:

```text
Parent
    Child
    Child
        Subchild
```

or:

```text
▸ Group
    Item
    Item
```

Indentation should align with the visual origin of the containing hierarchy.

Sibling items should share a consistent indentation origin.

Nested items should visibly advance relative to their parent.

## Indentation rules

Indentation should communicate:

- hierarchy
- containment
- dependency
- subordination

It should not be used merely as arbitrary spacing.

Indentation may be implemented through:

- padding
- grid tracks
- alignment guides
- nested layout regions
- platform-native tree/list indentation

The implementation must preserve the same perceived hierarchy.

## Indentation and accessibility

Indentation cannot be the only semantic indicator of hierarchy (D-169).

Hierarchical relationships must also exist in:

- document structure
- accessible semantics
- labels
- tree/list semantics where applicable

## Mobile indentation

Mobile may reduce indentation magnitude when screen width is constrained, but must preserve discernible hierarchy.

If the hierarchy would become ambiguous, the implementation should adapt through:

- disclosure
- labels
- grouping
- alternate presentation

See [Mobile Class](../adaptive/mobile.md).

## Desktop indentation

Desktop may use more generous indentation where screen space permits.

Tree and hierarchy-heavy interfaces may use substantial indentation when it meaningfully improves scanning. See [Desktop Class](../adaptive/desktop.md).

## Expression

Containers may use Sonata Expression mechanisms to reinforce grouping:

- color
- surface
- shape
- elevation
- transparency
- typography

Expression should reinforce structural grouping rather than create false grouping. See [`../expression/shape.md`](../expression/shape.md) (D-171) and [`../expression/surface-depth.md`](../expression/surface-depth.md) (D-011).

## Complexity

Containers should help represent complex software without forcing every logical unit into a separate visual box — the general complexity-accommodation stance (D-057, Principle 19) applied to containers rather than a separate rule.

Professional applications may use many coordinated regions while maintaining a coherent overall structure.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Containers) for what remains open: exact Container/Grid/Stack APIs, minimum indentation unit, tree/list indentation behavior, full-bleed containment rules, sticky-region constraints, container alignment APIs, and tablet-specific composition heuristics.
