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

## D-054 — Contextual navigation mechanisms
**Decision:** Sonata does not prescribe a universal navigation mechanism (Principle 17). Sidebar, navigation rail, top navigation, tabs, breadcrumbs, drill-down and contextual navigation are alternative manifestations of navigation semantics, selected according to destination count, hierarchy depth, switching frequency, available space, workflow complexity and interaction class — not competing philosophies.

## D-055 — Persistent navigation
**Decision:** Persistent navigation should be used when persistent orientation, frequent switching between destinations, or workflow efficiency materially benefits from keeping navigation visible. It is not mandatory. Users may be allowed to collapse or hide persistent navigation when the application supports that capability, whether to recover space or simply to reduce visual presence.

## D-056 — Space as a resource
**Decision:** Sonata uses available screen space when additional simultaneous information materially improves comprehension, comparison, navigation or task efficiency (Principle 18) — complex desktop applications should not be artificially constrained to a narrow central column when the space could meaningfully support multiple panes, navigation, inspectors, simultaneous form/data views or contextual information. Space should not be filled merely for the sake of filling it; application, workflow and context complexity determine how aggressively it is used.

## D-057 — Complexity accommodation
**Decision:** Sonata must support applications ranging from simple sites through moderately complex applications, professional productivity software and highly complex software up to CAD/engineering/enterprise environments, without an artificial simplicity ceiling (Principle 19). Complexity should be organized, spatially legible, hierarchically structured, discoverable and customizable rather than artificially hidden.

## D-058 — Multi-level navigation
**Decision:** Deep navigation is permitted when required by the application's domain, but navigation depth should be minimized when equivalent access can be provided through clearer composition, simultaneous visibility, direct navigation, search or workspace organization — avoiding unnecessary menu/submenu chains when a workflow could be expressed more directly.

## D-059 — Breadcrumbs
**Decision:** Breadcrumbs are an official Sonata navigation component, primarily providing orientation, hierarchy awareness and contextual navigation in complex hierarchical environments. Breadcrumb items should be interactive where navigation semantics permit; breadcrumbs supplement navigation rather than necessarily replacing primary navigation.

## D-060 — Workspaces
**Decision:** Workspace is an official Sonata concept for organizing a persistent or temporary working context — a project, task context, user workflow, document set, tool configuration or saved arrangement — including navigation state, open documents, visible/arranged panels, selected tools and user configuration. Workspaces are especially valuable in complex professional software.

## D-061 — Navigation customization
**Decision:** When application complexity justifies it, users may customize navigation and workspaces — showing/hiding, reordering or pinning destinations, collapsing navigation, choosing visible tool sets, and workspace-specific navigation/tool arrangements (create/rename/save/restore/switch, reorder, hide, pin, restore defaults) — consistent with capability being global while exposure remains contextual (D-017, Principle 9).

## D-062 — Command palette relationship
**Decision:** Command palettes and global search surfaces (D-014, D-043) supplement navigation and must not replace ordinary visible navigation. A user should be able to use an application indefinitely without knowing a command palette exists — command surfaces remain power-user capabilities, not a substitute for discoverable navigation.

## D-063 — Mobile navigation adaptation
**Decision:** Mobile may use a materially different navigation presentation from Desktop while the semantic navigation architecture — the destination hierarchy — remains consistent (see D-015). Mobile should not simply render a compressed desktop sidebar when another navigation mechanism better fits the interaction environment, and should be particularly careful about deep sequential navigation, preferring progressive disclosure, drill-down, contextual navigation, direct navigation or search over unnecessary nested menus.

## D-064 — Navigation density
**Decision:** Navigation participates in Sonata's global density system (see D-012, D-020, D-050). Changing density should coordinate item spacing, row heights, control dimensions, icon sizing, label spacing and group spacing without breaking navigation hierarchy or accessibility.

## D-065 — Data Display as first-class system
**Decision:** Tables, lists and complex data presentations are first-class Sonata components and patterns (see D-057, Principle 19) — Sonata must support data interfaces ranging from simple collections to highly complex professional software without an artificial simplicity ceiling.

