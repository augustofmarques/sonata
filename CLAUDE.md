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

### Token resolution model

Any rendered value resolves through three independent axes, in this order (D-024, full model in `system/resolution-model.md`):

1. **Abstraction** (`system/tokens.md`) — which layer of specificity a token lives at: raw values → foundation/system tokens → semantic tokens → component tokens.
2. **Precedence** (`system/theming.md`) — which source wins: Sonata spec defaults (including domain-specific generation algorithms, e.g. color's source→tonal→palette pipeline in `expression/color.md`) → application theme → user customization → accessibility constraints. Accessibility is last, which is the structural reason it has final authority.
3. **State** (`system/components.md`) — which interaction-state variant (hover/pressed/disabled/…) renders, applied last, after axes 1–2 produce a base value.

When adding a new domain's customization/generation rules (shape, motion, spacing, …), say explicitly which Axis-B step they run at, the way `expression/color.md` does — don't introduce a fourth competing pipeline diagram.

### Editorial convention: Expression vs. Customization

For any domain covered by both directories (color, typography, density, shape/surface, motion), `customization/*.md` is the canonical source for the **user/product-facing exposure surface** (what can be chosen, named options/profiles); `expression/*.md` is the canonical source for the **underlying technical mechanism** (architecture, generation algorithm, scale, semantic roles). State each fact once, cross-link the other direction — don't restate (D-025). When adding a new Expression domain that's meant to be customizable, add its `customization/*.md` counterpart in the same change; don't leave the exposure surface implied only inside the Expression file.

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

The root `README.md` is the master index/table of contents and also carries the current "working status" (what's decided vs. still open), the document status model (Decided/Recommended/Open/Reference), and a "working method" section. Treat it as the entry point for navigating the spec.

The repo is git-tracked. Watch for repeated duplicate-download files landing at the root (e.g. `README(1).md`, `README(3).md` and similar numbered copies, or stray top-level `principles.md`/`decision-log.md`/`open-questions.md`) — these have shown up more than once as leftover browser downloads shadowing the canonical `governance/*.md` files and the root `README.md`. Before trusting one as authoritative, diff it against the canonical file it shadows; if it's a pure duplicate or a strict subset, remove it, if it has genuinely newer content, consolidate it into the canonical file instead of keeping both.

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

## Known gaps (as of the 2026-09-07 audit)

- **Most domain files are conceptual, not normative.** They read as prose + bullet lists ending in "## Open decisions," not concrete specs — there are no actual numeric token values, no color-generation algorithm, no type/spacing/shape scales, no motion durations, no icon family, and section "07. Components" in `README.md` is a name-only placeholder with zero component specs. `implementation/skill.md` explicitly says the Sonata skill can't be written until the spec is more concrete. Don't assume a value exists just because a concept is named — check before citing a "default" as if it were decided.
- Only `expression/color.md`, `typography.md`, `shape.md`, `surface-depth.md`, `spacing-density.md`, `motion.md`, `iconography.md`, and `system/resolution-model.md` currently carry a `## Status` header (the Decided/Recommended/Open/Reference model from the README). The rest of the corpus doesn't use it yet.
