# RTL, Persian text, and bidirectional content

Use this reference when any part of the interface is written right-to-left or combines RTL text with Latin text, numbers, units, identifiers, or punctuation.

## Establish direction semantically

- Set the document language and base direction on the appropriate root or page region, such as `lang="fa" dir="rtl"` for Persian.
- Let nested regions declare a different language or direction when their content requires it.
- Prefer CSS logical properties: `padding-inline`, `margin-inline`, `inset-inline-start`, `border-inline-start`, `text-align: start`, and `scroll-margin-block-start`.
- Avoid spreading `left`/`right` rules through a component when the behavior is really start/end. Use physical coordinates only for genuinely physical decoration or media positioning.
- Keep DOM reading order, visible order, and keyboard order coherent. CSS `order` or reversed flex direction can create a screen-reader sequence that disagrees with what sighted users see.

```css
.card { padding-inline: var(--card-padding); }
.card__copy { min-width: 0; text-align: start; }
.divider { border-inline-start: 1px solid var(--border-subtle); }
```

## Isolate mixed-direction runs

Mixed direction is a text-layout problem, not a reason to flip an entire component. Use semantic isolation (`<bdi>`, `dir`, or the platform's equivalent) around the smallest run that has a different direction.

```html
<p lang="fa" dir="rtl">
  چای دارچین <bdi dir="ltr">Cinnamon Tea</bdi>
</p>
<p lang="fa" dir="rtl">
  مقدار: <bdi dir="rtl">۳۰ میلی‌لیتر</bdi>
</p>
<p lang="fa" dir="rtl">
  شناسه: <bdi dir="ltr">HC-2048</bdi>
</p>
```

- A Latin product name, URL, email address, code, or phone number often needs LTR treatment.
- A Persian quantity such as «۳۰ میلی‌لیتر» must remain readable as number then unit. Do not force every `<bdi>` to LTR.
- Choose Persian or Latin digits consistently with the locale and the surrounding UI. Formatting the number and isolating its direction are separate decisions.
- For user-entered mixed text, use `dir="auto"` or the framework's direction-aware equivalent when the content is unknown at render time.
- Punctuation can appear to jump across direction boundaries. Isolate the phrase and punctuation together when the punctuation belongs to that phrase.

## Preserve RTL scan and interaction

- Keep section headings, descriptions, values, and related actions aligned to the same logical reading edge unless a deliberate composition requires otherwise.
- In horizontal Persian layouts, inline-start is normally the right. Put supporting imagery at inline-end when it preserves the copy's reading edge; let a full-width image be a purposeful hero.
- Do not center multiline explanatory copy simply to make the panel symmetrical. Center short counts, badges, or labels only when the group remains easy to parse.
- Keep DOM tab order natural. An icon's visual location should not cause a keyboard user to encounter controls in a confusing order.
- Place a number badge and its text in distinct layout tracks. Leave a visible gap; start a divider after the badge column rather than running it through the number.

## Directional icon rules

- Mirror icons whose meaning encodes direction or progression (back, forward, breadcrumb chevron) when the locale requires it.
- Do not mirror symmetric or object icons (cup, leaf, search, settings) without a semantic reason.
- Use labels or accessible names for icon-only controls. An icon's direction must reinforce the actual action, not merely the text direction.

## Persian typography details

- Choose a Persian-capable font with the required weights actually loaded. Check bold weights and numerals in the real browser; fallback fonts can change wrapping and vertical alignment.
- Preserve ZWNJ (half-space) and correct Persian characters. Do not normalize content in a way that changes the intended word or punctuation.
- Keep units adjacent to their number as one semantic value, with a nonbreaking relationship only where it improves reading without causing overflow.
- Do not break a word in the middle to rescue a narrow column. Let the phrase wrap between words, or change the column, font size, or layout.
- Use locale-aware number formatting for counts, prices, and measurements; do not assume the operating system locale matches the page locale.
