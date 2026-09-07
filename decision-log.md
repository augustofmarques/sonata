# Sonata Decision Log

## D-001 — Architecture
**Decision:** Sonata uses Foundation / System / Expression as its primary layers.

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
**Decision:** Curated accent colors are provided by default, with an advanced free accent option. Neutral color is also customizable. Semantic status colors retain their semantic meaning.

## D-008 — Typography
**Decision:** Sonata defines a typographic architecture rather than one mandatory font family. Red Hat Display / Text / Mono is the current recommended default family, with multilingual fallback support; the family remains replaceable.

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
**Decision:** Search, command palettes, shortcuts and related features are supported as Sonata patterns when justified by the application's complexity; they are not universally mandatory.

## D-015 — Adaptive classes
**Decision:** Sonata uses Mobile Class, Adaptive Class and Desktop Class. They share the design language but may use materially different compositions and interaction patterns.