## D-066 — Table density
**Decision:** Tables participate in Sonata's global density system (see D-012, D-020, D-050, D-064) and support Comfortable, Balanced, Compact and Dense profiles, coordinating row height, cell padding, typography, spacing, icon size and control dimensions rather than compressing individual elements independently.

## D-067 — Data customization
**Decision:** Applications may allow users to resize, reorder, show/hide and pin/freeze columns and configure sorting, filtering and grouping when appropriate. Common configuration changes should be easy to reverse (Principle 22) — undo, reset, restore defaults or saved presets rather than manual reconstruction.

## D-068 — Selection models
**Decision:** Sonata supports single, multi, range and select-all selection models where semantically appropriate, with explicit and accessible selection behavior.

## D-069 — Data editing
**Decision:** Sonata supports inline, row, cell, and inspector/form-based editing as official data-editing patterns. The editing mechanism should reflect the complexity and risk of the operation; inline editing should not be used where it would obscure validation or workflow requirements.

## D-070 — Inspector
**Decision:** Inspector is an official Sonata component/pattern providing contextual information or editing tools for the currently selected object. It may be persistent, collapsible, hidden or invoked on demand, and is not mandatory in every data interface.

## D-071 — Master-Detail
**Decision:** Master-Detail is an official Sonata pattern for selecting an item in one context and examining or editing its details in another (adjacent panel, inspector, modal, sheet or dedicated view, depending on context and interaction class).

## D-072 — Split View
**Decision:** Split View is an official Sonata pattern for simultaneous presentation of related contexts (e.g. list + detail, table + inspector). Pane count is determined by workflow utility rather than screen size alone.

## D-073 — Responsive data transformation
**Decision:** Data representations may change between Desktop and Mobile when necessary for usability (see D-063). Mobile may add interaction depth — e.g. table → list, persistent inspector → detail screen — to avoid overwhelming presentations, provided semantically relevant information remains accessible.

## D-074 — Data-display expression
**Decision:** Dense data interfaces generally use restrained visual expression, reserving stronger color, motion and emphasis for selection/active state, errors, warnings, primary actions, important status and contextual controls.

## D-075 — Active vs historical priority
**Decision:** When a domain distinguishes active, pending or in-progress work from completed or historical information, current work should generally receive greater spatial and interaction priority (Principle 20). Historical information remains accessible without automatically competing for equal prominence; the treatment is contextual rather than universal.

## D-076 — Virtualization
**Decision:** Virtualization is an official implementation capability for large data collections when applicable, without changing the semantic data-display model presented to the user.

## D-077 — Workspace-integrated data configuration
**Decision:** Data-display configuration — columns, filters, sorting, grouping, visible panels, inspector state — may be stored within Sonata Workspaces (D-060), so users can switch between contextually meaningful data-presentation arrangements.

## D-078 — Selection as a first-class system
**Decision:** Selection is a first-class Sonata system and semantic state of the underlying data/object model. It extends the selection models decided in D-068 (single, multi, range, select-all) with toggle selection. The full model is defined in `system/selection.md`.

## D-079 — Selection state distinction
**Decision:** Selected, focused, hovered, active, checked and highlighted are distinct semantic/interaction states and must not be conflated.

## D-080 — Shared selection across views
**Decision:** Selection belongs to the underlying data/object model and may be observed by multiple views such as Table, List and Inspector.

## D-081 — Selection summary
**Decision:** Meaningful multi-selection should communicate its scope through a visible selection summary.

## D-082 — Contextual selection actions
**Decision:** Actions operating on a selection should become contextually discoverable and appropriately prominent when selection exists.

## D-083 — Selection persistence
**Decision:** Selection may persist across views, filtering, sorting, pagination and virtualization when the underlying data model and workflow justify it, with scope remaining clear.

## D-084 — Spreadsheet workflows
**Decision:** Spreadsheet-like selection is an explicit supported Sonata use case, including efficient row/cell selection, range selection, keyboard operation and bulk actions.

## D-085 — Selection Mode
**Decision:** Selection Mode is an official Sonata pattern for workflows in which temporarily transforming the interface into a selection-focused context improves usability.

