# System — Disclosure

## Status

Decided: Disclosure as a first-class component/pattern family, the Accordion/Collapsible/Expandable Row/Menu/Context Menu taxonomy, progressive disclosure as a bounded principle, disclosure-depth and menu-depth restraint, hover/touch disclosure accessibility requirements, and disclosure-and-workspace/motion integration (D-130–D-140). Sonata's general complexity-accommodation stance (D-057, Principle 19) already covers why complexity-rich software is a valid target and why complexity should be organized rather than hidden — this file applies that stance to disclosure mechanisms rather than restating it. Open: exact Accordion anatomy, single/multiple-open defaults, nesting heuristics, menu overflow/submenu presentation, disclosure animation timings (see Open questions).

## Purpose

Disclosure reveals, hides, expands or collapses information or functionality while preserving the current semantic context.

Disclosure is a mechanism for managing complexity (D-130).

It must reduce unnecessary cognitive load without arbitrarily hiding useful functionality.

## Core distinction

> Disclosure reveals or collapses content related to the current context.
>
> Navigation changes the current context or destination.

Disclosure must not be used as a disguised navigation system.

## Core disclosure mechanisms

Official Sonata disclosure mechanisms include:

- Accordion
- Collapsible
- Expandable Row
- Details / Disclosure
- Popover
- Menu
- Context Menu
- Progressive Disclosure

The system remains extensible.

## Accordion

Accordion groups related sections that may be expanded or collapsed (D-132).

Sonata permits:

- single-open behavior
- multiple-open behavior

The choice depends on the content relationship.

Accordion should not be used simply to reduce visible content when simultaneous visibility would materially improve the task.

## Collapsible

Collapsible represents an independently expandable or collapsible region (D-132).

It differs from Accordion because it does not imply membership in a mutually related collection of sections.

It is appropriate for:

- tool areas
- inspectors
- contextual information
- supporting content
- advanced options

## Initial state

Disclosure components may support:

- open by default
- closed by default
- remembered state
- context-dependent initial state

The appropriate default depends on whether the content is:

- essential
- frequently used
- secondary
- optional
- expensive in visual space

## Persistence

Expansion state may be persisted when the application benefits from remembering the user's working arrangement (D-139).

Persistent disclosure state may be part of Workspace state (D-060).

## Progressive disclosure

Progressive disclosure is an official Sonata design principle (D-131).

It should be used to:

- manage complexity
- sequence information
- reveal details when relevant
- reduce initial cognitive load

It must not be used as an excuse to hide necessary functionality.

When a user frequently needs information simultaneously, persistent or simultaneous presentation should be preferred (D-056, Principle 18).

## Disclosure depth

Nested disclosure is permitted when structurally justified (D-134).

However, Sonata discourages excessive nesting.

Avoid structures such as:

```text
Section
  ↓
Section
  ↓
Section
  ↓
Section
  ↓
Control
```

when the same workflow could be expressed through:

- better composition
- simultaneous visibility
- direct navigation
- contextual panels
- search
- workspace organization

No universal numeric nesting limit is required.

The implementation should use a reasonable contextual limit.

## Expandable rows

Expandable rows are an official pattern for collections and tables (D-133).

They are appropriate when:

- details belong directly to the selected row
- the information can reasonably remain within the collection context
- expanding does not destroy scanability

For more complex details, use Inspector, Master-Detail or another suitable composition. See [`data-display.md`](data-display.md).

## Disclosure vs Inspector

When the additional content:

- is brief
- belongs directly to one item
- benefits from local expansion

Expandable Row may be appropriate.

When the information:

- is substantial
- contains tools
- requires editing
- remains useful while inspecting multiple fields
- benefits from persistent spatial allocation

Inspector or contextual panel may be preferable.

## Disclosure vs Modal

Use local disclosure when the user benefits from keeping the surrounding context visible and interactive.

Use a modal when attention must temporarily be constrained or the operation requires focused interruption.

## Disclosure vs Navigation

