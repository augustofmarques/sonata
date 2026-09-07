# Adaptive — Mobile Class

Mobile Class prioritizes:

- touch
- focused contexts
- vertical flow
- progressive disclosure
- reduced persistent chrome
- comfortable targets
- explicit hierarchy

Mobile is not a scaled-down desktop layout.

## Navigation

Prefer contextual navigation, bottom navigation, tabs or hierarchical navigation where appropriate. The semantic navigation architecture stays consistent with Desktop even as the presentation changes (D-063) — a desktop Sidebar destination and a mobile navigation destination refer to the same place, reached differently. Mobile should not simply render a compressed desktop sidebar when another mechanism fits the interaction environment better.

Mobile should be particularly careful about deep sequential navigation: prefer progressive disclosure, hierarchical drill-down, contextual navigation, direct navigation or search over unnecessary nested menus (D-058). See [`../system/navigation.md`](../system/navigation.md) for the component catalog.

## Density

Recommended range: Comfortable to Compact. Dense layouts must not compromise touch usability.

## Data display

Mobile should not merely compress desktop tables until unreadable — prefer transformations such as table → list or persistent inspector → detail screen, without discarding important information merely to simplify layout. See [Data Display](../system/data-display.md).

## Customization

Prefer a smaller set of high-value controls such as theme, accent, text scale, interface scale, motion and contrast.