## D-086 — Mobile selection mode
**Decision:** Mobile may use platform-appropriate selection gestures and temporarily transform the UI into a selection-focused mode while preserving the same semantic selection model.

## D-087 — Selection and undo
**Decision:** Reversible operations performed on selections should integrate with the application's undo/redo system where practical.

## D-088 — Selection visual expression
**Decision:** Selection may use Sonata accent and Expression mechanisms, but must remain distinguishable from other states and must not depend exclusively on color.

## D-089 — Feedback as a first-class system
**Decision:** Feedback is a first-class Sonata component/system category rather than an application-specific afterthought.

## D-090 — Proportional feedback
**Decision:** Feedback presentation should be proportional to severity, urgency, persistence and context.

## D-091 — Undo-first recovery
**Decision:** When an operation is reversible, Sonata should strongly favor Undo or equivalent direct recovery.

## D-092 — Progressive error communication
**Decision:** Errors should communicate what happened, relevant consequence, and available recovery or next action when that information is available.

## D-093 — Error severity
**Decision:** Sonata distinguishes error severity independently from presentation persistence. Applications should distinguish recoverable, significant and critical errors where relevant.

## D-094 — Contextual inline feedback
**Decision:** Inline feedback is appropriate when it belongs directly to a local interaction or content context, but feedback should not unnecessarily disrupt layout.

## D-095 — Layout stability
**Decision:** Feedback should avoid unnecessary layout displacement. Floating, overlay or reserved contextual presentation may be preferred when equivalent clarity can be achieved without pushing established interface content.

## D-096 — Background operations
**Decision:** Long-running operations should remain non-blocking when safely possible, allowing users to continue unrelated work.

## D-097 — Proportional completion feedback
**Decision:** Completion feedback should be proportional to the significance of the completed operation.

## D-098 — Empty State
**Decision:** Empty State is an official Sonata component/pattern and must distinguish meaningful empty conditions such as no data, no results, filtering, loading and error.

## D-099 — Progress
**Decision:** Sonata officially supports determinate, indeterminate, staged and background progress representations, with ETA where a meaningful estimate is available.

## D-100 — Persistent status
**Decision:** Persistent status represents ongoing conditions and should update as the condition changes rather than repeatedly generate identical notifications.

## D-101 — Notification system
**Decision:** Notifications and Notification Center are official Sonata capabilities.

## D-102 — Notification persistence
**Decision:** Only events with meaningful continuing relevance should enter persistent notification history.

## D-103 — Notification grouping
**Decision:** Related notifications should be groupable when grouping reduces repetition and noise.

## D-104 — Feedback color semantics
**Decision:** Success, warning, danger and informational semantics may use Sonata semantic colors, but feedback meaning must not depend on color alone.

## D-105 — Feedback motion
**Decision:** Motion may reinforce feedback, but functional comprehension takes priority over decorative animation.

## D-106 — Feedback accessibility
**Decision:** Important and dynamic feedback must be exposed through appropriate accessibility semantics in addition to visual presentation.

## D-107 — Feedback writing
**Decision:** Feedback follows GNOME-derived Sonata writing principles (D-013) and should favor specific, direct and actionable communication over vague error language.

## D-108 — Content Space
**Decision:** Content Space is an official Sonata concept representing a coherent semantic working context that may contain multiple coordinated regions.

## D-109 — Composition concepts
**Decision:** Region, Pane and Panel are official Sonata composition concepts.

## D-110 — Context preservation
**Decision:** When related regions belong to the same Content Space, changes to contextual regions should preserve the primary context where practical.

## D-111 — Composition modes
**Decision:** Sonata officially supports horizontal, vertical, stacked, split, overlay, floating, modal and master-detail composition.

## D-112 — Region expansion
**Decision:** Regions may temporarily expand to occupy the Content Space when detailed work benefits from additional space, with a clear mechanism to restore the previous composition.

## D-113 — User-resizable composition
**Decision:** Users may resize appropriate panes and panels, and these preferences may be persisted as Workspace state.

