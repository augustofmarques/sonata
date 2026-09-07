# Pattern — Feedback

Feedback should match event significance, persistence and context. The normative semantic model — feedback forms, severity, error communication, layout stability, notifications — is defined in [`../system/feedback.md`](../system/feedback.md) (D-089–D-107).

## Proportional feedback

Prefer the least disruptive mechanism that still communicates the event adequately.

```text
micro event
→ transient feedback

contextual issue
→ inline / contextual feedback

persistent condition
→ banner / status / notification

critical immediate event
→ alert / interruption
```

## Undo-first recovery

When an operation is reversible, provide Undo when practical.

## No unnecessary layout shift

Do not push major content simply to display transient feedback when another accessible presentation would communicate the same information without disruption.

## Self-explanation

Feedback should answer:

- What happened?
- What does it mean?
- What can I do?

when those answers are relevant.

## Background work

Long operations should remain non-blocking when the workflow allows it.

Users should be free to continue unrelated work.

## Active status

Persistent status should represent current conditions rather than repeatedly notifying users that the same condition still exists.

## Historical notifications

Notification history should contain meaningful events rather than every ephemeral interaction.

## Severity

Feedback presentation should be proportional to severity.

Higher severity may increase prominence and persistence, but severity does not automatically imply modal interruption.
