# Sonata
## Design Language Specification

**Status:** Consolidated Working Draft 0.4

Sonata is a bespoke adaptive design language for desktop and mobile-class software. It combines complementary sources without treating them as a single visual system.

> **Structure determines where. Expression determines how strongly.**

## Architecture

```text
FOUNDATION
  GNOME HIG
      ↓
SYSTEM
  Radix-inspired
      ↓
EXPRESSION
  Material-inspired
      ↓
PATTERNS
  Sonata-native
      ↓
ADAPTIVE
  Mobile / Adaptive / Desktop
      ↓
CUSTOMIZATION
  Token-driven user control
```

## Authority hierarchy

1. Accessibility and platform accessibility requirements
2. Foundation / GNOME HIG
3. Sonata semantic rules
4. System / Radix-inspired implementation
5. Expression / Material-inspired techniques
6. Component defaults

The hierarchy concerns decision authority, not visual imitation.

## Table of Contents

### 00. Governance
- [Principles](governance/principles.md)
- [Decision Log](governance/decision-log.md)
- [Authority Matrix](governance/authority-matrix.md)
- [Open Questions](governance/open-questions.md)
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
- [Tokens](system/tokens.md)
- [Surfaces & Overlays](system/surfaces.md)
- [Theming](system/theming.md)

### 03. Expression
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
- [Power User](patterns/power-user.md)

### 06. Customization
- [Overview](customization/overview.md)
- [Color](customization/color.md)
- [Typography](customization/typography.md)
- [Density](customization/density.md)
- [Accessibility](customization/accessibility.md)

### 07. Implementation
- [Platform](implementation/platform.md)
- [Tokens](implementation/tokens.md)
- [Validation](implementation/validation.md)
- [Sonata Skill](implementation/skill.md)

### 08. References
- [Reference index](references/README.md)
- [GNOME](references/gnome.md)
- [Radix](references/radix.md)
- [Material](references/material.md)
- [Material Expressive](references/material-expressive.md)
- [Typography](references/typography.md)

## Document status model

Each module may contain:

- **Decided** — normative Sonata rule.
- **Recommended** — strong default, but replaceable.
- **Open** — design decision not yet frozen.
- **Reference** — borrowed idea that informs Sonata but is not itself binding.
