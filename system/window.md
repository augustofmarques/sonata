# System — Window

## Status

Decided: native window behavior takes precedence, multiple windows are permitted (D-122), window state may be preserved (D-124) (see [`application-shell.md`](application-shell.md), D-118–D-129). Open: multi-monitor restore policy, shell-layout persistence format (see Open questions).

## Purpose

Window represents the platform-level visual container of an application context.

Sonata uses platform-native window behavior whenever available (D-118).

## Native behavior

The implementation should defer to platform conventions for:

- title bar
- window controls
- resize
- move
- minimize
- maximize
- fullscreen
- snapping
- multi-monitor behavior
- system menus

## Sonata responsibilities

Sonata defines:

- semantic relationship to Workspace
- relationship to Content Space
- application chrome
- contextual regions
- shell composition
- preservation of user state

## Multiple windows

Multiple windows are permitted when independent or simultaneous contexts materially benefit the workflow (D-122). See [`application-shell.md`](application-shell.md).

## Window state persistence

Where platform conventions and privacy/security considerations permit, applications may restore (D-124):

- geometry
- display assignment
- maximized state
- fullscreen state
- workspace association

## Platform identity

A Sonata application should feel appropriate to its host platform.

Native conventions should be preserved when they do not conflict with Sonata's semantic or accessibility requirements.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Application Shell) for what remains open, including multi-monitor restore policy and shell-layout persistence format.
