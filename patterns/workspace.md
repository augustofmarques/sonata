# Pattern — Workspace

Workspace represents a reusable working context. Workspace itself is the official Sonata concept decided in D-060 ([`../governance/decision-log.md`](../governance/decision-log.md#d-060--workspaces)); this pattern describes its concrete contents and operations, and [`../system/application-shell.md`](../system/application-shell.md) (D-126) defines its relationship to Window and Content Space.

## Workspace contents

A workspace may contain:

- navigation state
- window association
- open content
- tool visibility
- panel arrangement
- inspector state
- table configuration
- filters
- sorting
- grouping
- toolbar configuration
- density and visual preferences where appropriate

## Workspace purpose

Workspaces are particularly valuable in complex professional software.

Examples:

- modeling
- editing
- analysis
- review
- administration
- production
- project-specific environments

## Workspace operations

Applications may support (D-061):

- create
- rename
- switch
- save
- duplicate
- restore
- reset
- delete

## User customization

Users may configure a workspace by (D-114, D-127):

- showing/hiding tools
- reordering navigation
- resizing panels
- changing compositions
- selecting visible data
- configuring toolbars

## Workspace vs application preferences

Application preferences define general behavior.

Workspace settings define the working arrangement for a specific context.

## Workspace vs document

A workspace is broader than a document.

A document may exist inside a workspace without defining the complete workspace composition.

## Workspace restoration

Applications may restore the last active workspace or allow users to explicitly select one when reopening.
