# System — Navigation

## Status

Decided: navigation component catalog, Breadcrumbs as official, Mobile/Desktop adaptation model, density integration (D-054, D-059, D-063, D-064). Open: exact anatomy for each component, breakpoint behavior, animation details (see Open questions).

## Purpose

Navigation components let users move between destinations. The architectural principles — why and when a given mechanism applies — live in [`../foundation/layout.md`](../foundation/layout.md) (D-054–D-058); this file catalogs the concrete components.

## Sidebar

Sidebar is an official Sonata navigation component. It is particularly appropriate when:

- there are many peer destinations
- frequent switching is expected
- persistent orientation is beneficial
- desktop space supports persistent navigation

Sidebar is not the universal default (D-054). It may be expanded, collapsed or hidden when the application supports those states (D-055).

## Navigation Rail

Navigation Rail is an official Sonata component. It provides a more space-efficient persistent navigation mechanism when full labels or a full sidebar are not necessary, and may expand into a fuller navigation surface where appropriate.

## Top navigation

Top navigation is permitted. Sonata must not assume that navigation belongs on the left side of the application — top navigation should be selected when it better fits the application's information architecture, platform conventions or available composition.

## Tabs

Tabs represent related peer destinations or views within a common context. They should not be used as a generic replacement for application navigation, deep hierarchy or unrelated destinations. Follow the Foundation's GNOME-informed tab guidance ([`../foundation/interaction.md`](../foundation/interaction.md)).

## Breadcrumbs

Breadcrumbs are an official Sonata navigation component (D-059), primarily providing orientation, hierarchy awareness and contextual navigation. They are particularly useful in complex hierarchical environments. Breadcrumb items should be interactive where navigation semantics permit; breadcrumbs supplement navigation and do not necessarily replace primary navigation.

## Back navigation

Back navigation should follow established platform conventions whenever available. Sonata does not require a novel universal back-navigation mechanism, but back navigation should preserve the user's sense of hierarchy and history.

## Mobile

Mobile may use a materially different navigation presentation from Desktop while the semantic navigation architecture remains consistent (D-063):

```text
Desktop
Sidebar → Projects

Mobile
Navigation destination → Projects
```

The destination semantics remain equivalent even when the mechanism changes. Mobile should not simply render a desktop sidebar as a compressed or awkward substitute when another navigation mechanism better fits the interaction environment — see [Mobile Class](../adaptive/mobile.md) for the concrete adaptation guidance and depth-minimization rules.

## Desktop

Desktop navigation should take advantage of available space when persistent orientation or rapid switching materially improves productivity (D-056; see [Desktop Class](../adaptive/desktop.md) for composition examples).

## Platform conventions

Sonata defines semantic navigation behavior and intended interaction outcomes. Implementation may use platform-native navigation mechanisms where appropriate — the same Sonata navigation concept does not require identical technical implementation across Web, Qt, GTK, Android or other platforms (D-034). Semantic consistency is required; pixel identity is not.

## Command palette and search relationship

Command palettes and global search surfaces supplement navigation and must not replace ordinary visible navigation (D-062). A user should be able to use the application indefinitely without knowing that a command palette exists. See [Command Palette](../patterns/command-palette.md) and [Search](../patterns/search.md).

## Navigation customization

When application complexity justifies it, users may customize navigation through showing/hiding, reordering or pinning destinations, collapsing navigation, and choosing visible tool sets or workspace-specific navigation (D-061). See [Workspaces](../patterns/power-user.md) for workspace-level customization. Capability is global; exposure is contextual (Principle 9, D-017) — applications determine which capabilities are exposed.

## Density

Navigation participates in Sonata's global density system (D-064; see [`../expression/spacing-density.md`](../expression/spacing-density.md)). Changing density should coordinate item spacing, row heights, control dimensions, icon sizing where appropriate, label spacing and group spacing without breaking navigation hierarchy or accessibility.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Navigation) for what remains open: exact sidebar/rail anatomy, workspace persistence model and switching UI, maximum recommended visible mobile destinations, exact breakpoint behavior, and navigation animation details.
