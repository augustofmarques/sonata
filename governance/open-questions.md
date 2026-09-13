# Sonata Open Questions

These are unresolved design/implementation decisions. They are not missing documentation; they are intentionally open.

## Highest priority

- Exact hybrid color generation algorithm.
- Curated Sonata palette and neutral defaults.
- Exact typography scale and variable-font strategy.
- ~~Exact spacing scale~~ Resolved by D-205 (v1 candidate baseline). Density transform tables per profile remain open.
- Exact shape/radius values per personality; organic geometry formal definition remains open.
- Surface/translucency tiers and blur rules.
- Motion durations, easing and spring strategy.
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
- Exact radius values per shape token and personality.
- Formal definition of organic geometry.
- Shape transition/morphing mappings.

## Surface
- Exact translucency tiers.
- Blur/backdrop rules.
- Elevation/depth mapping per light/dark mode.
- Reduced-transparency behavior.
- Whether glass is ever the default for specific platform classes.

## Spacing & Density
- ~~Exact base spacing scale.~~ Resolved by D-205 (v1 candidate baseline: 0/2/4/6/8/12/16/20/24/32/40/48/64/80/96).
- ~~Density profiles.~~ Resolved by D-206/D-207/D-208 (Comfortable/Balanced/Compact/Dense, Balanced default, per-class availability). Exact per-profile transform tables remain open.
- Interface-scale relationship.
- Mobile density constraints.
- Touch-target invariants.
- Tablet/Adaptive Dense-availability heuristics (window size, modality, complexity thresholds).
- Whether users can separately control spacing and density or whether one control maps both.

## Motion
- Exact durations and easing.
- Spring model, if any.
- Motion hierarchy.
- Reduced-motion transformation rules.
- Platform-specific motion adaptation.
- Exact morphing constraints (which state transitions qualify, how far shape may deviate mid-transition).

## Iconography
- Exact grid (e.g. whether 24×24 is required).
- Exact stroke weight (e.g. whether 1.5px is required).
- Whether outline is the required default rendering.
- A recommended default family.
- Exact size scale for the named categories (inline/control/toolbar/navigation/feature-hero).
- Icon customization (whether weight/rendering ever becomes user-facing).

## Components
- Final component inventory.
- Component APIs.
- Compound component patterns.
- Cross-platform implementation strategy.

## State

- Exact state-token naming conventions.
- State serialization boundaries.
- Session persistence policy.
- Workspace-state schema.
- Optimistic-state timeout/reconciliation patterns.
- Conflict-resolution UI patterns.
- Operation cancellation semantics.
- Operation history retention.
- Cross-view state synchronization implementation.
- Platform accessibility mappings.

## Actions
- Exact Button token dimensions.
- Exact size scale.
- Exact emphasis mappings.
- Link behavior and relationship to Button.
- Exact confirmation thresholds for destructive actions.
- Shortcut display conventions.
- Menu Button anatomy.
- Split Button anatomy.
- Toggle vs Switch distinction.
- Action-group layout rules.

## Inputs
- Exact field anatomy.
- Label/help/error placement.
- Inline vs block validation presentation.
- Floating labels or no floating labels.
- Field sizing.
- Exact input tokens.
- Select anatomy.
- Combobox interaction.
- Autocomplete result presentation.
- Mobile keyboard behavior.
- Date/time input strategy.
- File-upload patterns.
- Exact form-layout patterns.

## Data Display
- Exact Table anatomy.
- Column-resize interaction.
- Column customization UI.
- Pinning behavior.
- Grouping presentation.
- Row/cell editing behavior.
- Inspector anatomy and transition behavior.
- Split View collapse rules.
- Exact mobile transformations.
- Virtualization integration.
- Pagination controls.
- Filter-builder complexity.
- Timeline anatomy.

## Composition

- Exact pane minimum/maximum dimensions.
- Resize handle behavior.
- Collapse/expand controls.
- Region reordering mechanics.
- Expansion/restoration behavior.
- Floating-region anchoring.
- Mobile transformation rules.
- Workspace serialization of layout.

## Containers

- Exact Container anatomy.
- Exact Grid API.
- Exact Stack API.
- Minimum indentation unit.
- Tree/list indentation behavior.
- Full-bleed containment rules.
- Sticky-region constraints.
- Container alignment APIs.
- Tablet-specific composition heuristics.

## Application Shell

- Exact compact-header anatomy.
- Native chrome integration per platform.
- Toolbar overflow behavior.
- Toolbar customization UI.
- Multiple-window/workspace relationship.
- Multi-monitor restore policy.
- Exact docking model.
- Shell layout persistence format.
- Fullscreen transition behavior.

