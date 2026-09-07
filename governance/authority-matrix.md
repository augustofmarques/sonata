# Sonata Authority Matrix

This matrix defines which layer has decision authority.

| Domain | Primary authority | Secondary reference | Notes |
|---|---|---|---|
| Information architecture | GNOME HIG | Sonata | Structure first |
| Page layout | GNOME HIG | Sonata | Expression may change salience, not structural intent |
| Navigation | GNOME HIG | Sonata Patterns | Platform adaptation may alter presentation |
| Writing style | GNOME HIG | Sonata | Applies to UI copy and content patterns |
| Accessibility semantics | GNOME HIG + platform requirements | Radix | Accessibility has final authority |
| Keyboard/focus behavior | GNOME HIG + platform requirements | Radix | Platform conventions can affect implementation |
| Primitive behavior | Radix-inspired | Platform | Sonata semantics remain authoritative |
| Component architecture | Radix-inspired + Sonata | Platform | Use composable primitives |
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
| Iconography | Sonata | Radix / other families | Family remains open |
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