## D-114 — Composition customization
**Decision:** Applications may allow users to show, hide, collapse, reorder and configure contextual regions when application complexity justifies it.

## D-115 — Composition fragmentation
**Decision:** Sonata explicitly discourages unnecessary fragmentation of Content Space. Regions should exist because they represent meaningful relationships or simultaneous work.

## D-116 — Composition is distinct from navigation
**Decision:** Updating or changing a region within the same Content Space does not inherently constitute navigation.

## D-117 — Adaptive composition
**Decision:** Desktop and Mobile may use substantially different spatial compositions while preserving the same semantic relationships between regions.

## D-118 — Native window chrome
**Decision:** Sonata applications should primarily rely on native platform window chrome rather than duplicating title-bar functionality inside application content.

## D-119 — Optional compact application header
**Decision:** A separate application header is optional. It should be compact and introduced only when contextual identity or controls materially benefit from it.

## D-120 — Toolbar as compositional system
**Decision:** Toolbars are official Sonata components and are not constrained to horizontal layouts. They may be horizontal, vertical, docked, floating, contextual or inline according to workflow and platform.

## D-121 — Toolbar scope
**Decision:** Toolbar actions may belong to application, view, selection or tool scope. These scopes must remain semantically distinguishable.

## D-122 — Multiple windows
**Decision:** Multiple application windows are an official Sonata capability when independent or simultaneous contexts materially benefit the workflow.

## D-123 — Multi-monitor support
**Decision:** Sonata applications should accommodate multi-monitor workflows where supported by the platform.

## D-124 — Window state
**Decision:** Applications may preserve useful window state such as geometry, maximization, fullscreen and workspace association according to platform conventions.

## D-125 — Shell/content distinction
**Decision:** Application chrome, content, contextual UI, transient UI and system UI remain conceptually distinct.

## D-126 — Workspace/window distinction
**Decision:** Workspace is a working context; Window is a presentation container for that context; Document/View represents content within it.

## D-127 — Shell customization
**Decision:** Applications may expose user customization of navigation, tool visibility, toolbar contents, docking, panel dimensions and layout when justified by application complexity.

## D-128 — Compact mobile shell
**Decision:** Mobile may substantially reduce persistent application chrome while preserving the same semantic relationships and allowing contextual access to functionality.

## D-129 — Shell expression
**Decision:** Application shells may express product identity, but expressive treatment must remain subordinate to application orientation and workflow.

## D-130 — Disclosure as a first-class system
**Decision:** Disclosure is a first-class Sonata component/pattern family for revealing and collapsing related information without changing semantic context.

## D-131 — Progressive disclosure
**Decision:** Progressive disclosure is an official Sonata principle for managing complexity, but must not be used to arbitrarily hide functionality that users need.

## D-132 — Accordion and Collapsible
**Decision:** Accordion and Collapsible are distinct official components. Accordion groups related sections; Collapsible represents an independently expandable region.

## D-133 — Expandable rows
**Decision:** Expandable rows are an official pattern for brief details belonging directly to items in lists and tables.

## D-134 — Disclosure depth
**Decision:** Nested disclosure is permitted when justified, but excessive nesting should be avoided. Sonata uses contextual judgment rather than a universal hard numeric limit.

## D-135 — Menu and Context Menu
**Decision:** Menu and Context Menu are official Sonata components for actions and choices. They are not substitutes for primary application navigation.

## D-136 — Menu depth
**Decision:** Deeply nested menus are strongly discouraged. Applications should prefer direct actions, composition, contextual panels, search or command surfaces when they provide clearer access.

## D-137 — Hover disclosure
**Decision:** Hover may expose supplementary information or low-risk controls, but critical functionality must not depend exclusively on hover.

## D-138 — Touch disclosure
**Decision:** Touch may use established gestures such as long press or swipe for contextual disclosure, but critical functionality must remain accessible without obscure gestures.

## D-139 — Disclosure and workspace
**Decision:** User-configured expansion/collapse states may become part of Workspace state when useful.

## D-140 — Disclosure and motion
**Decision:** Disclosure transitions should use Sonata Motion where motion improves causal and spatial understanding.
