# Radix Reference

**Role in Sonata:** System and implementation reference.

Radix Primitives describes itself as an open-source, low-level UI component library for building accessible design systems and web apps. Its primitives are intentionally unstyled and designed to be used as the base layer of a design system or adopted incrementally. It also handles difficult accessibility concerns such as ARIA attributes, focus management and keyboard navigation. [Radix Primitives](https://www.radix-ui.com/primitives/docs/overview/introduction) [Accessibility](https://www.radix-ui.com/primitives/docs/overview/accessibility)

Sonata adopts the following ideas:

- composable low-level primitives
- explicit separation between semantics and styling
- accessibility-aware interaction infrastructure
- tokenized theming
- customization without rewriting component semantics
- ability to create a product-specific component API above primitives

Sonata does not adopt Radix's default visual styling as a required identity.

Radix Themes is also a reference for token architecture. Current Themes documentation exposes semantic configuration for accent color, radius, scaling and panel background/translucency, and supports remapping theme tokens. [Radix Themes](https://www.radix-ui.com/themes/docs/components/theme) [Color](https://www.radix-ui.com/themes/docs/theme/color)
