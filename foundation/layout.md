# Foundation — Layout & Information Architecture

## Status

Decided: navigation architecture, persistent-navigation rationale, space-as-a-resource and complexity-accommodation principles (D-054–D-058). The general composition model this principle extends to — Content Space, Region/Pane/Panel, composition modes — is defined in [`../system/composition.md`](../system/composition.md) (D-108–D-117). Open: exact breakpoint behavior and other specifics (see Open questions).

Sonata uses the existing GNOME HIG guidance as its authoritative foundation for page structure, layout logic, hierarchy and information architecture.

The Foundation answers:

- What belongs on the screen?
- Where does it belong?
- How is information grouped?
- What is primary or secondary?
- How does the user move between contexts?
- Which actions are persistent, contextual or discoverable elsewhere?

Layout decisions precede visual expression.

The Foundation does not mandate a particular radius, palette, surface treatment, typography family or animation style.

## Composition principles

- Prefer clear hierarchy over decorative symmetry.
- Use available space intentionally.
- Avoid adding chrome without functional justification.
- Preserve orientation and context.
- Adapt composition rather than merely shrinking it.
- Allow strong visual emphasis inside an established structural hierarchy.

## Navigation architecture

Sonata does not prescribe one universal navigation mechanism (D-054). The appropriate mechanism depends on:

- number of destinations
- hierarchy depth
- frequency of switching
- relationship between destinations
- available space
- workflow complexity
- interaction class
- need for simultaneous context

Sidebar, navigation rail, top navigation, tabs, breadcrumbs, hierarchical/drill-down navigation, contextual navigation, bottom navigation and workspace navigation are alternative manifestations of navigation semantics, not separate competing philosophies. See [`../system/navigation.md`](../system/navigation.md) for the concrete component catalog.

### Persistent navigation

Persistent navigation should be used when persistent orientation, frequent switching between destinations, or workflow efficiency materially benefits from keeping navigation visible (D-055). It is not mandatory: available screen space is a resource that may be allocated to navigation when doing so improves the task, and applications may let users collapse or hide persistent navigation, whether to recover space or simply to reduce visual presence.

### Navigation depth

Deep navigation is permitted when required by the application's domain, but navigation depth should be minimized when equivalent access can be provided through clearer composition, simultaneous visibility, direct navigation, search or workspace organization (D-058). Avoid unnecessary chains such as menu → submenu → submenu → submenu → screen when the same workflow could be expressed more directly; hierarchy, persistent sections, drill-down, split views, contextual panels, search, command surfaces and workspaces may all reduce navigation friction.

## Space as a resource

Sonata uses available space when additional simultaneous information materially improves comprehension, comparison, navigation or task efficiency (D-056). Do not artificially constrain complex desktop applications to narrow central columns when the available space could meaningfully support multiple panes, navigation, inspectors, simultaneous form/data views, comparison, contextual information or persistent tool areas — and do not fill available space merely for the sake of filling it. The complexity of the application, workflow and current context determines how aggressively space should be used.

The concrete regions and mechanisms this principle governs — Content Space, Pane, Panel, split/overlay/floating/modal composition, expansion, resizing — are specified in [`../system/composition.md`](../system/composition.md).

## Complexity accommodation

Sonata must support applications ranging across the full spectrum (D-057):

```text
Simple site/application
        ↓
Moderately complex application
        ↓
Professional productivity software
        ↓
Highly complex software
        ↓
CAD / engineering / enterprise environments
```

Sonata must not impose an artificial simplicity ceiling. Complexity should be organized, spatially legible, hierarchically structured, discoverable and customizable rather than artificially hidden — see [Complexity boundary](../system/components.md) (D-033) for the equivalent principle applied to individual components.
