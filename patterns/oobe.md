# Pattern — OOBE / First Use

Decided: OOBE/First Use as an official pattern, interactive demonstration over lengthy text, first-use scope (meaningful defaults over full-app coverage), non-forced onboarding with skip/dismiss/replay, and OOBE-level personalization (D-198–D-203). See [`onboarding.md`](onboarding.md) for the broader system OOBE sits inside.

## Purpose

Sonata provides an official pattern for first-use and initial application orientation (D-198).

OOBE (Out-of-Box Experience) and First Use are opportunities to:

- orient the user
- demonstrate important capabilities
- establish useful defaults
- expose meaningful personalization
- explain unfamiliar workflows
- ask decisions that materially affect behavior

## First-use is not necessarily a wizard

Sonata does not require a traditional sequential setup wizard.

First-use experiences may be:

- graphical
- interactive
- demonstrative
- exploratory
- contextual
- compact
- multi-stage when justified

## Demonstration

The interface may demonstrate real functionality rather than merely describe it (D-199, Principle 65).

Examples:

```text
Show a feature
    ↓
Let the user interact
    ↓
Explain the effect
    ↓
Offer to configure it
```

## Meaningful decisions

First Use may ask the user to choose behavior that has lasting consequences.

Examples:

- default workflow
- preferred layout
- visual theme
- interaction mode
- file handling behavior
- project organization
- synchronization preferences

Do not ask configuration questions merely because the system can expose them.

## Progressive introduction

Complex applications should not require users to understand the entire application during first launch (D-200).

First Use may:

- introduce the essentials
- demonstrate advanced capabilities
- defer optional configuration
- provide contextual rediscovery later

## Discovery

Important capabilities may be introduced visually.

Examples:

- interactive demonstrations
- annotated controls
- sample projects
- guided exploration
- feature previews

## Existing users

OOBE/First Use should not repeatedly interrupt experienced users without justification (D-202).

Applications may provide:

- skip
- dismiss
- replay
- help/revisit

where appropriate.

## Defaults

First Use may establish sensible application defaults.

Defaults should be:

- safe
- reversible where practical
- understandable
- aligned with Sonata principles

## Personalization

OOBE may expose high-value customization such as (D-203):

- theme
- accent
- typography
- scale
- density
- workspace setup

The experience should not overwhelm the user with every possible token.

## Complex applications

Professional applications may use First Use to introduce:

- workspace concepts
- tool panels
- command/search systems
- complex workflows
- non-obvious interaction mechanisms

The goal is not to hide complexity. The goal is to make complexity approachable (Principle 42, D-057).

## Contextual first-use

Applications may defer demonstration of advanced functionality until the relevant context appears (D-201).

First Use therefore includes both:

- initial onboarding
- contextual first-use education

## Writing

First-use content follows Sonata's Foundation writing principles.

Use:

- direct language
- concise explanations
- visible consequences
- concrete demonstrations

Avoid:

- marketing copy disguised as instructions
- unnecessary jargon
- long walls of text
- explanations of functionality that the interface can demonstrate directly

## Accessibility

OOBE must support:

- keyboard navigation
- assistive technology
- text scaling
- reduced motion
- high contrast
- reduced transparency
- touch where applicable

Interactive demonstrations must have non-motion alternatives.

## Platform adaptation

OOBE may follow platform conventions for first-run experiences while preserving Sonata's principles.

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## OOBE & Onboarding) for what remains open: exact OOBE flow anatomy, replay/help re-entry UI, and contextual-onboarding trigger rules.
