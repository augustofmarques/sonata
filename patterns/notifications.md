# Pattern — Notifications

Notification is a persistent event communication mechanism. The normative Notification and Notification Center model is defined in [`../system/feedback.md`](../system/feedback.md) (D-101–D-103).

## Notification lifecycle

```text
Event
  ↓
Notification
  ↓
Viewed / Acted upon
  ↓
Resolved / Archived
```

## Notification persistence

Only events with meaningful ongoing relevance should become persistent notifications.

Transient feedback should not automatically enter notification history.

## Grouping

Related events should be grouped where appropriate.

## Actions

Notifications may contain actions when the action is directly relevant to the event.

## Notification Center

Applications may provide a Notification Center as the primary place to inspect persistent notification history.

The Notification Center should prioritize meaningful information and avoid duplicate noise.
