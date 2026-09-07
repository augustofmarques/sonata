# Pattern — Selection

Selection is a cross-component interaction pattern. The normative semantic model — models, states, persistence, Selection Mode, accessibility — is defined in [`../system/selection.md`](../system/selection.md) (D-068, D-078–D-088).

## Shared selection model

Where multiple views represent the same objects, they should share the same semantic selection.

```text
Data / Object Model
        ↓
     Selection
   ┌────┼────┐
   ↓    ↓    ↓
 Table List Inspector
```

## Selection summary

Bulk actions should expose selection scope.

```text
12 items selected
```

or, where needed:

```text
12 visible items selected
```

## Selection actions

When selection exists, relevant bulk actions should become discoverable and contextually prominent.

## Reversible operations

Operations affecting selections should integrate with undo/redo when practical.

## Spreadsheet workflow

Sonata explicitly supports spreadsheet-like selection workflows when applications need them.

The design system should preserve visual coherence without suppressing:

- keyboard efficiency
- range selection
- multi-selection
- cell selection
- bulk actions
