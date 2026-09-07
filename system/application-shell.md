# System — Application Shell

## Status

Decided: native-chrome precedence, optional compact application header, multiple-window and multi-monitor support, window-state preservation, the shell/content/system-UI distinction, the Workspace→Window→Content Space→View relationship, shell customization, compact mobile shell, and restrained shell expression (D-118–D-129). Tool-area docking/floating/collapsing/resizing follows the general Composition model (D-109, D-113, D-114, [`composition.md`](composition.md)) rather than a separate rule, and Workspace itself is the existing D-060 concept rather than restated here. Open: exact compact-header anatomy, native-chrome integration per platform, docking model, shell-layout persistence format (see Open questions).

## Purpose

Application Shell defines the high-level structure through which a Sonata application organizes its window, navigation, content, tools, status and overlays.

The Application Shell is the outer framework within which Content Space and Workspaces operate.

## Core structure

A Sonata application may conceptually contain:

```text
Application Shell
├── Native Window Chrome
├── Optional Compact Application Header
├── Navigation
├── Tool Areas
├── Content Space
├── Contextual Areas
├── Status
└── Overlays
```

Not every application requires every region.

## Native window chrome

The operating system/window manager is responsible for native window-management controls and behavior wherever the platform provides them (D-118).

Sonata should not unnecessarily duplicate:

- title bars
- window controls
- system menus
- drag regions
- native window controls

Applications should use the native window chrome where appropriate.

## Application header

A Sonata application does not require a separate application title area when the native window already provides sufficient title/window identity (D-119).

A compact application header may be introduced when the application requires:

- additional contextual controls
- view identity
- navigation
- contextual actions
- integrated application controls

The header should remain compact and purposeful.

Sonata does not require a decorative application title bar.

## Header and content relationship

Application headers belong to the application shell, not to the content itself.

Where a header represents the current Content Space, its information and controls may update with changes in view or context.

## Application identity

The application shell may provide restrained expressive branding where appropriate (D-129).

Hero or highly expressive treatment should not overwhelm ordinary application chrome.

## Navigation

Navigation is a shell-level concern.

The appropriate manifestation may be:

- sidebar
- rail
- top navigation
- bottom navigation
- tabs
- contextual navigation
- other Sonata navigation patterns

The shell should not assume a single navigation geometry. See [`navigation.md`](navigation.md).

## Tool areas

Applications may provide persistent or contextual tool areas.

Examples include:

- inspector
- layers
- properties
- navigator
- tools
- filters
- contextual controls

Tool areas are Panels in the Composition model and may be docked, floating, collapsed, hidden or reordered under the same rules as any other Panel — see [`composition.md`](composition.md) (D-109, D-113, D-114) rather than a shell-specific docking rule.

## Content Space

Content Space is the primary working context (see [`composition.md`](composition.md), D-108).

The shell should provide the spatial resources needed to compose:

- main content
- supporting content
- contextual regions
- inspectors
- previews
- tools

The shell should avoid unnecessarily constraining Content Space.

## Status

Persistent application status may be exposed by the shell when relevant (see [`feedback.md`](feedback.md) Persistent status, D-100).

Examples:

- connection state
- synchronization
- background operations
- save state
- processing
- environment state

Status should not consume persistent space when the information is not meaningful to the current workflow.

## Overlays

The shell hosts transient layers such as:

- dialogs
- popovers
- sheets
- floating surfaces
- contextual overlays
- command surfaces

These remain associated with the current application context.

## Multiple windows

Applications may use multiple windows when the workflow benefits from independent contexts (D-122).

Examples:

- documents
- projects
- inspectors
- detached tools
- secondary workspaces
- auxiliary views

Multiple windows are an official Sonata capability.

## Multi-monitor environments

Sonata applications should support multiple windows across multiple displays where the platform permits it (D-123).

Window placement and monitor management are platform responsibilities, while application state may preserve useful contextual relationships.

## Fullscreen

Fullscreen is an official application capability where appropriate.

Fullscreen should not eliminate necessary application orientation or create inaccessible state transitions.

## Window state

Applications may preserve (D-124):

- size
- position where platform-safe
- maximized state
- fullscreen state
- selected workspace
- visible tool areas

according to platform conventions and user preferences. See [`window.md`](window.md).

## Workspace relationship

A Workspace represents a working context (D-060).

A Window is a visual manifestation of that context.

A Document or View represents content within the workspace/window (D-126).

```text
Workspace
   ↓
Window
   ↓
Content Space
   ↓
View / Document
```

One workspace may correspond to one or multiple windows depending on application needs.

## Application vs system UI

The shell must distinguish (D-125):

```text
System UI
Application chrome
Content
Contextual UI
Transient UI
```

Application UI must not visually or semantically impersonate system UI unnecessarily.

## Desktop shell

Desktop-class applications may use a rich shell containing:

- persistent navigation
- toolbars
- multiple tool areas
- Content Space
- inspectors
- status
- contextual controls
- multiple windows

The shell should take advantage of available space when doing so materially improves workflow. See [Desktop Class](../adaptive/desktop.md).

## Mobile shell

Mobile-class applications should use a more focused shell (D-128).

Elements that remain persistent on Desktop may become:

- contextual
- collapsible
- navigated
- floating
- bottom-anchored
- secondary

on Mobile.

The semantic role remains consistent. See [Mobile Class](../adaptive/mobile.md).

## Shell customization

Applications may allow users to customize shell elements such as (D-127):

- visible tools
- navigation visibility
- navigation order
- toolbar contents
- tool-area visibility
- tool-area position
- panel size
- docking
- workspace arrangement

when application complexity justifies it.

## Workspace persistence

Shell configuration may be saved as part of Workspace state (D-060, D-077).

A workspace may restore:

- shell composition
- navigation
- tool areas
- panel arrangement
- open content
- visibility
- dimensions
- relevant user configuration

## Platform adaptation

The shell's semantic architecture is platform-independent.

Implementation may follow platform conventions for:

- native title bars
- menus
- window controls
- fullscreen
- multiple windows
- drag regions
- system notifications
- window placement

Sonata defines the application semantics and desired relationships rather than requiring pixel-identical shells.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Application Shell) for what remains open: exact compact-header anatomy, native-chrome integration per platform, toolbar overflow/customization UI, the multiple-window/workspace relationship, multi-monitor restore policy, the exact docking model, floating-panel anchoring, shell-layout persistence format, and fullscreen transition behavior.
