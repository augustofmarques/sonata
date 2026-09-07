# Sonata Decision Log

## D-001 — Architecture
**Decision:** Sonata uses Foundation / System / Expression as its primary layers, with Patterns, Adaptive and Customization as cross-cutting/product-facing structures.

## D-002 — Foundation authority
**Decision:** GNOME HIG has authority over structure, behavior, navigation, accessibility, information architecture, writing and content principles.

## D-003 — System authority
**Decision:** Radix-inspired primitives, components, states and token architecture form the System layer.

## D-004 — Expression authority
**Decision:** Material 3 / Material Expressive concepts are selectively used for color, typography, shape, motion, animation, emphasis and hero composition.

## D-005 — Visual emphasis
**Decision:** Primary actions may receive substantially greater visual salience without moving outside the structural rules established by the Foundation.

## D-006 — Customization
**Decision:** User customization is a first-class Sonata capability mediated by semantic tokens.

## D-007 — Color
**Decision:** Curated accent colors are the default path, with an advanced free accent option. Neutral color is also customizable. Semantic status colors retain their semantic meaning.

## D-008 — Typography architecture
**Decision:** Sonata defines a typographic architecture rather than one mandatory font family. Red Hat Display / Text / Mono is the recommended default family architecture, with multilingual fallback support; the family remains replaceable.

## D-009 — Monospace
**Decision:** Mono is an explicit semantic role. Code and numeric/data typography are distinct concerns even when they share a family.

## D-010 — Shape
**Decision:** Shape is a semantic and customizable system. Sonata may use rounded and organic geometry without requiring every component to become a pill.

## D-011 — Surface
**Decision:** Translucency is a supported surface treatment. Glassmorphism is not mandatory and must not compromise legibility.

## D-012 — Density
**Decision:** Density is a first-class compositional property and a user customization capability. It is not equivalent to simply shrinking padding.

## D-013 — Writing
**Decision:** GNOME writing/content principles remain part of the Foundation and are not optional styling guidance.

## D-014 — Power-user patterns
**Decision:** Search, command palettes, shortcuts and related features are supported as Sonata patterns when justified by application complexity; they are not universally mandatory.

## D-015 — Adaptive classes
**Decision:** Sonata uses Mobile Class, Adaptive Class and Desktop Class. They share the design language but may use materially different compositions and interaction patterns.

## D-016 — Platform independence
**Decision:** Sonata is specified independently of any single implementation framework. Native platform conventions may be adapted at implementation time, but implementations must preserve Sonata semantics, accessibility requirements and design-language intent.

## D-017 — Customization exposure
**Decision:** Sonata provides customization capabilities globally, but applications decide which controls to expose based on context. User-facing configuration is not required to expose every supported token.

## D-018 — Accessibility precedence
**Decision:** Accessibility and operating-system/user accessibility preferences may override visual customization when necessary to preserve usability and access.

## D-019 — Localization as a first-class concern
**Decision:** Internationalization, locale-aware typography, RTL, text expansion and locale-sensitive data formatting must be treated as part of Sonata rather than implementation afterthoughts.

## D-020 — User-selectable spacing/density
**Decision:** Users may be offered coordinated interface density/spacing profiles when the application exposes that capability. Product structure remains fixed while spatial presentation varies.

## D-021 — Typography customization
**Decision:** Typeface, text scale and related typographic controls are eligible for user customization because they can affect accessibility and comfort. The application determines which controls to expose.

## D-022 — Color strategy
**Decision:** Sonata uses a hybrid color architecture: Radix-style scalable semantic/alpha roles combined with Material-inspired tonal generation. Exact algorithm remains open.

## D-023 — Capability vs exposure
**Decision:** Sonata capabilities exist at system level; each application decides which capabilities become user-facing controls.

