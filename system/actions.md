# System — Actions

## Status

Decided: action role hierarchy, self-explanatory-interface priority, destructive-action safeguards, and Split Button/Menu Button as official components (D-037–D-041). Open: exact tokens/dimensions, size scale, emphasis mappings, and other specifics (see Open questions).

## Purpose

Actions are interactive controls that cause an intentional operation.

Sonata provides a coherent action vocabulary while allowing applications to extend it when workflow complexity requires additional abstractions (D-031).

## Action hierarchy

Core semantic action roles (D-037):

- Primary
- Secondary
- Tertiary
- Quiet
- Destructive

These are semantic roles, not independent visual component variants.

### Primary

The principal action for the current context.

Primary actions should normally receive stronger visual salience than secondary actions when the distinction is meaningful (D-005).

### Secondary

An important but non-primary action.

### Tertiary

A lower-priority action that remains directly available.

### Quiet

A deliberately restrained action whose visual prominence is low because the action is secondary, contextual or infrequent.

Quiet actions remain discoverable and accessible.

### Destructive

An action that causes irreversible, harmful or potentially consequential change.

Destructive actions must communicate their consequence clearly before activation (D-039).

Applications should avoid destructive actions when safer alternatives are practical.

## Semantic role vs visual emphasis

Action role and visual emphasis are separate dimensions.

```text
role = primary
emphasis = strong
```

is valid.

```text
role = secondary
emphasis = neutral
```

is also valid.

Expression may increase or decrease salience according to context without changing semantic role.

## Primary-action emphasis

Sonata permits substantial visual differentiation for primary actions when increased salience improves discoverability or task completion (D-005).

Possible mechanisms include:

- size
- contrast
- accent color
- shape
- whitespace
- position within an established structure
- motion
- expressive composition

The action must remain in the structural position determined by the Foundation layer.

This follows the Sonata principle:

> Structure determines where. Expression determines how strongly.

Material 3 Expressive is a reference for this principle: its guidance treats stronger visual emphasis and expressive shape/motion as tools for improving usability and engagement, not decoration for its own sake. See [`../references/material-expressive.md`](../references/material-expressive.md).

## Button

Button is the default component for direct actions — an official, opinionated Core Component (D-032) that should solve ordinary action problems without requiring application-specific customization.

Applications should normally prefer the Sonata Button over locally invented button treatments for common actions.

## Complexity boundary

Button must not become a universal abstraction for every possible action (D-033).

When additional behavior would require excessive variants, ambiguous semantics or an increasingly complex API, the solution should graduate to another abstraction. For Button specifically, the preferred progression is:

```text
Button
  ↓
Specialized component
  ↓
Compound component
  ↓
Pattern
  ↓
Application-specific component
```

This is a Button-specific instance of the general catalog graduation ladder in [`components.md`](components.md); "Specialized component" here names an intermediate step within the Core Component tier, not a new catalog-wide tier of its own.

Complexity is a legitimate reason to introduce a new abstraction (Principle 16). The goal is not to minimize the number of components — it is to maintain semantic clarity and consistency.

## Icon Button

Icon Button represents a directly actionable control whose icon has a sufficiently established and recognizable meaning, subject to the iconography semantics contract (D-030): icon alone only when meaning is sufficiently obvious; otherwise prefer a textual label.

Icon-only actions should be used when:

- the symbol is mainstream enough to be recognized
- the action is sufficiently unambiguous
- the surrounding context supports interpretation

Tooltips, contextual labels or other discoverability mechanisms may supplement icon-only actions. They should not excuse an unnecessarily obscure icon.

## Button content

Buttons may use:

- label only
- icon + label
- label + icon
- icon only

The arrangement should be selected according to semantic and platform context.

The existence of an icon must not force decorative symmetry.

## Interface explains itself

Sonata strongly prefers self-explanatory interfaces (D-038).

Where a control might otherwise require documentation, the interface should first attempt to communicate meaning through:

- explicit labels
- established iconography
- contextual text
- visible state
- hover feedback
- focus feedback
- tooltips
- shortcut hints
- previews
- confirmation messaging

