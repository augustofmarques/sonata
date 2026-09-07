# System — Feedback

## Status

Decided: feedback as a first-class system, the core feedback-form taxonomy, proportionality, Undo-first recovery, error communication/severity, layout stability, background operations, Empty State, Progress, persistent status, and the Notification system (D-089–D-107). Haptic feedback within this domain follows the general haptics decision (D-028) rather than restating it. Open: exact severity taxonomy, Toast/Snackbar terminology and placement, Notification Center anatomy, progress-component anatomy, alert-interruption thresholds (see Open questions).

## Purpose

Feedback communicates the result, state, progress, consequence or availability of an operation or system condition.

Feedback is a first-class Sonata system (D-089).

It must communicate clearly without unnecessarily interrupting the user's workflow.

## Core feedback forms

Official Sonata feedback mechanisms include:

- Inline Message
- Toast
- Snackbar
- Banner
- Alert
- Progress Indicator
- Status
- Empty State
- Success State
- Error State
- Notification
- Notification Center

The appropriate mechanism depends on:

- severity
- persistence
- context
- urgency
- recoverability
- workflow impact
- platform
- available space

## Feedback hierarchy

Feedback should be proportional to the event (D-090).

```text
Micro event
    ↓
small / transient feedback

Meaningful event
    ↓
persistent contextual feedback

Serious event
    ↓
prominent feedback

Immediate critical event
    ↓
interruptive feedback
```

Not every event requires visible feedback.

## Severity

Feedback has a semantic severity.

Conceptual severity levels include:

- Informational
- Success
- Caution
- Warning
- Error
- Critical

Implementations may consolidate these labels where appropriate, but the system must distinguish ordinary information from increasingly consequential failures.

Severity is not identical to persistence.

A low-severity notification may persist.

A high-severity event may be transient if the user has already received sufficient contextual information.

## Severity vs presentation

Severity determines the importance of the event.

Presentation determines how the event is communicated.

The same severity may be presented differently depending on context.

Example:

```text
Error
    ↓
form field error
page-level error
banner
notification
modal alert
```

The appropriate presentation depends on scope and urgency.

## Inline feedback

Inline feedback is appropriate when the message belongs directly to the content or interaction that produced it (D-094).

Examples:

- field validation
- local state
- contextual explanation
- local error recovery

Inline feedback should not unnecessarily displace large portions of surrounding content.

Where an inline message would cause disruptive layout shift, another presentation may be preferable when it remains understandable.

## Toast / Snackbar

Toast/Snackbar is appropriate for transient, non-blocking feedback.

Typical use cases:

- completion
- minor status
- reversible action
- low-severity notification

Toasts should not be the primary mechanism for information that requires prolonged attention.

## Undo

When an operation is reversible, feedback should strongly favor providing Undo (D-091).

Example:

```text
Item moved
[Undo]
```

Undo should act on the operation that just occurred rather than requiring the user to manually reconstruct the previous state.

## Banner

Banner is appropriate for persistent contextual information whose relevance extends beyond a momentary event.

Examples:

- service status
- important page condition
- persistent warning
- contextual system state

Banner presentation remains application/context dependent.

An application may use a more expressive or prominent treatment when the page context justifies it.

## Alert

Alert is appropriate for information that requires significantly more attention.

Alerts may be interruptive when necessary.

They should not be used for ordinary status information.

## Critical alerts

Critical events that require immediate attention may justify interruption.

Examples include:

- imminent destructive consequence
- safety-critical state
- irreversible operation requiring immediate acknowledgement
- severe system condition that cannot reasonably be ignored

The threshold for interruption should remain high.

## Progress

Official progress forms include (D-099):

- determinate progress
- indeterminate progress
- staged progress
- background progress

Determinate progress should communicate meaningful progress toward completion.

Where a credible ETA can be calculated, it may be provided.

Example:

```text
Uploading
████████████░░░░░░
67%
About 2 minutes remaining
```

Progress indicators should not imply precision that the system does not actually have.

## Background operations

Long-running operations should not unnecessarily block the user's entire application (D-096).

When practical, long-running work should move into a background state while allowing the user to continue with unrelated work.

Examples:

```text
Exporting...
Processing...
Synchronizing...
Uploading...
```

The user should not be forced to remain idle while waiting for operations that can safely continue in the background.

## Persistent status

Long-running or continuously relevant states may be represented through persistent status (D-100).

Status should remain visible while the underlying condition remains active and should update or disappear when the condition changes.

Examples:

```text
Syncing
Connected
Offline
Processing
Saving
Paused
```

The status mechanism should avoid requiring repeated notifications for an unchanged condition.

## Completion feedback

Completion feedback should be proportional to the importance of the operation (D-097).

