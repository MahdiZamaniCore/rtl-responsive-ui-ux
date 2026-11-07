# Visual tokens, color, and typography

Use this reference when creating or aligning a visual system. Values below are role examples and starting points. Adapt them to the product's brand, font, density, and accessibility requirements.

## Model tokens by role

Separate semantic role from color value. A component should ask for `text-primary` or `surface-inset`, not invent a hex color.

```text
color
├── text: primary / secondary / muted / inverse / link
├── surface: page / card / inset / selected / disabled
├── border: subtle / default / strong / focus
├── action: primary / secondary / destructive
├── status: success / warning / error / information
└── semantic data: <domain family> → surface + border + ink
```

Keep the three text-bearing semantic colors together:

```js
{ surface: "#E5EEDB", border: "#BED1A5", ink: "#456333" }
```

- Use distinct hue or lightness differences to distinguish neighboring semantic families. Changing saturation alone often makes categories look alike.
- Choose a neutral semantic family for unknown or unclassified values. Pure white should not accidentally imply “missing color.”
- Keep one source of truth for a semantic value across cards and pages. Generate the same tokens in build-time data or central palette code rather than styling each occurrence independently.
- Never rely on color alone: pair it with text, an icon, a marker, or a clear label.
- Keep brand colors configurable. A coffee palette is a case-specific choice, not a default for an unrelated product.

## Contrast and color states

- Use accessible text/background contrast as an acceptance criterion. WCAG 2.2 AA SC 1.4.3 sets 4.5:1 for normal text and 3:1 for large text; review the [W3C explanation of Contrast (Minimum)](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum) and any stricter requirement applicable to the product.
- Check text against the actual final surface, including hover, selected, disabled, tinted, and translucent states. Alpha blending changes the effective color.
- Preserve legibility in focus and selection states. Border-only changes may be insufficient when the border is low contrast or the control is small.
- Keep muted text readable. “Secondary” means lower emphasis, not low opacity that makes information difficult to read.
- Prefer a lighter surface and an adequately dark ink color over darkening a whole panel just to rescue text contrast.
- Use fewer simultaneous accent colors in a component. A primary CTA can carry the strongest saturation while badges and chips use softer semantic surfaces.

## Spacing and surface tokens

Use a consistent spacing scale and choose values by grouping. One adaptable example is 4, 8, 12, 16, 24, 32, and 40px.

- Use the smaller steps within a component and the larger steps between distinct groups or sections.
- Keep repeated cards and panels on a small number of radii. One border radius per surface level is easier to recognize than many near-identical values.
- Define a surface stack: page → card → optional inset panel. Add a nested panel only when it groups information the user understands as a separate unit.
- A border and a subtle surface often separate content more cleanly than multiple shadows. Reserve shadows for elevation, not for every nested group.
- Use a focus ring token that remains visible on every surface; do not treat the ordinary border as the focus indicator.
- A pill radius is appropriate for short tags, chips, or toggles when the shape reinforces the control. It is not a substitute for semantic grouping.

## Typography roles

Define roles first, then map them to a type scale:

| Role | Typical use | Starting range |
|---|---|---:|
| Display / page title | Main task or page identity | 28–40px, responsive |
| Section title | Major content group | 20–28px |
| Card title | Item identity | 16–20px |
| Body | Explanation and instructions | 15–17px |
| Supporting text | Secondary explanation | 13–15px |
| Compact label | Metadata, tag, count | 12–14px; avoid tiny essential text |

These ranges need adjustment for the actual Persian font, viewport, and content. A usable hierarchy is a visible size/weight/contrast step between levels; small differences such as 800 vs 850 may not survive the font rendering.

- Load the weights the design actually uses. Verify real Persian glyphs, digits, punctuation, and line boxes in the selected font.
- Persian body text often needs more line-height than Latin UI text. Tune against multi-line real copy; body text commonly needs around 1.6–1.9, while headings usually need a tighter but non-colliding line box.
- Use a clear weight hierarchy; too many near-identical weights make labels and headings feel equally important.
- Keep multiline paragraphs aligned to inline-start. Center short single-line labels only when the surrounding pattern supports it.
- Keep meaningful text untruncated. Avoid `overflow-wrap: anywhere`, `word-break: break-all`, and line clamping for titles, values, explanations, or actions.
- If text does not fit, adjust the column, copy length, spacing, or responsive layout before reducing it below a comfortable readable size.

## Icons and perceived weight

- Align icon size and stroke/filled style across a component family.
- Give an icon-only action a text alternative and an adequate touch target.
- Compare visual weight by area, contrast, and density, not by font weight alone. An image, filled CTA, badge, and dense paragraph can dominate a layout even when their CSS font values are modest.
- Use one strong focal point per card or panel. Keep supporting labels and decorative icons quieter.