Documentation remains valid, but the UI should not outsource basic discoverability to documentation when the information can reasonably be communicated in the interface itself.

## Destructive actions

Destructive actions should (D-039):

- communicate that a consequential operation is about to occur
- use semantically appropriate visual treatment
- avoid accidental activation
- provide confirmation where the consequence warrants it
- provide recovery or undo when practical

The strongest visual treatment should be reserved for genuinely consequential operations. Destructive styling must not be used merely to make a button visually prominent.

## Full-width

Buttons may occupy the full available width when required by composition.

`full-width` is a compositional property, not a visual variant.

This is particularly useful for:

- mobile actions
- narrow layouts
- prominent primary actions
- forms
- edge-to-edge workflows

## Size

Button supports a semantic size scale:

- Small
- Medium
- Large

The actual dimensions are resolved through Sonata tokens. Size does not constitute an independent visual personality.

## Shape

Button consumes the semantic Sonata control shape (D-036). Applications and users should modify button geometry through the shape system rather than per-button arbitrary styling.

## Loading and asynchronous action

Buttons may transition between semantic states:

```text
Idle
  ↓
Loading
  ↓
Success
```

or:

```text
Idle
  ↓
Loading
  ↓
Error
```

Where appropriate, Motion and Shape may cooperate to morph between these states (D-029).

The transition must preserve:

- action identity
- state recognition
- spatial continuity
- accessibility

## Mobile

Buttons retain the same semantic model across interaction classes.

Mobile implementations may adapt:

- minimum target size
- width
- spacing
- label treatment
- composition

to support touch. The Button does not become a different semantic component on Mobile.

## Desktop

Desktop implementations may additionally support:

- hover
- keyboard activation
- shortcut hints
- pointer-specific feedback
- context-sensitive actions

These capabilities must not create a dependency on pointer input.

## Platform adaptation

The Sonata Button should remain semantically equivalent across platforms (D-034). Pixel identity is not required.

Platform-native rendering and interaction conventions may be used where they preserve Sonata's semantic and visual intent.

## Menu Button

Menu Button is an official Sonata component (D-041) combining an action with access to related actions.

It should be used when:

- one action is the primary operation
- related alternatives belong naturally in a menu

The primary action should remain obvious.

## Split Button

Split Button is an official Sonata component (D-040) combining:

- a primary action
- a related menu of alternative actions

Its visual relationship should communicate that the two regions belong to one action family without making their semantic roles ambiguous.

Material 3 Expressive provides Split Button as an expressive component and is a useful reference for combining related action regions through shape and motion.

## Toggle

Toggle represents an action whose state persists.

The visual treatment must clearly distinguish:

- off
- on
- disabled
- focused
- pressed where applicable

The toggle's semantics must remain comprehensible without relying solely on color.

## Toggle Group

Toggle Group represents a set of related mutually exclusive or multi-select choices where the selection itself is the persistent state.

The selection model must be clear from semantics and state presentation.

## Action groups

Related actions may be grouped when grouping improves comprehension.

Groups should preserve action hierarchy. A group must not visually equalize actions that have materially different semantic importance.

## Shortcuts

Actions may expose keyboard shortcuts where appropriate; see [`../patterns/shortcuts.md`](../patterns/shortcuts.md).

Shortcut presentation should be integrated into the action's discoverability model rather than exist as separate undocumented knowledge.

## Action labels

Action labels should follow Sonata's Foundation writing principles — see [`../foundation/writing.md`](../foundation/writing.md).

Prefer labels that communicate what will happen. Avoid vague labels such as "OK", "Continue" or "Submit" when a more specific action name is practical.

## Extensibility

Applications may introduce additional action components when (D-031):

- the interaction is genuinely distinct
- the semantics cannot be represented clearly by an existing component
- forcing the behavior into an existing component would produce inconsistency
- the new abstraction represents a reusable pattern

Application-specific components remain compatible with Sonata when they preserve Foundation, System and Expression principles.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Actions) for what remains open: exact Button tokens/dimensions, size scale, emphasis mappings, Link behavior, destructive-action confirmation thresholds, shortcut display conventions, Menu Button/Split Button anatomy, Toggle vs Switch distinction, and action-group layout rules.
