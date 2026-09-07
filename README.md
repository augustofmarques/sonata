# Sonata
## Design Language Specification

**Status:** Working Draft 0.3  
**Purpose:** Master index and navigation for the Sonata design language.

Sonata is a bespoke adaptive design language composed from complementary foundations:

- **Foundation — GNOME HIG:** structure, information architecture, interaction, accessibility, writing, and content principles.
- **System — Radix-inspired:** primitives, components, states, tokens, surfaces, theming, and reusable construction mechanisms.
- **Expression — Material-inspired:** color, typography, shape, motion, animation, visual emphasis, and hero composition.
- **Patterns — Sonata-native:** search, command palette, shortcuts, filtering, and power-user workflows.
- **Adaptive — Sonata:** mobile, adaptive, and desktop classes.
- **Customization — Sonata:** user-controlled visual and accessibility preferences.

## Core principle

> **Structure determines where. Expression determines how strongly.**

## Authority hierarchy

1. Accessibility and platform accessibility requirements
2. Foundation / GNOME HIG
3. Sonata semantic rules
4. System / Radix-inspired implementation
5. Expression / Material-inspired techniques
6. Component defaults

The hierarchy is about decision authority, not visual imitation.

---

# Table of Contents

## 00. Governance

- [Principles](governance/principles.md)
- [Decision Log](governance/decision-log.md)
- [Open Questions](governance/open-questions.md)

## 01. Foundation — GNOME HIG

- [Foundation Overview](foundation/overview.md)
- [Layout & Information Architecture](foundation/layout.md)
- [Interaction & Navigation](foundation/interaction.md)
- [Accessibility](foundation/accessibility.md)
- [Writing & Content](foundation/writing.md)

## 02. System — Radix-inspired

- [System Overview](system/overview.md)
- [Primitives](system/primitives.md)
- [Components & States](system/components.md)
- [Tokens](system/tokens.md)
- [Surfaces & Overlays](system/surfaces.md)
- [Theming](system/theming.md)

## 03. Expression — Material-inspired

- [Expression Overview](expression/overview.md)
- [Color](expression/color.md)
- [Typography](expression/typography.md)
- [Shape & Geometry](expression/shape.md)
- [Surface & Depth](expression/surface-depth.md)
- [Spacing & Density](expression/spacing-density.md)
- [Motion & Animation](expression/motion.md)
- [Visual Emphasis & Hero](expression/emphasis.md)
- [Iconography](expression/iconography.md)

## 04. Adaptive

- [Adaptive Overview](adaptive/overview.md)
- [Mobile Class](adaptive/mobile.md)
- [Adaptive Class](adaptive/adaptive.md)
- [Desktop Class](adaptive/desktop.md)
- [Input Modality](adaptive/input-modality.md)

## 05. Patterns

- [Patterns Overview](patterns/overview.md)
- [Search](patterns/search.md)
- [Command Palette](patterns/command-palette.md)
- [Shortcuts](patterns/shortcuts.md)
- [Filtering & Bulk Actions](patterns/filtering.md)
- [Power-user Workflows](patterns/power-user.md)

## 06. Customization

- [Customization Overview](customization/overview.md)
- [Theme & Color](customization/color.md)
- [Typography](customization/typography.md)
- [Spacing & Density](customization/spacing-density.md)
- [Shape & Surface](customization/shape-surface.md)
- [Motion & Accessibility](customization/motion-accessibility.md)

## 07. Components & Patterns

This section will contain the normative component specifications after the foundations and token system are sufficiently stable.

- Component architecture
- Buttons
- Inputs
- Navigation
- Lists
- Tables
- Dialogs
- Menus
- Sheets
- Cards
- Toolbars
- Notifications
- Data visualization
- Empty states
- Error states
- Loading states

## 08. Implementation

Future modules for platform-specific translations:

- Web
- Qt
- GTK
- Other platform implementations

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
             filtering · power workflows
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

- Three-layer architecture: Foundation / System / Expression.
- GNOME HIG remains authoritative for structure and behavior.
- GNOME writing/content principles are explicitly retained.
- Radix is primarily a construction and token foundation, not the visual identity.
- Material is primarily an expressive reference, not a component mandate.
- Desktop Class and Mobile Class are distinct interaction compositions.
- Adaptive Class bridges them.
- User customization is first-class and token-driven.
- Accent color is highly customizable.
- Curated color palette + advanced arbitrary accent color.
- Neutral palette may also be customized.
- Semantic success/warning/danger/info roles are protected.
- Typography is system-level, not locked to one font family.
- Recommended default typography: Red Hat Display / Text / Mono, with multilingual fallback strategy, while remaining replaceable.
- Mono is explicitly supported for code and technical content.
- Numeric typography is a distinct semantic concern.
- Shape is customizable and may range from subtle to expressive/organic.
- Translucent surfaces are supported but glassmorphism is not mandatory.
- Density is a first-class user preference, not merely smaller padding.
- Search, command palettes, shortcuts, and other advanced workflows are Sonata patterns, not universal requirements.
- Primary actions may receive substantially higher visual salience when justified.

## Next working area

**Spacing & Density**, including:

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
- Exact color generation algorithm.
- Exact default neutral and accent palette.
- Final default font recommendation beyond the Red Hat family proposal.
- Exact shape values and organic geometry rules.
- Surface/blur/transparency thresholds.
- Motion curves and durations.
- Icon family.
- Final component inventory and APIs.
- Platform implementation details.

---

# Working method

Each new subject should be documented in four parts where applicable:

1. **Inherited principles** — what comes from GNOME, Radix, or Material.
2. **Sonata decisions** — what Sonata changes or establishes itself.
3. **Customization** — what the product/user may change.
4. **Open questions** — unresolved decisions that should not be silently assumed.

New decisions should be added to `governance/decision-log.md`.