## D-024 — Token resolution model
**Decision:** Any rendered value is resolved through three independent, ordered axes: Abstraction (`system/tokens.md` — which layer of specificity a token lives at), Precedence (`system/theming.md` — which source wins: Sonata defaults → application theme → user customization → accessibility constraints), and State (`system/components.md` — which interaction-state variant renders, applied last). Domain-specific generation algorithms (e.g. color's source→tonal→palette pipeline) run inside the Precedence axis rather than forming a competing pipeline. Accessibility's final authority (Principle 7, D-018) follows structurally from occupying the last position in the Precedence axis. See `system/resolution-model.md`.

## D-025 — Expression/Customization split of authorship
**Decision:** For any domain covered by both an `expression/*.md` file and a `customization/*.md` file, the `customization/*.md` file is the canonical source for the user/product-facing exposure surface (what can be chosen, and the named options/profiles offered); the `expression/*.md` file is the canonical source for the underlying technical mechanism (architecture, generation algorithm, scale, semantic roles). Each file states its own content once and cross-links to the other rather than restating it. This closed a standing duplication between the two directories and the gap where `expression/shape.md`, `expression/surface-depth.md` and `expression/motion.md` described customization surfaces with no corresponding `customization/*.md` file (`shape-surface.md` and `motion.md` were added to close it).

## D-026 — Sonata motion personality
**Decision:** Sonata has a distinct motion language characterized by smooth, organic and spatially coherent transitions, with subtle transformations and selective use of spring-like behavior. Material motion is a reference rather than a normative implementation.

## D-027 — Shared motion language across classes
**Decision:** Desktop and Mobile share the same Sonata motion language and personality. Implementations may adapt technical characteristics to context, but Sonata does not define separate desktop and mobile motion aesthetics.

## D-028 — Haptic interaction
**Decision:** Haptic feedback is an optional Sonata interaction modality and should be used when supported by the platform. Haptics must be semantically meaningful and must not be required for understanding an interaction. The specific haptic vocabulary and platform-strength mapping remain open (see Open Questions).

## D-029 — Morphing
**Decision:** Sonata explicitly permits morphing between semantically related component states. Shape and Motion may be combined to communicate state transitions such as action → loading → success or collapsed → expanded.

## D-030 — Iconography authority
**Decision:** Sonata specifies the iconography contract (geometry, rendering coherence, named scale, semantics, states, accessibility), not the icon family. No icon family is mandatory; Radix Icons, Lucide, Phosphor, native platform iconography or custom iconography are all compatible sources provided they satisfy the contract in `expression/iconography.md`. Exact grid, stroke weight, default rendering style and size scale remain open (see Open Questions).

## D-031 — Extensible component catalog
**Decision:** Sonata defines a normative base catalog that applications may extend with product-specific components.

## D-032 — Opinionated components
**Decision:** Official Sonata components are opinionated and should provide a preferred solution for common interaction problems.

## D-033 — Complexity boundary
**Decision:** A component must not be artificially simplified when doing so would create inconsistency, obscure semantics or fail to represent a genuinely more complex interaction. Complex cases may graduate from component → compound component → pattern → application-specific component.

## D-034 — Platform-equivalent implementation
**Decision:** Sonata components should preserve semantic identity and design-language intent across platforms without requiring pixel-identical rendering.

## D-035 — Composable variants
**Decision:** Component APIs should prefer orthogonal semantic properties and token-driven composition over combinatorial variant proliferation.

## D-036 — Token-based customization
**Decision:** Components consume Sonata semantic tokens and do not expose arbitrary independent visual styling as their normal customization mechanism.

## D-037 — Action hierarchy
**Decision:** Sonata defines Primary, Secondary, Tertiary, Quiet and Destructive semantic action roles. These roles are independent from visual emphasis (see D-005).

## D-038 — Self-explanatory interface
**Decision:** Sonata prioritizes interfaces that communicate their purpose and behavior directly through labels, established iconography, state, contextual information, hover/focus feedback, tooltips and other in-interface cues before relying on external documentation.

## D-039 — Destructive action safeguards
**Decision:** Destructive actions use a distinct semantic role and must communicate irreversible or consequential outcomes clearly, avoid accidental activation, and provide confirmation or recovery/undo where the consequence warrants it. Applications should prefer safer alternatives when practical.

## D-040 — Official Split Button
**Decision:** Split Button (a primary action paired with a menu of related alternatives) is an official Sonata component rather than an application-only pattern.

## D-041 — Official Menu Button
**Decision:** Menu Button (a primary action paired with access to related actions in a menu) is an official Sonata component.

## D-042 — Semantic input distinction
**Decision:** Sonata distinguishes semantic input roles — Text Field, Search Field, Select, Combobox, Command Input/Command Palette, and specialized inputs where genuinely required — while allowing them to share a common, highly capable text-input infrastructure. Text fields may expose composable capabilities such as clearing, validation, suggestions, autocomplete, search and contextual actions without becoming semantically equivalent to a command palette. Similar appearance does not imply identical semantics.

## D-043 — Unified command/search surfaces are scarce
**Decision:** Sonata permits unified application-level search/command surfaces when the workflow justifies them, but treats them as intentionally scarce global interaction surfaces. One global command/search surface should normally be sufficient; a second requires strong contextual justification. Sonata does not mandate a universal "super input."

## D-044 — Select and Combobox coexist
**Decision:** Select and Combobox are both official Sonata components. The choice depends on the nature, size and interaction requirements of the option set: small, stable option sets should not be forced into searchable controls, while large or difficult-to-scan option sets may justify Combobox/autocomplete behavior.

## D-045 — Progressive validation
**Decision:** Validation should occur as early as practical without unnecessarily interrupting the user's task: avoid premature interruption during editing, validate known problems after meaningful interaction or leaving the field, and validate remaining requirements at submission/completion. The underlying principle is shared across Desktop and Mobile even as exact timing adapts.

## D-046 — Required field semantics
**Decision:** Sonata explicitly communicates required fields rather than relying on widespread use of optional markers. Required status must be understandable through labels and accessible semantics.

## D-047 — Checkbox and Switch distinction
**Decision:** Checkbox represents selection or participation in a set/form context; Switch represents an on/off setting or capability whose state is persistent and immediately meaningful. They are not interchangeable visual variants.

## D-048 — Slider capability
**Decision:** Sonata Slider supports, where appropriate, single-value selection, range selection, stepped values, keyboard interaction, and direct numeric entry (or equivalent precise input) when useful. A given UI may expose only the capabilities relevant to that slider.

## D-049 — Shared input model across classes
**Decision:** Input components preserve the same semantic model across Desktop and Mobile (see D-015). Mobile implementations may adapt target size, spacing, arrangement, presentation and interaction affordances without unnecessarily creating separate semantic components.

## D-050 — Input density integration
**Decision:** Inputs participate in Sonata's global density system (D-012, D-020). Changing density must update related dimensions and spacing consistently across input components rather than independently shrinking individual fields.

## D-051 — Complex forms
**Decision:** Sonata treats complex forms as compositional patterns rather than simple sequences of label/input pairs. Official patterns should support, where appropriate, sections, groups, multi-column layouts, dependencies, progressive disclosure, summaries, validation, navigation, persistent completion actions and responsive transformation, to reduce the cognitive and interaction burden of long or complex forms.

## D-052 — Autocomplete
**Decision:** Autocomplete/typeahead is an official Sonata capability, appropriate when users need to find or select from a potentially large set of values. It should not be used merely because it is technically available.

## D-053 — Consolidated input model
**Decision:** Sonata prefers a small number of semantically meaningful input components with composable behavior over a proliferation of narrowly specialized input variants (see D-035). Differences should result in a distinct component only when they represent a distinct semantic interaction; otherwise, additional behavior should be provided compositionally. This preference for a small semantic taxonomy does not imply low capability — a common input foundation may support a rich set of composable behaviors while preserving semantic distinctions at the component and interaction level.
