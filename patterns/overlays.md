# Pattern — Overlays

The normative model — overlay taxonomy, modal scope, promotion to persistent UI, nesting restraint — is defined in [`../system/overlays.md`](../system/overlays.md) (D-141–D-155).

## Choose Popover when

The user needs short contextual interaction without leaving the current context.

## Choose Tooltip when

Supplementary explanation is useful but not required for task completion.

## Choose Dialog when

A focused decision or temporary isolated task is appropriate.

## Choose Sheet/Drawer when

The user needs more space than a Popover but should remain within the same broader context.

## Choose Floating Panel when

A tool or contextual surface benefits from independent positioning or persistence.

## Choose persistent Region when

The user repeatedly interacts with the surface or needs simultaneous access for sustained work.

## Promotion

Applications may offer to convert a repeatedly used overlay into persistent workspace UI.

Example:

```text
Temporary panel
    ↓
repeated use
    ↓
"Keep this panel?"
    ↓
persistent workspace region
```

## Avoid overlay chains

Do not place an overlay inside another overlay as a general navigation mechanism.

When complexity grows, change the composition.

## Preserve context

Closing an overlay should return the user to the same logical context and focus where possible.
