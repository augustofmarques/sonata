# Sonata
## Design Language Specification

**Status:** Consolidated Working Draft 0.4
**Purpose:** Master index and navigation for the Sonata design language.

Sonata is a bespoke adaptive design language for desktop and mobile-class software. It combines complementary foundations without treating them as a single visual system:

- **Foundation — GNOME HIG:** structure, information architecture, interaction, accessibility, writing and content principles.
- **System — Radix-inspired:** primitives, components, states, tokens, surfaces, theming and reusable construction mechanisms.
- **Expression — Material-inspired:** color, typography, shape, motion, animation, visual emphasis and hero composition.
- **Patterns — Sonata-native:** search, command palette, shortcuts, data and power-user workflows.
- **Adaptive — Sonata:** Mobile, Adaptive and Desktop classes.
- **Customization — Sonata:** user-controlled visual preferences and accessibility preferences.

## Core principle

> **Structure determines where. Expression determines how strongly.**

## Authority hierarchy

1. Accessibility and platform accessibility requirements
2. Foundation / GNOME HIG
3. Sonata semantic rules
4. System / Radix-inspired implementation
5. Expression / Material-inspired techniques
6. Component defaults

The hierarchy concerns decision authority, not visual imitation. See [Authority Matrix](governance/authority-matrix.md) for the full per-domain breakdown.

## Document status model

Each module may contain content in one or more of these states:

- **Decided** — normative Sonata rule.
- **Recommended** — strong default, but replaceable.
- **Open** — design decision not yet frozen.
- **Reference** — borrowed idea that informs Sonata but is not itself binding.

---

# Table of Contents

### 00. Governance
- [Principles](governance/principles.md)
- [Decision Log](governance/decision-log.md)
- [Open Questions](governance/open-questions.md)
- [Authority Matrix](governance/authority-matrix.md)
- [Glossary](governance/glossary.md)

### 01. Foundation — GNOME HIG
- [Overview](foundation/overview.md)
- [Layout & Information Architecture](foundation/layout.md)
- [Interaction & Navigation](foundation/interaction.md)
- [Accessibility](foundation/accessibility.md)
- [Writing](foundation/writing.md)
- [Content](foundation/content.md)
- [Internationalization](foundation/i18n.md)

### 02. System — Radix-inspired
- [Overview](system/overview.md)
- [Primitives](system/primitives.md)
- [Components & States](system/components.md)
- [Actions](system/actions.md)
- [Inputs](system/inputs.md)
- [Navigation](system/navigation.md)
- [Data Display](system/data-display.md)
- [Selection](system/selection.md)
- [Feedback](system/feedback.md)
- [Composition](system/composition.md)
- [Application Shell](system/application-shell.md)
- [Window](system/window.md)
- [Toolbar](system/toolbar.md)
- [Disclosure](system/disclosure.md)
- [Tokens](system/tokens.md)
- [Surfaces & Overlays](system/surfaces.md)
- [Theming](system/theming.md)
- [Token Resolution Model](system/resolution-model.md)

### 03. Expression — Material-inspired
- [Overview](expression/overview.md)
- [Color](expression/color.md)
- [Typography](expression/typography.md)
- [Shape](expression/shape.md)
- [Surface & Depth](expression/surface-depth.md)
- [Spacing & Density](expression/spacing-density.md)
- [Motion](expression/motion.md)
- [Visual Emphasis & Hero](expression/emphasis.md)
- [Iconography](expression/iconography.md)

### 04. Adaptive
- [Overview](adaptive/overview.md)
- [Mobile Class](adaptive/mobile.md)
- [Adaptive Class](adaptive/adaptive.md)
- [Desktop Class](adaptive/desktop.md)
- [Input Modality](adaptive/input-modality.md)

### 05. Patterns
- [Overview](patterns/overview.md)
- [Search](patterns/search.md)
- [Command Palette](patterns/command-palette.md)
- [Shortcuts](patterns/shortcuts.md)
- [Data](patterns/data.md)
- [Selection](patterns/selection.md)
- [Feedback](patterns/feedback.md)
- [Notifications](patterns/notifications.md)
- [Composition](patterns/composition.md)
- [Workspace](patterns/workspace.md)
- [Disclosure](patterns/disclosure.md)
- [Power User](patterns/power-user.md)