Examples:

```text
minor action
→ microfeedback

meaningful operation
→ explicit completion status

major operation
→ stronger confirmation/completion feedback
```

## Error communication

Errors should communicate (D-092):

1. What happened
2. Why it matters, when useful
3. What the user can do next
4. Whether anything changed, failed or was lost

Avoid vague messages such as:

```text
Something went wrong.
Error.
Operation failed.
```

when more useful information is reasonably available.

## Error severity

Errors should distinguish at least (D-093):

### Recoverable

The user can reasonably correct or retry.

### Significant

The operation failed or the workflow is meaningfully affected.

### Critical

The user must be informed of a serious condition or consequence.

Severity should determine communication intensity, not merely color.

## Error recovery

Where practical, provide:

- Retry
- Undo
- Fix
- Cancel
- Restore
- Alternative action

Recovery should be presented near the error.

## Empty State

Empty State is an official Sonata component/pattern (D-098).

At minimum, the system distinguishes:

```text
Never had data
No results
Filtered out
No selection
Loading
Unavailable
Error
```

Empty states should communicate why the space is empty and what the user can do next when a useful next action exists.

## Loading State

Loading must communicate that the system is working when the delay is meaningful.

Possible representations include:

- progress bar
- spinner
- skeleton
- inline status
- persistent status

The choice depends on whether the user needs to understand:

- that work is happening
- how much has completed
- what content will appear
- how long it may take

## Notification

Notification is an official Sonata system (D-101).

Notifications communicate events that may remain relevant beyond the immediate context in which they occurred.

Notifications may be:

- transient
- persistent
- actionable
- informational
- status-oriented

Notifications should remain distinguishable from alerts and contextual messages.

## Notification Center

Notification Center is an official Sonata capability (D-101).

It may provide access to:

- recent notifications
- persistent notifications
- grouped notifications
- actionable notifications
- notification history where appropriate

The center should not become a dumping ground for every transient message.

Only events with meaningful persistence value should enter persistent notification history (D-102).

## Notification grouping

Related notifications should be groupable when doing so reduces repetition and noise (D-103).

Example:

```text
12 files processed
```

instead of:

```text
File 1 processed
File 2 processed
File 3 processed
...
```

## Feedback hierarchy and noise control

Complex applications must prevent feedback overload.

The system should prevent situations such as:

- many simultaneous toasts
- repeated notifications for one condition
- redundant banner + toast + notification
- repeated warnings for an unchanged state

A persistent condition should generally update existing feedback rather than repeatedly generate new feedback.

## Layout stability

Feedback should avoid unnecessary layout displacement (D-095).

When appropriate, use:

- overlays
- floating surfaces
- reserved contextual regions
- inline placement with allocated space
- status areas

rather than unexpectedly pushing major interface regions.

However, contextual inline messages may legitimately change layout when doing so materially improves comprehension.

## Feedback and Expression

Feedback may use Sonata Expression mechanisms:

- color
- shape
- motion
- animation
- iconography
- emphasis

Strong expression should correspond to meaningful severity or semantic importance.

## Color

Semantic feedback may use (D-104):

- success
- warning
- danger
- info

Color must not be the only mechanism conveying the meaning.

## Motion

Feedback may use motion for (D-105):

- appearance
- state transition
- completion
- error indication
- progress
- acknowledgement

Functional feedback takes priority over decorative animation.

## Haptics

When supported, important feedback may be reinforced through haptic interaction. Haptics remain an optional, supplementary modality — the general rule and open vocabulary questions are decided in [`../governance/decision-log.md`](../governance/decision-log.md#d-028--haptic-interaction) (D-028) rather than restated here.

An event must remain understandable without haptics.

## Accessibility

Important feedback must be exposed appropriately to assistive technologies (D-106).

Live feedback should use suitable announcement semantics.

Critical feedback should remain perceivable without relying exclusively on visual presentation.

## Writing

Feedback follows Sonata's Foundation writing principles (D-013, D-107). See [`../foundation/writing.md`](../foundation/writing.md).

Messages should be:

- specific
- direct
- concise
- actionable where appropriate
- consistent in terminology

The interface should explain the event rather than force users to consult documentation.

## Platform adaptation

Feedback may use platform-native mechanisms where appropriate.

The semantic distinction between:

- status
- notification
- alert
- contextual feedback

must remain intact even when presentation differs between platforms.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Feedback) for what remains open: exact severity taxonomy, Toast/Snackbar terminology and placement, Notification Center anatomy, notification grouping mechanics, live-region/announcement behavior, progress-component anatomy, ETA formatting, alert-interruption thresholds, feedback-stacking rules, and Mobile/Desktop presentation mappings.
