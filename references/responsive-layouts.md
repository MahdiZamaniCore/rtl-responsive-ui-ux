# Responsive layouts and sticky behavior

Use this reference when the screen must work on mobile, tablet, desktop, or when content is clipped by a header, tab strip, or fixed navigation.

## Review bands, not magic breakpoints

Breakpoints are a means of changing layout when content stops fitting. Start by reviewing representative CSS widths, then move the transition to where the real content needs it.

| Review width | What it reveals |
|---:|---|
| 360px | Narrow mobile, long Persian words, action wrapping |
| 390–430px | Common phone widths, tab distribution, card density |
| 768px | Tablet transition and two-column feasibility |
| 1024px | Compact desktop/tablet landscape, sidebars, sticky offsets |
| 1280–1440px | Wide desktop alignment, max-content width, empty gaps |

These are review samples, not universal CSS breakpoints. Also inspect any width near a visible wrap or overflow failure.

## Choose behavior by content

| Pattern | Wide view | Mid-width | Mobile |
|---|---|---|---|
| Independent cards | 3–4 columns when card content stays readable | 2 columns | 1 column or a deliberately horizontal scroller |
| Image plus copy | Two balanced tracks or compact media-object | Reduce image or stack if copy becomes narrow | Media-object for scanning; stack for a true hero |
| Sidebar plus main task | Sidebar and main panel | Collapse or make sidebar compact | Put task first; expose filters/details on demand |
| Related tabs | Inline tabs with clear active state | Wrap or scroll if labels need space | Balanced grid or accessible scroll row; avoid tiny compressed tabs |
| Metrics | One aligned strip or grid | 2+1 or 3 columns according to label length | Compact strip or stacked cards with labels attached to values |
| Multi-action row | Primary and secondary in a clear group | Allow text to wrap before controls collide | Stack only when both remain clearly grouped and comfortably tappable |

Always use `minmax(0, 1fr)` or an equivalent shrinkable track for long content. Give text containers `min-width: 0` where the layout system requires it. Images need a stable aspect ratio and a deliberate crop point; never crop meaningful content accidentally.

## Card height and density

- Let content set the height by default. Fixed heights and large `min-height` values often create dead space when some records contain fewer fields.
- Equal-height cards are useful for direct comparison when they share a row. Anchor the CTA consistently if that improves comparison, while keeping the content above it compact and readable.
- A sparse card should stay visually balanced: reduce unnecessary padding, use a compact variant, or choose a list pattern. Do not add filler copy or stretch a few chips across an empty panel to simulate density.
- When a card has a thumbnail and text, check whether the image carries enough weight. A small image next to a large blank text area can look like a sticker; either enlarge the image, use a hero, or choose a text-led row.

## Sticky and fixed elements

Before making an element sticky, establish that it helps the user's task and that the viewport can support it.

- Measure the actual fixed app-bar height. Use one shared offset token for the sticky element and for anchor/scroll targets.
- Keep sticky elements inside an ancestor that does not create an unintended scroll container; ancestor `overflow` can disable or alter sticky behavior.
- Set an appropriate stacking level and an opaque or sufficiently solid background so scrolled content does not compete with the sticky bar.
- Add `scroll-margin-block-start` or the platform equivalent to section targets so headings are not hidden under the sticky region.
- On mobile, account for browser chrome, notches, safe areas, the on-screen keyboard, and fixed bottom navigation. Reserve content space so the final action is reachable.
- Check the sticky state after scroll as well as at the top. Inspect clipped edges, shadows, adjacent bars, and content that begins under the sticky region.
- A sticky element should not consume so much viewport height that the main task becomes a narrow scroll window.

## Overflow and text resilience

- Avoid `100vw` inside a padded parent when it introduces horizontal scroll; prefer the parent's available inline size.
- Check long translated labels, large text settings, browser zoom, and real data—not only short mock strings.
- Let chip/tag rows wrap as groups. Do not shrink controls or make labels illegible just to preserve one line.
- Avoid relying on a single `max-width` fix if a grid track or intrinsic minimum is the real source of overflow.