### 06. Customization
- [Overview](customization/overview.md)
- [Color](customization/color.md)
- [Typography](customization/typography.md)
- [Density](customization/density.md)
- [Shape & Surface](customization/shape-surface.md)
- [Motion](customization/motion.md)
- [Accessibility](customization/accessibility.md)

### 07. Components & Patterns

Catalog architecture is decided — see [Components & States](system/components.md) for the Primitive → Core Component → Compound Component → Pattern → Application Component graduation ladder (D-031–D-036). Actions ([`system/actions.md`](system/actions.md), D-037–D-041), Inputs ([`system/inputs.md`](system/inputs.md), D-042–D-053), Navigation ([`system/navigation.md`](system/navigation.md), D-054–D-064), Data Display ([`system/data-display.md`](system/data-display.md), D-065–D-077), Selection ([`system/selection.md`](system/selection.md), D-068, D-078–D-088), Feedback ([`system/feedback.md`](system/feedback.md), D-089–D-107), Composition ([`system/composition.md`](system/composition.md), D-108–D-117), Application Shell ([`system/application-shell.md`](system/application-shell.md), [`system/window.md`](system/window.md), [`system/toolbar.md`](system/toolbar.md), D-118–D-129) and Disclosure ([`system/disclosure.md`](system/disclosure.md), D-130–D-140) now have decided semantic models.

Concrete specifications for the remaining categories remain planned, pending a stable foundation and token system:

- Dialogs
- Sheets
- Cards
- Data visualization

### 08. Implementation
- [Platform](implementation/platform.md)
- [Tokens](implementation/tokens.md)
- [Validation](implementation/validation.md)
- [Sonata Skill](implementation/skill.md)

### 09. References
- [Reference index](references/README.md)
- [GNOME](references/gnome.md)
- [Radix](references/radix.md)
- [Material](references/material.md)
- [Material Expressive](references/material-expressive.md)
- [Typography](references/typography.md)

The implementation must translate Sonata, not redefine it.

---

# Current architecture

```text
                         SONATA
                            │
       ┌────────────────────┼────────────────────┐
       │                    │                    │
  FOUNDATION             SYSTEM             EXPRESSION
  GNOME HIG              RADIX              MATERIAL
       │                    │                    │
 structure              primitives             color
 layout                 components              type
 hierarchy              tokens                  shape
 navigation             states                  motion
 interaction            surfaces                animation
 accessibility          theming                 emphasis
 writing                                       hero
       │                    │                    │
       └────────────────────┼────────────────────┘
                            │
                         PATTERNS
                            │
             search · command · shortcuts
                data · power workflows
                            │
                         ADAPTIVE
                            │
           mobile · adaptive · desktop
                            │
                          TOKENS
                            │
                 ┌──────────┴──────────┐
                 │                     │
          PRODUCT DEFAULTS      USER CUSTOMIZATION
                 │                     │
                 └──────────┬──────────┘
                             │
                       ACCESSIBILITY
                         CONSTRAINTS
                            │
                            ▼
                         UI OUTPUT
```

---

# Working status

## Completed / provisionally decided

