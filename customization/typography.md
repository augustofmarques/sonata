# Customization — Typography

Typography is a high-priority customization category because it affects readability and accessibility.

Possible controls:

- text size
- interface scale
- typeface
- line spacing
- advanced typography

The application decides how much of this surface to expose.

## Text scale profiles

Official text-scale profiles: Small, Standard, Large, Extra Large, with **Standard** as the default (see [`../expression/typography.md`](../expression/typography.md), D-220).

Text Scale and Interface Scale are independent controls — Text Scale changes typography only, Interface Scale changes typography together with control dimensions, icon sizing and relevant spacing. Density is independent from both: changing density does not globally shrink or grow type.

## Large text must reflow, not clip

When a user selects a larger text scale, applications must adapt layout rather than shrinking text to fit: prefer reflow (wrap → increase container → increase region height → progressive disclosure → alternate composition) over clipping or truncation. See [`../expression/typography.md`](../expression/typography.md) (D-220).

## Typography presets

Applications may expose curated typography presets (a coherent UI/Display/Mono family set, numeric behavior and locale fallback together, not just a body-font swap) and, where supported, a custom font (D-212). See [`../expression/typography.md`](../expression/typography.md) for the Sonata default preset and the typography contract alternative font systems must satisfy.
