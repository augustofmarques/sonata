# System — Operations

## Status

Decided: Operations as first-class semantic entities with an identifiable lifecycle, identity, history and error-recovery model (D-186). Reversible-operation/undo integration follows the existing D-091 rather than a separate rule, and background/non-blocking behavior follows the existing D-096. Open: operation cancellation semantics, operation history retention, cross-view state synchronization implementation (see Open questions).

## Purpose

Operations represent user-initiated or system-initiated work that can produce state changes, feedback and potentially undoable effects. See [`state.md`](state.md) for the semantic states operations produce.

## Operation lifecycle

Typical lifecycle:

```text
Created
  ↓
Queued
  ↓
Running
  ↓
Completed
```

Alternative paths:

```text
Running → Failed
Running → Cancelled
Running → Paused
Paused  → Running
```

## Operation identity

Where useful, operations should have identifiable context (D-186).

Examples:

```text
Export #42
Upload #17
Sync #8
Import #11
```

This enables consistent relationships between:

- progress
- feedback
- notifications
- undo
- command systems
- background work

## Operation and undo

When an operation is reversible, it should integrate with the application's undo system — this is the existing Undo-first recovery decision ([`feedback.md`](feedback.md), D-091) applied to Operations rather than a separate rule.

```text
Operation
   ↓
State change
   ↓
Feedback
   ↓
Undo
```

## Operation and feedback

An operation may produce:

- progress
- completion
- warning
- error
- notification

The operation should not require every possible feedback mechanism. See [`feedback.md`](feedback.md).

## Background operations

Long-running operations may continue independently from the current view — the existing Background operations decision ([`feedback.md`](feedback.md), D-096) rather than a separate rule.

Users should be allowed to continue unrelated work when safe.

## Operation persistence

Operations should not automatically become persistent application data.

An operation may belong to:

- transient session state
- workspace state
- durable task history

depending on its semantics. See [`state.md`](state.md) (D-176).

## Operation history

Applications may retain completed operations when users reasonably need to inspect:

- what happened
- when
- result
- failure reason
- recovery options

## Error recovery

Failed operations should provide available recovery actions such as:

- retry
- undo
- resume
- fix
- dismiss

## Offline operations

Operations may remain:

- queued
- local-only
- waiting for connection
- retrying

when offline behavior is supported. See [`state.md`](state.md) (D-183).

## Optimistic operation

Operations may expose optimistic results when the system can safely reconcile later remote confirmation (see [`state.md`](state.md), D-185).

The UI must distinguish:

```text
locally applied
vs
remotely confirmed
```

where the difference matters.

## Operation independence

Operations should not block unrelated work merely because they are still executing.

## Platform independence

Operation semantics are platform-independent (D-191).

The implementation may use:

- background threads
- jobs
- tasks
- services
- workers
- platform task APIs

without changing the Sonata model.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## State) for what remains open, including operation cancellation semantics and operation history retention.
