# System — State & Interaction Model

## Status

Decided: the domain/UI state split, four persistence scopes (Persistent/Session/Workspace/Transient), composable state dimensions, the Unavailable/Disabled/Read-only/Locked/Hidden taxonomy with disabled restraint, Dirty as an official state distinct from Synced, offline/degraded operation, synchronization conflict, optimistic operations, shared state across views, workspace-state restoration boundaries, state-triggered feedback, and state accessibility (D-175–D-191, plus Operations in [`operations.md`](operations.md), D-186). Background-operation non-blocking behavior and operation/undo integration follow the existing D-096 and D-091 rather than restating them. Open: state-token naming conventions, state serialization boundaries, session persistence policy, workspace-state schema, optimistic-state timeout/reconciliation patterns, conflict-resolution UI patterns (see Open questions).

## Purpose

Sonata defines a unified model for application state, interaction state, workspace state and transient state.

The goal is to prevent individual components from inventing incompatible concepts of state.

State is semantic (D-175, Principle 55).

Visual components provide a presentation of state.

## Domain vs UI state

Sonata explicitly distinguishes between (D-175):

### Domain / application state

State that describes the application, its data or the operation of the product.

Examples:

- saved
- unsaved
- synced
- syncing
- offline
- degraded
- locked
- completed
- failed

### UI / interaction state

State that describes how the user is interacting with the interface.

Examples:

- focused
- hovered
- selected
- pressed
- expanded
- collapsed
- active

The two categories may coexist.

Example:

```text
document:
  dirty
  syncing

interface:
  selected
  focused
```

This generalizes the same distinction Selection already draws between selection state and focus/hover/active/checked/highlighted ([`selection.md`](selection.md), D-079) to the full state model.

## State persistence

Sonata recognizes four primary persistence scopes (D-176):

```text
Persistent
Session
Workspace
Transient
```

### Persistent

State that should survive application restarts and represents durable application or user data.

Examples:

- document contents
- saved configuration
- persistent user preferences

### Session

State that lasts for the current application/session context but does not necessarily represent durable user configuration.

Examples:

- temporary search state
- current operation context
- temporary navigation history

### Workspace

State associated with a reusable working environment. See [`../patterns/workspace.md`](../patterns/workspace.md) (D-060).

Examples:

- panel visibility
- panel dimensions
- table configuration
- tool arrangement
- selected workspace
- relevant view configuration

### Transient

Short-lived state associated with a current interaction or immediate system event.

Examples:

- hover
- pressed
- temporary loading indicator
- ephemeral highlight

## State is composable

State dimensions are independent whenever their semantics are independent (D-177). This extends the same orthogonality preference Components already apply to visual variants ([`components.md`](components.md), D-035) to state itself.

Valid examples:

```text
selected + disabled
focused + expanded
dirty + syncing
readonly + selected
locked + visible
```

Avoid giant mutually exclusive state enumerations.

## State vs presentation

Semantic state must exist independently of its visual presentation.

A component may present state through:

- color
- typography
- shape
- iconography
- motion
- haptics
- layout
- text

but none of those presentation mechanisms constitute the state itself.

## Common state distinctions

Sonata explicitly distinguishes (D-178):

```text
Unavailable
Disabled
Read-only
Locked
Hidden
```

### Unavailable

The capability or resource cannot currently be used or accessed.

### Disabled

The control exists but is currently not activatable.

### Read-only

The user may inspect, select, copy or navigate the content, but cannot modify it through the current context.

### Locked

The content or resource exists but modification or access is constrained by a specific lock or permission state.

### Hidden

The element is not currently presented.

These states must not be conflated.

## Disabled restraint

Disabled controls should be used when appropriate, but applications should avoid using disabled state as the only explanation of why an action cannot currently be performed (D-179). This extends the self-explanatory-interface decision ([`actions.md`](actions.md), D-038) to the disabled state specifically.

Where useful, the interface should explain:

- why the action is unavailable
- what prerequisite is missing
- what the user can do next

## Read-only behavior

