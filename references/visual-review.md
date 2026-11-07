# Visual review and quality gates

Use this reference before delivery, especially when the user reports a visual defect or asks for “polish.” Review the rendered interface at real CSS viewport sizes; source inspection alone cannot prove visual quality.

## Capture representative states

Review the smallest supported mobile width, a common phone, tablet transition, and wide desktop. Useful starting points are 360, 390, 768, 1024, and 1440 CSS px. Add widths where a title wraps, a grid changes, or a sticky bar collides.

For each affected screen, inspect:

- Initial view and the full target section, including content below the fold.
- Long Persian title, multiline body, long chip, mixed Latin/Persian name, and number-plus-unit.
- The actual active tab/filter and its inactive state.
- Sticky state after scrolling, anchor destination, and the final content above fixed bottom navigation.
- Empty, loading, error, selected, disabled, and expanded states when they exist.
- Keyboard focus and touch-target behavior for changed controls.

Use screenshots at actual viewport dimensions, not a scaled desktop window. When screenshots and the user's live browser differ, confirm the URL, viewport, locale, stored state, and build served by that tab.

## Inspect layout evidence

When a screenshot symptom is ambiguous, inspect computed styles or element bounds:

- `scrollWidth` versus `clientWidth` for horizontal overflow.
- `getBoundingClientRect()` for edge alignment and overlap.
- Grid/flex tracks, `min-width`, `gap`, padding, and intrinsic image dimensions.
- Computed foreground/background colors and text contrast.
- Actual sticky offset, containing block, and ancestor overflow.
- Rendered font family, weight, size, and line-height for Persian glyphs.

If a layout is wrong at one width, search all media queries and selector overrides affecting that component. Do not patch only the latest rule while an older narrow breakpoint still wins.

## Review checklist

### Hierarchy and composition

- [ ] The primary content and next action are obvious in a quick scan.
- [ ] Page, section, and card titles have distinct roles.
- [ ] The image, text, details, and action balance each other; no large area is empty without purpose.
- [ ] Related labels and values stay together; repeated items align consistently.
- [ ] One primary action is visually dominant per relevant group.
- [ ] Repeated semantic values use the same color and formatting across views.

### RTL and content

- [ ] Reading edge, visual order, DOM order, and keyboard order agree.
- [ ] Mixed Persian/Latin content, punctuation, numerals, and units render correctly.
- [ ] No meaningful text is clipped, ellipsized, or broken inside words.
- [ ] Multiline body copy uses the reading edge; centered copy is limited to appropriate short groups.

### Responsive and interaction

- [ ] No horizontal overflow at the narrowest supported width.
- [ ] Tabs and controls remain readable and touchable on mobile.
- [ ] Grid columns change before text becomes cramped.
- [ ] Sticky bars do not clip, stack over one another, or hide destination headings.
- [ ] Fixed bottom UI does not cover the final action or content.
- [ ] Focus, selected, disabled, and error states are still visible.

### Color and type

- [ ] Text and meaningful controls have sufficient contrast on their real surfaces.
- [ ] Secondary text remains readable.
- [ ] Font fallback, Persian glyphs, numerals, and line-height are checked in the browser.
- [ ] Semantic colors have explicit roles; color is not the only meaning cue.

## Delivery report

State which routes/components changed, which viewport sizes and states were visually inspected, which project checks were actually run, and any limitation that remains. Do not use “looks good” as evidence when the relevant screen was not opened.
