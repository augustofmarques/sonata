# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

Sonata is a **design language specification**, written entirely as Markdown documentation — there is no source code, build system, package manager, or test suite. All work here is writing/editing spec documents. The `system:init`-style commands (build/lint/test) do not apply to this repo.

## Core concept

Sonata is a bespoke, composed design language, not an original one. It layers three borrowed foundations plus three Sonata-native concerns:

- **Foundation — GNOME HIG** (`foundation/`): information architecture, layout, navigation, interaction, accessibility, writing/content. Grounded in the GNOME Human Interface Guidelines.
- **System — Radix-inspired** (`system/`): primitives, components, states, tokens, surfaces, theming — construction mechanisms, not visual identity.
- **Expression — Material-inspired** (`expression/`): color, typography, shape, motion, animation, visual emphasis, hero composition — expressive technique, not a component mandate.
- **Patterns — Sonata-native** (`patterns/`): search, command palette, shortcuts, data, power-user workflows. Optional, applied when justified by an app's complexity.
- **Adaptive — Sonata-native** (`adaptive/`): Mobile, Adaptive, and Desktop interaction classes.
- **Customization — Sonata-native** (`customization/`): user-controlled visual/accessibility preferences, mediated by tokens.

Core principle (governs all decisions): **"Structure determines where. Expression determines how strongly."**

### Authority hierarchy

When sources conflict, resolve in this order (see `governance/authority-matrix.md` for the full per-domain table):

1. Accessibility and platform accessibility requirements
2. Foundation / GNOME HIG
3. Sonata semantic rules
4. System / Radix-inspired implementation
5. Expression / Material-inspired techniques
6. Component defaults

Structural/semantic questions → Foundation decides. Implementation questions → System decides. Expression questions → Sonata Expression decides. Accessibility can override any visual preference, always.

## Repository structure

```
governance/       principles, decision log, open questions, authority matrix, glossary
foundation/        GNOME HIG-derived: layout, interaction, accessibility, writing, content, i18n
system/            Radix-inspired: primitives, components, tokens, surfaces, theming
expression/        Material-inspired: color, typography, shape, motion, emphasis, iconography, surface-depth
patterns/          search, command-palette, shortcuts, data, power-user
adaptive/          mobile, adaptive, desktop classes, input-modality
customization/     user-facing color, typography, density, shape/surface, accessibility, motion
implementation/    platform translation, tokens, validation, and the future "Sonata skill"
references/        notes on the external systems Sonata borrows from (GNOME, Radix, Material, typography)
```

The root `README.md` is the master index/table of contents and also carries the current "working status" (what's decided vs. still open) and a "working method" section. Treat it as the entry point for navigating the spec.

**Note:** the repo root also contains stray duplicate files — `README(1).md`, `README(3).md`, plus root-level `principles.md`, `decision-log.md`, `open-questions.md` that shadow the canonical copies under `governance/`. These appear to be leftover duplicate downloads with diverging content (e.g. `README(3).md` describes a newer "Consolidated Working Draft 0.4" with a Decided/Recommended/Open/Reference status model not yet reflected in the canonical `README.md`). Don't treat any of the root-level duplicates as authoritative without checking with the user — `governance/*.md` and the root `README.md` are the ones referenced by the table of contents.

## Working method for adding/editing spec content

Each subject/topic module should be documented in four parts where applicable (per `README.md`'s "Working method"):

1. **Inherited principles** — what comes from GNOME, Radix, or Material.
2. **Sonata decisions** — what Sonata changes or establishes itself.
3. **Customization** — what the product/user may change.
4. **Open questions** — unresolved decisions that should not be silently assumed.

When a new normative decision is made, add an entry to `governance/decision-log.md` (sequential `D-XXX` IDs, each with a one-line `**Decision:**` statement). When a decision is deliberately deferred, record it in `governance/open-questions.md` rather than silently assuming an answer — the spec treats open questions as intentional, not missing documentation.

`governance/principles.md` holds the 15 foundational Sonata principles (e.g. "Structure before decoration", "Accessibility has final authority", "Capability is global; exposure is contextual") — check new decisions against these before adding them.

`governance/glossary.md` defines Sonata-specific terms (Adaptive Class, Density, Hero, Shape Profile, Token, etc.) — use these terms consistently rather than inventing new vocabulary for the same concepts.

## Reference sources

`references/README.md` groups the external design systems by role, not equal normativity:

- **GNOME HIG** — normative foundation for structure/interaction/accessibility/writing.
- **Radix Primitives / Themes** — system reference for primitives, tokens, theming mechanics.
- **Material 3 / Material Expressive / Material Color Utilities** — expression reference for color, motion, shape, hero composition.
- **Red Hat Design System** — typography reference (recommended default family architecture: Display/Text/Mono + Noto fallbacks).

Sonata adopts selected ideas from these; it does not inherit their full UX or visual identity.
