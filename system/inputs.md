# System — Inputs

## Status

Decided: semantic input taxonomy, validation model, required-field semantics, Checkbox/Switch distinction, Slider capability, shared cross-class model, density integration, complex-form patterns, autocomplete, and the consolidated-taxonomy principle (D-042–D-053). Open: exact field anatomy, tokens, and other specifics (see Open questions).

## Purpose

Inputs are interactive controls that capture, edit or select data. Sonata's core input components are opinionated and provide preferred solutions for common interaction problems, consistent with the general catalog decision (D-032).

## Semantic input distinction

Sonata distinguishes semantic input roles (D-042):

- Text Field
- Search Field
- Select
- Combobox
- Command Input / Command Palette
- specialized inputs where genuinely required

Similar appearance does not imply identical semantics — but these roles share a common, highly capable text-input infrastructure rather than being built as unrelated one-off controls:

```text
Shared text-input infrastructure
        │
        ├── Plain text
        ├── Validated text
        ├── Suggestions
        ├── Autocomplete
        ├── Search
        └── Contextual commands
                │
                ▼
        semantic component
```

A text field may expose composable capabilities — clearing, validation, suggestions, autocomplete, search, contextual actions — without becoming semantically equivalent to a command palette.

## Unified command/search surfaces

Sonata permits a unified application-level search/command surface when the workflow justifies it, but treats it as intentionally scarce global interaction infrastructure (D-043):

```text
Application-wide command/search surface
        ↓
typically 0–1
exceptionally 2
```

Sonata does not mandate a universal "super input." This constraint applies to global surfaces, not to ordinary or contextual text/search fields — see [Global command/search surface restraint](../patterns/command-palette.md#global-commandsearch-surface-restraint) in the Command Palette pattern.

## Select and Combobox

Select and Combobox are both official Sonata components (D-044). The choice depends on the nature, size and interaction requirements of the option set:

- small, stable option sets should not be forced into searchable controls
- large or difficult-to-scan option sets may justify Combobox/autocomplete behavior

## Validation

Validation should occur as early as practical without unnecessarily interrupting the user's task (D-045):

```text
During editing
    ↓
avoid premature interruption

After meaningful interaction / leaving field
    ↓
validate known problems

Submission / completion
    ↓
validate remaining requirements
```

Validation timing may adapt to the nature of the input and platform context, but the underlying principle remains shared across Desktop and Mobile.

## Required fields

Sonata explicitly communicates required fields rather than relying on widespread use of optional markers (D-046). Required status must be understandable through labels and accessible semantics.

## Checkbox and Switch

Checkbox represents selection or participation in a set/form context. Switch represents an on/off setting or capability whose state is persistent and immediately meaningful (D-047). They must not be treated as interchangeable visual variants.

## Slider

Sonata Slider supports, where appropriate (D-048):

- single-value selection
- range selection
- stepped values
- keyboard interaction
- direct numeric entry or equivalent precise input when useful

A given UI may expose only the capabilities relevant to that particular slider.

## Mobile and Desktop

Input components preserve the same semantic model across Desktop and Mobile (D-049; see D-015). Mobile implementations may adapt:

- target size
- spacing
- arrangement
- presentation
- interaction affordances

without unnecessarily creating separate semantic components.

## Density and customization

Inputs participate in Sonata's global density system (D-050; see D-012, D-020, [`spacing-density.md`](../expression/spacing-density.md)). Changing density must update related dimensions and spacing consistently across input components rather than independently shrinking individual fields.

Input appearance otherwise inherits from Sonata semantic tokens (D-036) rather than exposing arbitrary per-field styling. Customization is exposed in coordinated packages — density, interface scale, typography, shape, spacing, contrast — rather than requiring users to configure individual fields independently.

## Complex forms

Sonata treats complex forms as compositional patterns rather than simple sequences of label/input pairs (D-051). Official patterns should support, where appropriate:

- sections
- groups
- multi-column layouts
- dependencies
- progressive disclosure
- summaries
- validation
- navigation
- persistent completion actions
- responsive transformation

The goal is to reduce the cognitive and interaction burden of long or complex forms.

## Autocomplete

Autocomplete/typeahead is an official Sonata capability (D-052), appropriate when users need to find or select from a potentially large set of values. It should not be used merely because it is technically available.

## Consolidated input model

Sonata prefers a small number of semantically meaningful input components with composable behavior over a proliferation of narrowly specialized input variants (D-053; see D-035). A difference should produce a distinct component only when it represents a distinct semantic interaction; otherwise, additional behavior should be provided compositionally.

This preference for a small semantic taxonomy does not imply low capability — a common input foundation may support a rich set of composable behaviors while preserving semantic distinctions at the component and interaction level.

## Self-explanatory inputs

Inputs follow Sonata's general self-explanatory-interface priority (D-038): they should communicate what is expected, what format is accepted, current state, errors, constraints and available suggestions through the interface wherever practical. Users should not need external documentation to understand ordinary input requirements.

## Component taxonomy

```text
Inputs
├── Text Field
├── Text Area
├── Search Field
├── Number Input
├── Select
├── Combobox
├── Checkbox
├── Radio
├── Switch
├── Slider
├── Date / Time inputs
├── File / Upload input
└── Color input
```

This list remains extensible (D-031). The taxonomy should be kept semantically small even when the underlying behavior is sophisticated (D-053).

## Open questions

See [`../governance/open-questions.md`](../governance/open-questions.md) (## Inputs) for what remains open: exact field anatomy, label/help/error placement, inline vs block validation presentation, floating labels or not, field sizing, exact input tokens, Select anatomy, Combobox interaction, autocomplete result presentation, mobile keyboard behavior, date/time input strategy, file-upload patterns, and exact form-layout patterns.