- Three-layer architecture: Foundation / System / Expression, with Patterns, Adaptive and Customization as cross-cutting/product-facing structures.
- GNOME HIG remains authoritative for structure and behavior.
- GNOME writing/content principles are explicitly retained.
- Radix is primarily a construction and token foundation, not the visual identity.
- Material is primarily an expressive reference, not a component mandate.
- Desktop Class and Mobile Class are distinct interaction compositions; Adaptive Class bridges them.
- User customization is first-class and token-driven.
- Accent color is highly customizable; curated palette + advanced arbitrary accent color; neutral palette may also be customized. Semantic success/warning/danger/info roles are protected.
- Typography is a system-level architecture, not locked to one font family. Recommended default: Red Hat Display / Text / Mono, with multilingual fallback strategy, while remaining replaceable. Mono is an explicit semantic role distinct from numeric typography.
- Shape is customizable and may range from subtle to expressive/organic.
- Translucent surfaces are supported but glassmorphism is not mandatory.
- Density is a first-class user preference, not merely smaller padding.
- Search, command palettes, shortcuts and other advanced workflows are Sonata patterns, not universal requirements.
- Primary actions may receive substantially higher visual salience when justified.
- Sonata is specified independently of any single implementation framework; native platform conventions may be adapted at implementation time without violating Sonata semantics.
- Accessibility and OS/user accessibility preferences may override visual customization when necessary.
- Internationalization, locale-aware typography, RTL, text expansion and locale-sensitive formatting are first-class Sonata concerns, not implementation afterthoughts.
- Color strategy is a hybrid architecture: Radix-style scalable semantic/alpha roles combined with Material-inspired tonal generation (exact algorithm remains open).
- Token values resolve through a single three-axis model — Abstraction, Precedence, State — reconciling what were previously three separate, uncoordinated pipeline diagrams. See [Token Resolution Model](system/resolution-model.md).
- Expression and Customization now split cleanly per domain: `expression/*.md` owns the technical mechanism, `customization/*.md` owns the user/product-facing exposure surface, cross-linked rather than duplicated. Shape & Surface and Motion gained their own customization pages, closing a gap left by earlier drafts.
- Motion has a distinct Sonata personality (smooth, organic, spatially coherent) rather than simply inheriting Material's motion language; Desktop and Mobile share this personality even where technical timing adapts.
- Sonata explicitly supports morphing between semantically related states (e.g. action → loading → success), combining Shape and Motion.
- Haptic feedback is a supported, optional interaction modality; it must never be required to understand an interaction. The specific haptic vocabulary remains open.
- Sonata specifies the iconography contract (geometry, rendering coherence, named scale, semantics, states, accessibility), not the icon family — no family is mandatory, provided a compatible source (Radix Icons, Lucide, Phosphor, native or custom) satisfies the contract.
- Sonata defines an extensible, opinionated component catalog (Primitive → Core Component → Compound Component → Pattern → Application Component). Complexity is a valid reason to graduate to a more specific abstraction rather than forcing an interaction into an existing component; components preserve semantic identity across platforms without pixel-identical rendering, and prefer orthogonal token-driven props over combinatorial variants.
- Actions have a semantic role hierarchy (Primary/Secondary/Tertiary/Quiet/Destructive) independent of visual emphasis; Split Button and Menu Button are official components. Sonata prioritizes self-explanatory interfaces (labels, iconography, state, tooltips) over offloading discoverability to documentation, and destructive actions must guard against accidental activation and communicate consequence. See [Actions](system/actions.md).
- Inputs share a common, highly capable text-input infrastructure while keeping distinct semantic roles (Text Field/Search Field/Select/Combobox/Command Input); Select and Combobox coexist as separate official components. Validation is progressive (avoid interrupting mid-edit), required fields are explicit, Checkbox and Switch are semantically distinct, and a unified global command/search surface is intentionally scarce (typically 0–1, exceptionally 2). See [Inputs](system/inputs.md).
- Sonata does not prescribe one universal navigation mechanism (Sidebar/Rail/Top nav/Tabs/Breadcrumbs are alternative manifestations, not competing philosophies); persistent navigation is used when it materially benefits orientation or switching, not by default. Available space is a resource — complex desktop applications should use multi-pane composition rather than being confined to a narrow single column — and Sonata accommodates applications up to CAD/enterprise complexity without an artificial simplicity ceiling. Workspaces are an official concept for persistent/temporary working contexts. See [Navigation](system/navigation.md).
- Table, List, Inspector, Master-Detail and Split View are first-class, official Data Display components — a table is not a lesser citizen of the catalog. Data density coordinates with the global density system, common configuration changes should be reversible, dense interfaces use restrained expression, and active/current information generally takes spatial priority over historical information. Data-display configuration may live in Workspaces. See [Data Display](system/data-display.md).
- Selection is a first-class semantic state of the underlying data/object model (single/multi/range/select-all/toggle), distinct from focus/hover/active/checked/highlighted, and shareable across views (Table/List/Inspector) rather than owned independently by each. Meaningful multi-selection exposes a summary and contextual bulk actions, integrates with undo where reversible, and may persist across filtering/sorting/pagination with scope kept clear. Spreadsheet-like row/cell selection and Selection Mode (including a mobile long-press variant) are official patterns; selection must never depend solely on color. See [Selection](system/selection.md).
- Feedback is a first-class system covering Inline Message/Toast/Snackbar/Banner/Alert/Progress/Status/Empty State/Notification/Notification Center. Feedback presentation is proportional to severity/urgency/persistence/context; reversible operations strongly favor Undo; errors communicate what happened, consequence and next action; long-running work stays non-blocking where safe; and feedback avoids unnecessary layout displacement or notification spam for an unchanged condition. Haptics for feedback follow the general haptics rule (D-028) rather than a separate one. See [Feedback](system/feedback.md).
- Composition generalizes space-as-a-resource (D-056) into an official model: a Content Space may hold multiple coordinated Regions/Panes/Panels without becoming separate navigation destinations. Sonata prefers simultaneous presentation when it materially helps, but explicitly discourages fragmenting a Content Space into regions with no meaningful relationship. Regions may expand, be resized, collapsed or floated, with layout preferences persisted in Workspaces; changing a region's content is not navigation. Desktop and Mobile compose the same semantic relationships spatially differently. See [Composition](system/composition.md).
- Application Shell defines the outer framework — native window chrome (used rather than duplicated), an optional compact header, navigation, tool areas, Content Space, status and overlays — within which Composition and Workspace operate. Toolbar is compositional (not inherently horizontal) with distinguishable application/view/selection/tool scopes. Multiple windows and multi-monitor workflows are official capabilities; Workspace (window's working context), Window (its presentation container) and Document/View (content within it) are distinct concepts. Mobile substantially reduces persistent shell chrome while keeping the same semantic relationships. See [Application Shell](system/application-shell.md).
- Disclosure (Accordion, Collapsible, Expandable Row, Menu, Context Menu, progressive disclosure) reveals or collapses content within the current semantic context — distinct from navigation, which changes context. Progressive disclosure manages complexity without an excuse to arbitrarily hide needed functionality; nested disclosure and menu chains are discouraged past a reasonable contextual limit; hover- and touch-only disclosure must have an accessible equivalent; and disclosure state may be persisted in Workspaces. Sonata's existing complexity-accommodation stance (D-057) already covers why complexity-rich professional software is a valid target — Disclosure applies it rather than re-deciding it. See [Disclosure](system/disclosure.md).

See [Decision Log](governance/decision-log.md) for the full, numbered (D-001…) record.

## Next working area

**Spacing & Density**, including (values should be defined as Axis-B spec defaults per the [resolution model](system/resolution-model.md)):

- base spacing rhythm
- semantic spacing tokens
- density levels
- relation between density and interface scale
- desktop/mobile density behavior
- touch constraints
- user customization
- adaptive transformations

## Deliberately open

- Exact numeric token scales.
- Exact color generation algorithm; curated Sonata palette and neutral defaults.
- Exact typography scale and variable-font strategy; final default typeface within the Red Hat + Noto architecture.
- Exact shape/radius values and organic geometry rules.
- Surface/translucency tiers and blur/backdrop rules.
- Motion durations, easing and spring strategy.
- Exact icon grid, stroke weight, default rendering style and size scale (no icon family is mandated — see D-030).
- Final component inventory and exact cross-platform APIs (catalog architecture decided — D-031–D-036).
- Platform convention boundary (Web / Qt / GTK).

See [Open Questions](governance/open-questions.md) for the full breakdown by domain (architecture, localization, input, content, theming, configuration UX, navigation, motion, component governance).

---

# Working method

Each new subject should be documented in four parts where applicable:

1. **Inherited principles** — what comes from GNOME, Radix, or Material.
2. **Sonata decisions** — what Sonata changes or establishes itself.
3. **Customization** — what the product/user may change.
4. **Open questions** — unresolved decisions that should not be silently assumed.

New decisions should be added to [`governance/decision-log.md`](governance/decision-log.md). Deliberately deferred decisions should be added to [`governance/open-questions.md`](governance/open-questions.md) rather than silently assumed.
