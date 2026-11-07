# Component and page patterns

Use these patterns as starting structures. Keep the information model and interaction clear, then adapt the implementation to the project's component library.

## Page and section headings

- A page title names the current task or destination. A section heading names the group below it. Do not give both the same size and weight.
- Use an optional eyebrow for category/context, with lower emphasis than the title.
- Keep the heading and its explanatory sentence visually grouped. Do not put a decoration or empty badge between them unless it carries meaning.
- Let heading blocks wrap naturally on mobile. Do not clip or force a single line for long Persian titles.

## Content card

```text
┌──────────────────────────────────────────────┐
│ context / status                   (optional) │
│ item title                                    │
│ short reason or useful summary                │
│                                              │
│ inset details: values, chips, or facts        │
│                                              │
│ primary action                secondary link │
└──────────────────────────────────────────────┘
```

- Keep the item identity easy to find before its metadata.
- Place the description near the title. Put related attributes in one clearly named group.
- Use the inset surface for a meaningful sub-group. Avoid a card inside a panel inside another panel.
- Use content-driven height. Align bottom actions across a row only when that improves comparison, and do not fill the remaining area with stretched labels.
- If a thumbnail supports identification, use a stable ratio and a deliberate object position. Keep the text on the reading edge.

## Comparison and recommendation cards

Make repeated cards comparable: keep title placement, description width, metadata labels, value formatting, and action placement consistent. Vary content without varying the meaning of colors or icons.

- Use a card grid for separate candidates that benefit from side-by-side scanning.
- Use a compact media-object row when the user is scanning a long list.
- Use a larger hero card only for a primary recommendation or focal item.
- For unequal descriptions, let the card content expand naturally. Keep a shared CTA row if necessary; consider a compact list variant when cards become too tall.
- Do not use identical artwork sizes if it makes an unimportant image dominate the text. Conversely, avoid tiny “sticker” images beside broad blank space.

## Chips, badges, and values

- A chip is best for a short attribute, selected filter, or compact token. Long explanatory phrases usually need normal text.
- Distinguish interactive chips from informational tags through focus/hover/pressed states and semantics.
- Keep chip color by semantic value, not by card position. Unknown values use an intentional neutral.
- Let groups wrap at narrow widths; keep each label intact where practical.
- Attach a number and its label as one group. In RTL, verify the visual reading order, especially where Latin digits or units appear.

## Tabs and segmented controls

- Use tabs for related views of the same entity. Use navigation for destinations and filters for changing the visible set.
- Keep tab labels readable and touch targets comfortable. On mobile, distribute a small number of tabs in a balanced grid, or use a clearly indicated horizontal scroll region. Do not shrink every tab to fit a single row.
- Make the active tab apparent through more than color alone (shape, underline, weight, or selected semantics).
- If tabs stick while scrolling, leave enough top offset below the app bar and keep the destination heading visible after selection.

## Numbered steps and timelines

- Give numbers a dedicated fixed-width track or badge.
- Keep 8–12px of visible space between the number column and the text as a useful starting point; adjust for type size and density.
- Start row dividers after the number track or within the copy area so they do not cross a badge or timeline marker.
- Use adequate block spacing between a preface and the first step. Distinguish introductory notes from actionable steps through grouping and typography, not only color.

## Summary metrics

- Keep each label attached to its value. Put the group in an aligned strip/grid, not at opposite ends of an oversized panel.
- For three metrics, use three equal columns when each label fits. On mobile, switch to a compact grid or stack rather than allowing labels to drift away from values.
- Center compact metric groups if that creates a clear unit. Keep longer explanations aligned to the reading edge.
- Use consistent number formatting and unit direction.

## CTA groups

- Identify one primary action per visual region. Give it the strongest filled treatment only when it is the obvious next step.
- Make the secondary action quieter (outline, text, or a clearly separate control) and keep its click target usable.
- Place a CTA beside the item or skill it affects when that makes the relationship clearer. Two unequal actions stacked without grouping make a weak action hierarchy.
- On mobile, stack actions only if the group remains compact and the primary action is still obvious. Otherwise use a full-width primary action and a nearby text/outline secondary action.
- Use action text that states the outcome. Do not use an icon or “more” label as the only clue when the action has a meaningful consequence.

## Empty, loading, and error states

- Explain what is happening or why the set is empty in one short, neutral sentence.
- Use a restrained icon or illustration to give the state a visual anchor. The visual must remain secondary to the message and should not imply a result that was not found.
- Show the most useful next step. Keep retry, edit, and navigation actions visually distinct and ordered by likelihood.
- Make the same state valid across all causes (no input, no match, network failure) or provide distinct copy where the cause changes the user's next action.
- Do not show a large blank panel with a tiny message stranded in its center unless the empty state is deliberately designed as a focused landing state.

## Image behavior

- Decide whether the image is content or decoration. Content images need an appropriate alternative; decorative images should not add redundant screen-reader content.
- Choose `contain` for illustrations/product renderings that must remain whole; use `cover` only when cropping is safe.
- Inspect the top and bottom crop at the narrowest and widest supported ratios. Keep the subject and focal point visible.
- A background image, transparent PNG, and square preview can have very different visual weight. Inspect the actual asset, not only its CSS box.
