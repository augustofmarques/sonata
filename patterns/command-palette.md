# Pattern — Command Palette

Command palette is an optional Sonata power-user pattern.

It may expose:

- actions
- navigation
- entities
- documents
- settings
- commands
- shortcuts

It complements ordinary discoverability and does not replace normal navigation or visible actions (D-062). A user should be able to use the application indefinitely without knowing that a command palette exists — see [Navigation](../system/navigation.md).

## Global command/search surface restraint

Global command or search surfaces are scarce application-level interaction infrastructure, not a component to add freely (D-043).

A typical application should expose zero or one global command/search surface. A second global surface is exceptional and must have a clearly distinct context or purpose.

This constraint does not apply to ordinary text fields or contextual search fields. Multiple text fields may use the same underlying input infrastructure (see [`../system/inputs.md`](../system/inputs.md)) without becoming multiple command palettes.
