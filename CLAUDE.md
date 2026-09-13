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

- **Most domain files are conceptual, not normative, though this is starting to change.** They mostly read as prose + bullet lists ending in "## Open decisions," not concrete specs — there is still no color-generation algorithm, no type scale, no motion durations, and no exact radius/density-transform values. But spacing and shape now have real numeric/named scales: `expression/spacing-density.md` has a v1 candidate spacing baseline (0/2/4/6/8/12/16/20/24/32/40/48/64/80/96, D-205) and the four density profiles with Balanced as default and per-class availability (D-206–D-208); `expression/shape.md` has the shape-scale token names and five named personalities, Subtle/Soft/Rounded/Expressive/Organic — "Subtle" renames the old "Geometric" (D-209–D-211). Exact radius values and density transform tables are still open. No icon family is mandated by design (D-030), not as a placeholder. Section "07. Components" in `README.md` now has a decided catalog architecture (`system/components.md`, D-031–D-036: Primitive → Core Component → Compound Component → Pattern → Application Component), a semantic Actions spec (`system/actions.md`, D-037–D-041: Button/Icon Button/Toggle/Menu Button/Split Button roles and behavior), a semantic Inputs spec (`system/inputs.md`, D-042–D-053: Text Field/Select/Combobox/Checkbox/Switch/Slider roles, validation, forms), a Navigation spec (`system/navigation.md` + `foundation/layout.md`, D-054–D-064: Sidebar/Rail/Tabs/Breadcrumbs, persistent-nav rationale, space-as-a-resource, workspaces), a Data Display spec (`system/data-display.md`, D-065–D-077: Table/List/Inspector/Master-Detail/Split View, density, editing, selection, active-vs-historical priority), a Selection spec (`system/selection.md`, D-068, D-078–D-088: selection models, selection-vs-state distinction, shared selection across views, summary/contextual actions, persistence, spreadsheet workflows, Selection Mode), a Feedback spec (`system/feedback.md`, D-089–D-107: feedback-form taxonomy, proportionality, Undo-first recovery, error communication/severity, layout stability, background operations, Empty State, Progress, persistent status, Notification/Notification Center), a Composition spec (`system/composition.md`, D-108–D-117: Content Space, Region/Pane/Panel, composition modes, expansion, resizing, fragmentation restraint, composition-vs-navigation, adaptive composition), and an Application Shell / Window / Toolbar spec (`system/application-shell.md`, `system/window.md`, `system/toolbar.md`, D-118–D-129: native-chrome precedence, optional compact header, compositional Toolbar with application/view/selection/tool scopes, multiple windows, multi-monitor support, window state, shell/content/system-UI distinction, Workspace→Window→Content Space→View relationship, shell customization, compact mobile shell), a Disclosure spec (`system/disclosure.md`, D-130–D-140: Accordion/Collapsible/Expandable Row/Menu/Context Menu taxonomy, progressive disclosure, disclosure-vs-navigation, disclosure/menu depth restraint, hover/touch accessibility), an Overlays spec (`system/overlays.md`, D-141–D-155: Popover/Tooltip/Dialog/Modal/Sheet/Drawer/Floating Panel/Full-screen Overlay taxonomy, modal scope, overlay-vs-disclosure-vs-navigation, no arbitrary nesting, promotion to persistent workspace UI), a Containers spec (`system/containers.md`, D-156–D-171, D-174: Container/Group/Section/Card/Panel/Stack/Cluster/Grid/Inset-Well/Separator taxonomy, surface-independence, full-bleed, sticky regions, indentation as a semantic-plus-visual pattern, tablet/intermediate composition, rounded floating surfaces), a State & Interaction Model / Operations spec (`system/state.md`, `system/operations.md`, D-175–D-191: domain-vs-UI state, four persistence scopes, composable state, Unavailable/Disabled/Read-only/Locked/Hidden taxonomy, Dirty/Saved/Synced distinction, offline/degraded operation, sync conflict, optimistic operations, Operations as first-class entities, shared state across views, workspace-state restoration boundaries), and a Token Architecture / Theming / OOBE round (`system/tokens.md`, `system/theming.md`, `system/resolution-model.md`, `patterns/oobe.md`, `patterns/onboarding.md`, `governance/authority-matrix.md`, D-192–D-204: four-layer token abstraction with State tokens as independently themeable Component-token variants, Theme/Preference/Preset distinction, user-customization structural boundary, application token extensibility, the Reference Authority classification model, and official OOBE/Onboarding patterns favoring demonstration over lengthy text) — but still no exact token values/dimensions, and no specs at all yet for other remaining component categories (data visualization). `implementation/skill.md` explicitly says the Sonata skill can't be written until the spec is more concrete. Don't assume a value exists just because a concept is named — check before citing a "default" as if it were decided.
- Only `expression/color.md`, `typography.md`, `shape.md`, `surface-depth.md`, `spacing-density.md`, `motion.md`, `iconography.md`, `system/components.md`, `system/actions.md`, `system/inputs.md`, `system/navigation.md`, `system/data-display.md`, `system/selection.md`, `system/feedback.md`, `system/composition.md`, `system/application-shell.md`, `system/window.md`, `system/toolbar.md`, `system/disclosure.md`, `system/overlays.md`, `system/containers.md`, `system/state.md`, `system/operations.md`, `system/tokens.md`, `system/theming.md`, `foundation/layout.md`, and `system/resolution-model.md` currently carry a `## Status` header (the Decided/Recommended/Open/Reference model from the README). The rest of the corpus doesn't use it yet.
