# Pattern — Disclosure

Disclosure is used to control the visibility of related information or functionality without changing semantic context. The normative model — Accordion/Collapsible/Expandable Row/Menu/Context Menu, depth restraint, hover/touch accessibility — is defined in [`../system/disclosure.md`](../system/disclosure.md) (D-130–D-140).

## Choose disclosure when

Use disclosure when the user remains in the same Content Space and the hidden content is related to what is already visible.

## Choose simultaneous presentation when

Keep information visible when:

- comparison is important
- repeated access is expected
- context would otherwise be lost
- available space supports simultaneous work

## Choose Inspector when

Use an Inspector when contextual information or editing needs more space or persistent interaction than local expansion can provide.

## Choose Navigation when

Navigate when the content represents a distinct destination or semantic context.

## Avoid disclosure chains

Prefer composition, workspace organization or direct access over deep nesting.

## Workspace relationship

Expansion/collapse settings may be persisted in Workspace state when useful.

## Mobile

Mobile may progressively disclose more information to preserve readability and touch usability.

## Desktop

Desktop may keep more information simultaneously visible when this materially improves efficiency.
