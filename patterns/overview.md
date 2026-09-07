# Patterns — Overview

Patterns are optional reusable solutions to recurring application workflows.

They are not mandatory merely because Sonata defines them.

Patterns sit between Compound Components and Application Components on the Sonata component graduation ladder (see [`../system/components.md`](../system/components.md)). A recurring, complex workflow — search, command palette, power-user shortcuts — is not forced into a single flat component just to keep the catalog small.

Initial pattern families:

- search
- command palette
- shortcuts
- filtering
- data exploration
- selection
- feedback
- notifications
- power-user workflows

Sidebar, Navigation Rail and Breadcrumbs are official System navigation *components* (see [`../system/navigation.md`](../system/navigation.md)), not Patterns — they follow the graduation ladder in `components.md` and are often structurally necessary rather than complexity-justified additions. Workspaces are a power-user pattern; see [Power User](power-user.md).
