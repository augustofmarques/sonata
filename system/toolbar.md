# System — Toolbar

## Status

Decided: Toolbar as an official, compositional (not inherently horizontal) Sonata component with distinguishable application/view/selection/tool scopes (D-120, D-121). Density and customization follow the general Density (D-012, D-050, D-064) and Composition-customization (D-114, D-127) decisions rather than a separate toolbar-specific rule. Open: toolbar overflow behavior, toolbar customization UI (see Open questions).

## Purpose

Toolbar provides efficient access to actions and controls associated with an application, view or context.

## Toolbar is compositional

A Toolbar is not inherently horizontal (D-120).

Possible manifestations include:

- horizontal
- vertical
- floating
- docked
- contextual
- inline
- overlay

The appropriate form depends on:

- available space
- action relationships
- input modality
- platform
- workflow

## Scope

Toolbar actions may belong to (D-121):

- application scope
- view scope
- selection scope
- tool scope

These scopes should remain semantically distinguishable.

## Global actions

Application-level actions may remain persistent when useful.

## Contextual actions

Contextual toolbars may update when:

- view changes
- selection changes
- mode changes
- workflow changes

## Selection

When a meaningful selection exists, a toolbar may expose actions that apply to that selection. See [`selection.md`](selection.md) (D-082).

## Density

Toolbars participate in Sonata Density (D-012, D-050, D-064).

## Customization

Applications may allow users to (D-127):

- show/hide actions
- reorder actions
- group actions
- collapse toolbars
- move toolbars

when the application complexity justifies it.

## Discoverability

Customized or compact toolbars must preserve discoverability through (D-038):

- labels
- tooltips where appropriate
- menus
- shortcut hints
- contextual feedback

## Platform adaptation

Platform-native toolbar conventions may be used where appropriate.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Application Shell) for what remains open: toolbar overflow behavior and toolbar customization UI.
