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
