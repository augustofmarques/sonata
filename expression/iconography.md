# Expression — Iconography

## Status

Decided: authority and contract. Open: exact grid, stroke weight, rendering default and size scale (see Open questions).

Iconography is an independent Sonata subsystem: Sonata specifies the language icons must speak, not the alphabet they come from.

## Authority

Sonata defines the iconography contract. No icon family is mandatory.

Compatible sources may include:

- Radix Icons
- Lucide
- Phosphor
- native platform iconography
- custom product iconography

provided they satisfy the Sonata contract below. See [`../references/radix.md`](../references/radix.md) for Radix Icons specifically as an optional, non-normative reference.

## Sonata decisions — the iconography contract

Any icon family adopted by a Sonata product must satisfy:

### Geometry

- coherent proportions
- consistent optical weight
- predictable alignment
- internally consistent grid

### Rendering

- outline, filled or mixed systems are allowed
- the chosen family must remain internally coherent (no mixing rendering strategies within one family unless the family itself defines that as a coherent variant)

### Scale

Icons are used at named scales, not arbitrary sizes:

- inline — within text or dense lists
- control — buttons, form controls
- toolbar — header bars, action bars
- navigation — sidebars, tab/view switchers
- feature / hero — empty states, onboarding, major status

### Semantics

- icon alone only when meaning is sufficiently obvious
- critical or ambiguous actions should retain textual/contextual support

### States

Icons participate in the same interaction states as the controls that host them:

- default
- hover
- focus
- pressed
- selected
- disabled
- status variants where meaningful

### Accessibility

- icons must have appropriate accessible names/semantics
- purely decorative icons must be distinguishable from semantic icons

## Desktop/Mobile adaptation

Desktop may favor compact iconography; mobile may favor larger icons and more explicit icon-plus-label combinations. This follows the general Adaptive Class guidance ([`../adaptive/`](../adaptive/)) rather than a separate iconography rule.

## Customization

Icon family selection is a product/theme-level decision, not a per-user runtime preference at this stage. There is currently no `customization/iconography.md` counterpart (see [D-025](../governance/decision-log.md#d-025--expressioncustomization-split-of-authorship)); if icon weight or rendering style becomes user-facing, that surface should be added there rather than here.

## Open questions

The following remain deliberately unresolved (see [`../governance/open-questions.md`](../governance/open-questions.md)):

- exact grid (e.g. whether 24×24 is required)
- exact stroke weight (e.g. whether 1.5px is required)
- whether outline is the required default rendering
- a recommended default family
- an exact size scale for the named categories above
