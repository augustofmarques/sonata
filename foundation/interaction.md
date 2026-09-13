# Foundation — Interaction & Navigation

Interaction and navigation follow the existing GNOME HIG skill.

Sonata preserves semantic roles and platform-appropriate behavior while permitting its System and Expression layers to alter implementation and appearance.

## Input modalities

Support where applicable:

- pointer
- touch
- keyboard
- pen
- assistive technology

No critical function should rely solely on a single modality when an equivalent accessible path is appropriate.

## Advanced interaction patterns

Search, command palettes, shortcuts, filtering, bulk actions and other power-user capabilities are supported as optional Sonata patterns. They should be introduced when the application workflow justifies them rather than being mandatory features.

## State and interaction

Interaction should be understood through semantic state rather than purely visual changes. The normative state model is defined in [`../system/state.md`](../system/state.md) (D-175–D-191).

The implementation should distinguish:

- focus
- hover
- selection
- activation
- editing
- expansion
- availability
- persistence
- operation state

State changes should remain understandable even when visual effects such as motion or color are reduced.
