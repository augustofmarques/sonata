# Sonata Authority Matrix

This matrix defines which layer has decision authority.

| Domain | Primary authority | Secondary reference | Notes |
|---|---|---|---|
| Information architecture | GNOME HIG | Sonata | Structure first |
| Page layout | GNOME HIG | Sonata | Expression may change salience, not structural intent |
| Navigation | GNOME HIG | Sonata System + Patterns | Platform adaptation may alter presentation; component catalog decided (D-054–D-064) |
| Writing style | GNOME HIG | Sonata | Applies to UI copy and content patterns |
| Accessibility semantics | GNOME HIG + platform requirements | Radix | Accessibility has final authority |
| Keyboard/focus behavior | GNOME HIG + platform requirements | Radix | Platform conventions can affect implementation |
| Primitive behavior | Radix-inspired | Platform | Sonata semantics remain authoritative |
| Component architecture | Radix-inspired + Sonata | Platform | Use composable primitives |
| Actions | Sonata System | GNOME HIG | Role hierarchy and safeguards decided (D-037–D-041); Foundation governs when/why an action appears |
| Inputs | Sonata System | GNOME HIG | Semantic input taxonomy, validation and forms decided (D-042–D-053) |
| Data Display | Sonata System | GNOME HIG | Table/List/Inspector/Master-Detail/Split View decided (D-065–D-077) |
| Selection | Sonata System | GNOME HIG | Selection is data/object-model state, not component-owned styling (D-068, D-078–D-088) |
| Feedback | Sonata System | GNOME HIG + Foundation writing | Feedback taxonomy and proportionality decided (D-089–D-107); message copy follows Foundation writing (D-013) |
| Token architecture | Sonata | Radix | Sonata owns semantic token contract |
| Color generation | Sonata | Radix + Material | Hybrid model |
| Typography architecture | Sonata | Red Hat + Material + Radix | Family replaceable |
| Shape | Sonata | Radix + Material | Rounded/organic allowed |
| Surface/depth | Sonata | Radix + Material | Translucency contextual |
| Spacing | Sonata | Radix | Shared rhythm, adaptable density |
| Density | Sonata | Radix | Compositional property |
| Motion | Sonata | Material | Accessibility overrides |
| Visual emphasis | Sonata | Material | Structure determines placement |
| Hero composition | Sonata | Material Expressive | Optional composition mode |
| Iconography | Sonata | Radix / other families | No family mandated by design (D-030); grid/stroke/rendering defaults open |
| Search | Sonata Pattern | GNOME / platform | Optional by app complexity |
| Command palette | Sonata Pattern | Platform | Power-user affordance |
| Shortcuts | Sonata Pattern + platform | GNOME | Must remain discoverable |
| Desktop composition | Sonata Adaptive | GNOME HIG | Desktop class |
| Mobile composition | Sonata Adaptive | GNOME HIG | Mobile class |
| RTL | GNOME HIG + locale/platform | Sonata | Layout may mirror selectively |
| User customization | Sonata | Radix + Material | Capability is global, exposure contextual |
| Product branding | Application | Sonata | Must map into semantic roles |
| Platform-native conventions | Platform implementation | Sonata | May adapt presentation without violating semantic intent |

## Conflict rule

When two sources disagree, identify the type of decision first. Structural and semantic questions are resolved by Foundation; implementation questions by System; expression questions by Sonata Expression. Accessibility requirements can override any visual preference.

## Reference authority model

External sources may participate in Sonata at different authority levels (D-192).

### Normative

Sonata explicitly adopts the rule. The rule becomes part of Sonata's own specification.

### Foundational

The source provides a foundational conceptual or structural model that Sonata explicitly builds upon.

### Reference

The source provides design guidance or inspiration that Sonata may adapt.

### Implementation Reference

The source is consulted for implementation techniques without becoming a Sonata design rule.

### Reference disposition

Every important external influence should be classified as one of:

- Adopted
- Adapted
- Reference-only
- Rejected

The disposition should explain the problem or design goal that motivated the decision.

### Current reference roles

**GNOME HIG** — Normative/Foundational for structure, layout, navigation, interaction, accessibility, writing and content.

**Radix** — System and Implementation Reference for primitives, components, states, tokens, theming and accessible interaction infrastructure.

**Material 3 Expressive** — Reference (primary Expression reference, D-172) for color, typography, shape, motion, animation, emphasis, hero composition and expressive interaction. See [`../references/material-expressive.md`](../references/material-expressive.md).

**Apple Human Interface Guidelines** — Reference (secondary, D-173) for adaptive composition, platform-aware interaction, sidebars, toolbars, material surfaces, floating UI, window/application composition and visual polish. See [`../references/apple-hig.md`](../references/apple-hig.md).

**Red Hat Typography** — Implementation Reference for the recommended UI/text family architecture, display typography, monospace and multilingual fallback.

This section classifies reference *sources*; the table above classifies decision authority per *domain*. The two are complementary — a domain's authority may draw on a Normative, Foundational or Reference-level source depending on the question being asked.
