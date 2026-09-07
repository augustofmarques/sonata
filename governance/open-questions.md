# Sonata Open Questions

These are unresolved design/implementation decisions. They are not missing documentation; they are intentionally open.

## Highest priority

- Exact hybrid color generation algorithm.
- Curated Sonata palette and neutral defaults.
- Exact typography scale and variable-font strategy.
- Exact spacing scale and density transforms.
- Exact shape/radius values and organic geometry rules.
- Surface/translucency tiers and blur rules.
- Motion durations, easing and spring strategy.
- Default icon family.
- Exact component inventory and cross-platform APIs.
- Platform convention boundary.

## Color
- Exact hybrid Radix-scale / Material-tonal generation model.
- Curated Sonata palette.
- Neutral palette defaults.
- Secondary/tertiary generation rules.
- Semantic color mapping rules.
- Dynamic/image-derived color.

## Typography
- Final default typeface recommendation within the Red Hat + Noto architecture.
- Exact type scale.
- Variable-font strategy.
- Numeric typography defaults.
- Detailed locale/script fallback table.

## Shape
- Exact radius values.
- Relationship between component shape tokens and global shape profiles.
- Formal definition of organic geometry.
- How shape profiles affect different components.

## Surface
- Exact translucency tiers.
- Blur/backdrop rules.
- Elevation/depth mapping per light/dark mode.
- Reduced-transparency behavior.
- Whether glass is ever the default for specific platform classes.

## Spacing & Density
- Exact base spacing scale.
- Density profiles and their transform tables.
- Interface-scale relationship.
- Mobile density constraints.
- Touch-target invariants.
- Whether users can separately control spacing and density or whether one control maps both.

## Motion
- Exact durations and easing.
- Spring model, if any.
- Motion hierarchy.
- Reduced-motion transformation rules.
- Platform-specific motion adaptation.
- Exact morphing constraints (which state transitions qualify, how far shape may deviate mid-transition).

## Iconography
- Default icon family.
- Stroke/fill strategy.
- Optical sizing.
- Icon customization.

## Components
- Final component inventory.
- Component APIs.
- Compound component patterns.
- Cross-platform implementation strategy.

## Cross-cutting / Architecture
- Exact boundary between Sonata conventions and native platform conventions.
- Which platform conventions may override Sonata, and under what conditions.
- What must remain invariant across Web, Qt, GTK and mobile implementations.
- ~~Full token precedence model.~~ Resolved by D-024 / `system/resolution-model.md` (three-axis model: Abstraction, Precedence, State). Remaining sub-questions:
  - Exact conflict rule when an application theme marks a token non-overridable but user customization still targets it.
  - Which domains beyond color need a documented Axis-B generation algorithm (shape, motion, spacing are candidates).
  - Whether Axis C state variants are independently themeable tokens or fixed transforms of the Axis B result.
  - How accessibility constraints (Axis B) interact with state transitions (Axis C) — e.g. is a "pressed" motion variant removed under reduced motion, or replaced with a static equivalent?
- Public vs private tokens.
- Product-specific token extension rules.
- Custom-theme validation criteria.

## Localization & Internationalization
- RTL mirroring policy and intentional asymmetries.
- Locale-aware typography and script fallback strategy.
- Locale-aware number, date, time and currency formatting.
- Text expansion/contraction rules.
- Scripts requiring dedicated display/type treatment.
- Locale-specific writing guidance while retaining shared semantic principles.

## Input & Interaction
- Guarantees for keyboard, pointer, touch, pen and assistive technology.
- Haptic feedback on mobile.
- Context-menu/right-click conventions.
- Drag-and-drop and touch equivalents.
- Gesture support boundaries.
- Focus vs selection semantics.

## Content & Data
- Dates, times, numbers, currencies, units and identifiers.
- Table/list conventions.
- Truncation, wrapping, ellipsis and overflow.
- Long-form content and line lengths.
- Empty/loading/error/success/partial states.

## Theming & Product Identity
- Product palette extension rules.
- Brand-to-semantic mapping.
- New semantic color roles.
- User vs application presets.
- Theme import/export.
- Scope of preferences across apps/devices/accounts.

## Configuration UX
- Where customization settings live.
- Immediate vs deferred application of changes.
- Temporary app overrides.
- Customization in immersive/hero contexts.

## Information & Navigation Patterns
- Navigation taxonomy across Mobile/Desktop.
- Relationship between search and command palette retrieval.
- Global vs contextual search.
- Shortcut discovery/remapping.
- Back behavior.
- Workspace/window behavior.

## Motion & Feedback
- Sound/audio feedback.
- Haptic vocabulary and platform-strength mapping (haptics-as-a-modality is decided, D-028; the vocabulary itself — e.g. a candidate `selection / activation / success / warning / error / boundary / completion` taxonomy mapped to platform haptic strengths — is not).
- Feedback intensity.
- Notification interruption levels.

## Component Governance
- Naming conventions.
- Versioning strategy.
- Deprecation policy.
- Product-specific extensions.
- Criteria for promoting patterns to Sonata-wide status.
