# System — Token Resolution Model

## Status

Decided: the three-axis structure below, and the combined resolution order. Open: several precedence and generation details, listed at the end of this file.

## Why this file exists

Three earlier documents each described a "layered pipeline," and each answered a different question without saying how it combines with the others:

- `tokens.md` — Raw values → Foundation/system tokens → Semantic tokens → Component tokens → Rendered UI
- `theming.md` — Sonata defaults → Application theme → User preferences → Accessibility constraints → Component state
- `expression/color.md` — Source Color → Tonal/perceptual generation → Sonata palette scale → Semantic roles → Components

None of these is wrong, but read side by side they look like three competing models of "how a value is produced," which is not implementable as-is: a skill or a renderer needs one deterministic resolution order. This file is that single authoritative model. The three files above now each describe one axis and defer here for the full picture (see D-024).

## The three axes

Producing any rendered value in Sonata means resolving three independent questions, in this order:

### Axis A — Abstraction (what kind of token is this)

```text
Raw / generated values
    ↓
Foundation / System tokens
    ↓
Semantic tokens
    ↓
Component tokens
    ↓
Rendered UI
```

Full detail: [`tokens.md`](tokens.md). This axis says nothing about *where a value comes from* — only how specific/reusable it is, and which layer a component is allowed to consume directly (semantic and component tokens, per `tokens.md`, not raw or foundation values).

### Axis B — Precedence (which source wins)

```text
Sonata specification defaults
    ↓
Application theme
    ↓
User customization
    ↓
Accessibility constraints
```

Full detail: [`theming.md`](theming.md). Each step may override the value produced by the step above it. Accessibility constraints occupy the last position — this is the structural basis for "accessibility has final authority" (Principle 7, D-018): it is not a special-cased exception, it is simply the last writer in the cascade.

Domain-specific **generation algorithms** — such as color's Source Color → Tonal generation → Palette scale → Semantic roles pipeline (see [`expression/color.md`](../expression/color.md)) — execute *inside* the "Sonata specification defaults" and, when an application supplies its own source input (e.g. a brand source color), the "Application theme" step. They are not a fourth, competing pipeline; they are how a source input at one precedence step becomes usable semantic-role values. Every domain that supports generated (rather than fixed) values should document its own generation algorithm the same way color does, at the step of Axis B where it runs.

### Axis C — State (which variant renders right now)

```text
default · hover · focus · pressed · active · selected ·
disabled · loading · error · success · warning ·
read-only · dragged · expanded · collapsed
```

Full detail: [`components.md`](components.md). Applied last, after Axis A + B have produced a resolved base value for a component token. State selects among variants of that already-resolved value; it does not re-run precedence.

## Combined resolution order

To resolve any value the system needs to render:

1. **Classify (Axis A):** identify which semantic/component token governs the requested value.
2. **Resolve (Axis B):** walk the precedence chain low to high — spec default (via the domain's generation algorithm where one exists) → application theme → user customization → accessibility constraint. Accessibility may clamp or force the value regardless of what any earlier step set.
3. **Select (Axis C):** apply the interaction-state variant appropriate to the current state to the value produced in step 2.

`Rendered value = StateSelect_C( PrecedenceResolve_B( AbstractionClassify_A(request) ) )`

## Open decisions

- Exact conflict rule when an application theme marks a token non-overridable but user customization still targets it — does "capability is global, exposure is contextual" (Principle 9) mean the application can lock a token out of Axis B entirely, or only hide the control for it?
- Which domains beyond color require a documented generation algorithm at the Axis B "spec defaults" step (shape, motion and spacing are current candidates — see their own Open Decisions sections).
- Whether Axis C state variants are themselves independently themeable tokens (subject to their own Axis B precedence) or fixed transforms applied to the Axis B result.
- How accessibility constraints on Axis B (reduced motion, high contrast) interact with Axis C state transitions — e.g. is a "pressed" motion variant removed under reduced motion, or replaced with a static equivalent?
- Public vs private tokens, and product-specific token extension rules (affects what a product is allowed to insert at the "Application theme" step of Axis B).