If the user remains within the same semantic Content Space, disclosure should generally be preferred over navigation when the information is simply being revealed. See [`composition.md`](composition.md) (D-116, Composition is distinct from navigation).

Navigation is appropriate when the user is entering a distinct destination or context.

## Menu

Menu is an official Sonata component for presenting a set of related actions or choices (D-135).

Menus are contextual interaction surfaces.

Menus are not application navigation. Menu Button, the composite action that opens a Menu, is separately decided in [`actions.md`](actions.md) (D-041).

## Context Menu

Context Menu is an official Sonata component for contextual actions associated with an object, selection or location (D-135).

Context menus should remain discoverable through accessible alternatives.

## Menu depth

Sonata strongly discourages deeply nested menus (D-136).

Avoid:

```text
Menu
  → submenu
    → submenu
      → submenu
```

when actions could instead be presented through:

- direct actions
- grouped actions
- contextual panels
- command surfaces
- search
- better composition

A single level of submenu may be appropriate when the relationship is clear.

Deeper nesting requires strong contextual justification.

## Hover disclosure

Hover may reveal supplementary information or low-risk controls (D-137).

Important functionality must not depend exclusively on hover.

Hover-only disclosure must have an equivalent interaction for:

- keyboard
- touch
- assistive technology

## Touch

Touch interfaces may use platform-appropriate interactions such as (D-138):

- tap
- long press
- established swipe gestures

to reveal contextual content.

Gestures must remain discoverable and must not be the sole way to access critical functionality.

## Mobile

Mobile may use more progressive disclosure than Desktop because available space is limited.

This may result in additional interaction steps.

Additional steps are acceptable when they meaningfully prevent visual overload and preserve comprehension.

Mobile should not blindly reproduce Desktop's simultaneous regions when that would produce an unusable interface. See [Mobile Class](../adaptive/mobile.md).

## Desktop

Desktop should favor simultaneous visibility when relevant information or tools are repeatedly needed.

Disclosure may be used for:

- advanced options
- secondary tool areas
- contextual details
- optional panels

but should not become a substitute for effective use of available screen space. See [Desktop Class](../adaptive/desktop.md).

## Motion

Disclosure transitions should use Sonata Motion to communicate (D-140):

- expansion
- collapse
- spatial relationship
- continuity

Motion should remain subordinate to comprehension.

## Accessibility

Disclosure must expose:

- expanded/collapsed state
- control relationship
- accessible name
- focus behavior
- keyboard operation

Keyboard users must be able to open and close disclosure controls.

## Customization

Applications may allow users to configure:

- default expanded state
- visible sections
- persistent tool areas
- disclosure behavior

where application complexity justifies it.

These preferences may become part of Workspace state (D-139).

## Visual expression

Disclosure may use Sonata Expression mechanisms to communicate hierarchy and state.

It should not rely solely on animation, color or shape to indicate expanded/collapsed state.

## Complexity principle

Sonata targets a wide complexity range (D-057, Principle 19), including:

- simple applications
- productivity software
- creative tools
- professional data applications
- enterprise applications
- engineering/CAD environments

Disclosure should organize complexity rather than suppress it.

## Complex creative/professional software

Applications with substantial toolsets may expose many simultaneously available capabilities.

Examples include:

- creative applications
- audio applications
- notation/editing software
- design tools
- engineering software
- development environments

Sonata does not require such applications to hide their capabilities behind excessive disclosure (D-057).

Instead, it should provide:

- composition
- persistent panels
- collapsible regions
- workspaces
- customization
- command/search surfaces
- contextual actions
- appropriate hierarchy

to make complexity manageable.

## Principle

> **Complexity should be organized, not hidden.** (D-057)

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Disclosure) for what remains open: exact Accordion anatomy, single-open vs multiple-open defaults, exact nesting heuristics, expandable-row height behavior, menu overflow rules, submenu presentation, the context-menu touch equivalent, disclosure animation timings, and workspace-persistence details.
