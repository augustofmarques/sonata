# Pattern — Composition

Composition patterns describe meaningful spatial relationships between regions of a Content Space. The normative semantic model — Content Space, Region/Pane/Panel, composition modes, fragmentation restraint — is defined in [`../system/composition.md`](../system/composition.md) (D-108–D-117).

## Core patterns

### Master / Detail

```text
Master | Detail
```

Selection in Master determines Detail.

### List / Inspector

```text
List | Inspector
```

Inspector reflects the selected object.

### Table / Inspector

```text
Table | Inspector
```

Suitable for high-information-density workflows.

### Form / Preview

```text
Form | Preview
```

Useful when the result of editing benefits from simultaneous visibility.

### Navigation / Content / Context

```text
Navigation | Content | Context
```

Useful in complex applications where persistent navigation and contextual information materially improve the workflow.

## Context preservation

Prefer updating contextual regions in place rather than navigating away from the primary Content Space when both belong to the same task.

## Expansion

Allow important regions to temporarily occupy more of the Content Space when detailed work requires it.

## User layout control

Where appropriate, users may:

- resize panes
- collapse panels
- show/hide contextual regions
- switch layouts
- save arrangements in Workspaces

## Fragmentation test

Before adding a region, ask:

> Does this region represent a meaningful relationship or simultaneous task?

If not, prefer a simpler composition.