Read-only content remains interactive where appropriate (D-180).

Depending on context, it may support:

- selection
- copying
- navigation
- inspection
- search

Read-only does not imply inaccessible.

## Dirty / unsaved

Dirty or unsaved is an official Sonata application state (D-181).

Applications should clearly communicate when user changes have not been durably saved.

Possible presentation includes:

- modified indicator
- window/document marker
- persistent status
- save affordance
- navigation warning

The exact presentation depends on context.

## Saved vs synced

`Saved` and `Synced` are distinct states (D-182).

```text
Saved locally
≠
Synced remotely
```

An application may be:

```text
saved + syncing
saved + offline
saved + synced
dirty + offline
dirty + syncing
```

These combinations are legitimate.

## Operational states

Applications may represent operational state such as:

- queued
- running
- paused
- processing
- saving
- syncing
- completed
- failed
- cancelled
- unavailable

These states may be presented differently by different components. See [`operations.md`](operations.md).

## Offline and degraded operation

Offline or degraded environments are official Sonata states (D-183).

When continued operation is possible, the application should continue functioning rather than simply fail closed.

The UI should communicate the current operating condition. This is the normative offline/degraded model behind the "Offline" example already listed under Feedback's Persistent status ([`feedback.md`](feedback.md), D-100).

Examples:

```text
Offline
Limited connectivity
Degraded service
Local-only mode
Synchronizing
```

The exact terminology should follow the application's domain and Foundation writing guidance.

## Offline-first behavior

When safe and semantically appropriate, applications may allow users to continue working while offline.

The UI should make the current state clear without unnecessarily blocking unrelated work.

## Synchronization conflict

Synchronization conflict is an official Sonata state (D-184).

A conflict may be represented as:

```text
Local changes
Server changes
Conflict
Resolution
Resolved
```

The application should make the conflict and available resolution clear.

## Optimistic operations

Sonata supports optimistic interaction (D-185).

When safe, an application may present a successful local result before remote confirmation.

The application must provide appropriate handling if the remote operation later fails.

Examples:

```text
optimistic success
    ↓
remote confirmation
    ↓
confirmed
```

or:

```text
optimistic success
    ↓
remote failure
    ↓
reverted / recovery
```

The user should not be misled about the actual persistence state.

## State synchronization across views

Multiple views representing the same data or context should observe shared semantic state (D-187) — the same principle Selection already applies to selected state specifically ([`selection.md`](selection.md), D-080), generalized to state overall.

Examples:

```text
Selection
    ↓
Table + Inspector

Dirty
    ↓
Document + Window + Save status

Syncing
    ↓
Document + Status + Notification
```

Views should not maintain conflicting copies of the same semantic state.

## Workspace state

Workspace may preserve appropriate UI and working-context state.

Workspace should not arbitrarily preserve all application state (D-188).

Do not restore transient conditions such as:

- completed operations
- expired notifications
- temporary hover states
- obsolete loading indicators

unless explicitly meaningful.

## State restoration

When restoring workspace or session state, the application should verify that the state remains valid.

For example:

```text
saved panel
    ↓
panel still exists?
    ├── yes → restore
    └── no  → gracefully adapt
```

## State transitions

State changes may trigger (D-189):

- visual updates
- feedback
- motion
- haptics
- notifications
- workspace changes

but each mechanism is contextual.

A state change does not automatically require every feedback channel.

## Accessibility

Semantic state must be exposed to assistive technologies through appropriate platform mechanisms (D-190). This is the general statement behind the accessibility requirements already decided per domain (e.g. Selection D-088, Feedback D-106, Containers D-169).

Visual state alone is insufficient.

## Platform independence

The state model is independent of implementation framework (D-191), consistent with the general platform-independence decision (D-016).

Platforms may have different APIs and native state mechanisms, but should preserve the same Sonata semantic distinctions.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## State) for what remains open: state-token naming conventions, state serialization boundaries, session persistence policy, workspace-state schema, optimistic-state timeout/reconciliation patterns, conflict-resolution UI patterns, and platform accessibility mappings.
