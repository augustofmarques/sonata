# Sonata Glossary

**Adaptive Class** — intermediate layout/interaction state between Mobile and Desktop classes.

**Accent** — primary expressive color identity of an application/theme.

**Application Component** — a product-specific component that extends the Sonata base catalog rather than replacing it.

**Card** — a self-contained content or interaction container with optional visual surface treatment; not the universal grouping mechanism.

**Component** — reusable semantic UI building block consuming Sonata tokens.

**Component Token** — a token mapping semantic values to the implementation of a specific component.

**Compound Component** — multiple coordinated primitives or Core Components composed into one semantic unit.

**Container** — a semantic or spatial grouping mechanism that does not necessarily have a visible surface.

**Content Space** — the primary coherent working context that may contain multiple coordinated regions.

**Core Component** — an official, opinionated Sonata component providing a preferred solution to a common interaction problem.

**Density** — coordinated amount of information and spatial compression in an interface.

**Empty State** — presentation shown when a view has no content, distinguished by cause (never had data, no results, filtered out, loading, unavailable, error) so the interface can explain why and, where useful, what to do next.

**Expression** — Sonata layer responsible for visual and experiential character.

**Expressive Icon** — an icon whose primary purpose is character, personality or hero-level visual emphasis rather than compact semantic labeling.

**Feedback** — communication of the result, state, progress, consequence or availability of an operation or system condition; presentation is proportional to the event's severity, urgency, persistence and context.

**First Use** — the first meaningful interaction with a feature or application capability; may occur after initial launch, not only at OOBE.

**Foundation** — Sonata layer responsible for structure, behavior, accessibility, writing and content; primarily grounded in GNOME HIG.

**Group** — a semantic grouping of related elements that belong together conceptually.

**Hero** — expressive composition mode used for focal, onboarding, empty-state or major-status experiences.

**Icon Family** — a coherent, internally consistent set of icons sharing geometry, optical weight and rendering strategy; Sonata does not mandate a specific one.

**Icon Weight** — the perceived stroke thickness or fill density of an icon, kept consistent within a family and appropriate to its scale.

**Indentation** — a spatial cue communicating hierarchy, containment or subordination; must have corresponding semantic structure, not just visual offset.

**Material Expression** — a visual treatment inspired by Material 3 Expressive involving color, shape, typography, motion or layered surfaces.

**Mobile Class** — touch-first, focused-context adaptation of Sonata.

**Notification** — communication of an event that may remain relevant beyond the moment it occurred, capable of persisting (optionally in a Notification Center) rather than only appearing transiently; distinct from a Toast and from an interruptive Alert.

**Onboarding** — the broader system of orientation, discovery and education surrounding First Use; OOBE is its initial entry point.

**OOBE** — Out-of-Box Experience; the initial experience used to orient, configure or demonstrate an application.

**Optical Alignment** — visual, rather than strictly geometric, centering and sizing so an element (icon, type, container) reads as balanced against adjacent content; perceived alignment takes precedence over mathematical bounding-box alignment when the two conflict (D-223). Originally defined for icons; generalized to typography and UI generally.

**Pane** — a Region with a relatively persistent spatial allocation.

**Panel** — a functional region within a composition or application shell; may be persistent, contextual, collapsible, floating or transient.

**Pattern** — reusable solution to a recurring application workflow; optional unless applicable.

**Platform Reference** — external platform guidance (e.g. Apple HIG) that may inform implementation or expression without overriding Sonata's normative principles.

**Preference** — a single user, application or system choice affecting presentation or behavior; a Theme is the coordinated result of one or more Preferences.

**Preset** — a predefined Theme.

**Primitive Token** — a low-level design value used internally to construct semantic or component tokens.

**Region** — a functional subdivision of a Content Space.

**Salience** — degree of visual prominence assigned to an element.

**Section** — a meaningful division within a larger context; does not imply a particular surface treatment.

**Selection** — the semantic state of which item(s) of an underlying data/object model are currently selected; distinct from focus, hover, active, checked and highlighted, and shareable across multiple views (e.g. Table, List, Inspector) of the same data.

**Semantic Icon** — an icon whose meaning is functionally load-bearing (identifies an action, status or object), as distinct from a purely decorative icon.

**Semantic State** — a meaningful condition of application, data or interaction state, independent of visual presentation (see [`../system/state.md`](../system/state.md)).

**Semantic Token** — a stable token representing a design meaning rather than a raw visual value.

**Shape Profile** — named geometry personality: Subtle, Soft, Rounded, Expressive or Organic (D-209; "Subtle" was previously named "Geometric").

**Sonata Theme** — coherent collection of token values defining a visual configuration; the result of one or more Preferences, and a Preset is a predefined one.

**State Token** — a token representing the visual treatment of a semantic or interaction state (e.g. `button.hover`); independently themeable, not a fixed transform.

**Surface** — a visual material treatment independent of semantic container identity.

**System** — construction layer grounded in Radix-style primitives, states, tokens and theming.

**Toast** — transient, non-blocking feedback surface for low-severity or reversible-action confirmation (e.g. "Item moved — Undo"); not intended for information requiring prolonged attention.

**Token** — semantic variable representing a reusable design decision.

**User Customization** — user-controlled changes to expression-level values while preserving semantic and accessibility invariants.

**Workspace** — a persistent or temporary working context (project, task, document set, tool configuration or saved arrangement) that may bundle navigation state, open documents, panel arrangement, selected tools and user configuration.