## Overlays

- Exact Popover sizing rules.
- Exact Tooltip timing/placement.
- Exact Dialog size classes.
- Sheet vs Drawer terminology.
- Floating Panel docking model.
- Overlay promotion interaction.
- Full-screen overlay thresholds.
- Overlay stacking/z-order implementation.
- Accessibility announcement behavior.
- Platform-specific dismissal mappings.

## Disclosure

- Exact Accordion anatomy.
- Single-open vs multiple-open defaults.
- Exact nesting heuristics.
- Expandable-row height behavior.
- Menu overflow rules.
- Submenu presentation.
- Context-menu touch equivalent.
- Disclosure animation timings.
- Workspace persistence details.

## Navigation
- Exact sidebar anatomy.
- Exact navigation rail anatomy.
- Maximum recommended visible mobile destinations.
- Exact breakpoint behavior.
- Navigation animation details.

## Selection

- Exact selected-row treatment.
- Exact cell-selection behavior.
- Selection summary placement.
- Selection-mode transition.
- Selection action bar anatomy.
- Cross-page selection model.
- Select-all scope communication.
- Exact keyboard mappings per platform.

## OOBE & Onboarding

- Exact OOBE flow anatomy.
- Replay/help re-entry UI.
- Contextual-onboarding trigger rules.
- Personalization step count/order within OOBE.

## Cross-cutting / Architecture
- Exact boundary between Sonata conventions and native platform conventions.
- Which platform conventions may override Sonata, and under what conditions.
- What must remain invariant across Web, Qt, GTK and mobile implementations.
- ~~Full token precedence model.~~ Resolved by D-024 / `system/resolution-model.md` (three-axis model: Abstraction, Precedence, State). Remaining sub-questions:
  - Exact conflict rule when an application theme marks a token non-overridable but user customization still targets it.
  - Which domains beyond color need a documented Axis-B generation algorithm (shape, motion, spacing are candidates).
  - How accessibility constraints (Axis B) interact with state transitions (Axis C) — e.g. is a "pressed" motion variant removed under reduced motion, or replaced with a static equivalent?
- ~~Whether Axis C state variants are independently themeable tokens or fixed transforms of the Axis B result.~~ Resolved by D-197: they are independently themeable state tokens.
- ~~Public vs private tokens.~~ Resolved by the Stable/Controlled/Internal API tiers in `system/tokens.md`.
- ~~Product-specific token extension rules.~~ Resolved by D-195 (namespaced application tokens).
- Custom-theme validation criteria.
- Exact Apple-derived patterns Sonata will adopt.
- Which Apple material behaviors belong in Sonata's Surface implementation.
- Exact Material 3 Expressive principles to encode.
- Whether Sonata defines a formal "Expressiveness" token affecting multiple visual dimensions simultaneously.

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
- Drag-and-drop and touch equivalents.
- Gesture support boundaries.

## Content & Data
- Dates, times, numbers, currencies, units and identifiers.
- Truncation, wrapping, ellipsis and overflow.
- Long-form content and line lengths.
- Empty/loading/error/success/partial states.

## Theming & Product Identity
- Product palette extension rules.
- Brand-to-semantic mapping.
- New semantic color roles.
- User vs application presets (D-196 decides Theme/Preference/Preset as distinct concepts and that applications may ship curated presets; whether users can save their own custom presets remains open).
- Theme import/export.
- Scope of preferences across apps/devices/accounts.

## Configuration UX
- Where customization settings live.
- Immediate vs deferred application of changes.
- Temporary app overrides.
- Customization in immersive/hero contexts.

## Information & Navigation Patterns
- Shortcut discovery/remapping.
- Exact platform back-navigation conventions to follow per platform.

## Motion & Haptics
- Sound/audio feedback.
- Haptic vocabulary and platform-strength mapping (haptics-as-a-modality is decided, D-028; the vocabulary itself — e.g. a candidate `selection / activation / success / warning / error / boundary / completion` taxonomy mapped to platform haptic strengths — is not).

## Feedback

- Exact severity taxonomy.
- Toast vs Snackbar terminology.
- Exact Toast/Snackbar placement.
- Notification Center anatomy.
- Notification grouping mechanics.
- Exact live-region/announcement behavior.
- Progress component anatomy.
- ETA formatting.
- Exact alert interruption thresholds.
- Feedback stacking rules.
- Mobile/desktop presentation mappings.

## Component Governance
- Naming conventions.
- Versioning strategy.
- Deprecation policy.
- Product-specific extensions.
- Criteria for promoting patterns to Sonata-wide status.
