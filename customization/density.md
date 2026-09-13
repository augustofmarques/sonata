# Customization — Density

Density is a coordinated presentation preference, not a simple padding toggle.

Official profiles (D-207), with **Balanced** as the Sonata default (D-206):

- Comfortable
- Balanced (default)
- Compact
- Dense

Density may affect spacing, control dimensions, grouping, table row height, navigation density, toolbar density and information exposure. See [`../expression/spacing-density.md`](../expression/spacing-density.md) for the reference spacing scale, the per-class profile availability and how density composes with interface scale.

The application may expose named profiles rather than arbitrary numeric controls — profiles keep the coordinated set of effects above coherent, which a single free-form spacing slider cannot guarantee.

Mobile should generally constrain the densest modes to Comfortable through Compact; Dense is primarily a Desktop and large-Adaptive/Tablet capability (D-208).

Density is independent from Interface Scale and Typography Scale — e.g. Compact + Large Text, or Comfortable + Small Interface Scale, are both valid and must remain usable.
