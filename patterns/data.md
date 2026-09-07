# Pattern — Data

Data-oriented interfaces should explicitly manage:

- dense tables
- sorting
- filtering
- selection (see [`selection.md`](selection.md) and [`../system/selection.md`](../system/selection.md))
- bulk actions
- pagination or progressive loading
- empty states
- partial states
- numeric presentation
- identifiers

Desktop may expose multiple simultaneous contexts; mobile may transform them into sequential detail views.

The concrete component catalog (Table, List, Master-Detail, Split View, Inspector, Grouped Collection, Timeline) and its normative decisions live in [`../system/data-display.md`](../system/data-display.md).

## Spatial composition

Prefer simultaneous visibility when it materially improves comparison or task completion (D-056, Principle 18):

```text
List | Detail
Table | Inspector
Navigation | Data | Context
```

Sequential navigation is acceptable when simultaneous presentation would overwhelm the available space or cognitive load.

## Current vs historical information

Applications should distinguish active operational information from historical or completed information when the distinction is meaningful (D-075, Principle 20). Active work may receive greater prominence, spatial allocation, default filtering and interaction priority; historical data may be archived, collapsed, filtered, grouped or placed in secondary views. The appropriate treatment depends on the domain.
