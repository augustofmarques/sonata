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
