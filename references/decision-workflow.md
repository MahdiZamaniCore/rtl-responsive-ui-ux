# Design decision workflow

Use this reference when a task is broad, a screenshot shows several connected problems, or the request names a visual symptom without specifying the implementation.

## Decision priority

Resolve competing choices in this order:

1. The user's goal, content meaning, and task scope.
2. Content completeness, accessibility, and correct interaction.
3. Existing product conventions, shared components, and brand tokens.
4. Responsive clarity and visual consistency across the journey.
5. Aesthetic preference and optional polish.

Do not let a screenshot, example, or one past fix override the user's current request or a stronger project convention.

## From request to layout

### Starting a new product

When no codebase or visual system exists yet, define the design contract before producing a large set of screens:

1. Clarify the target users, product goal, most common journey, and highest-impact decision.
2. List the real content and actions for one representative screen. Do not invent detailed domain rules to make a mockup feel complete.
3. Establish a small brand-neutral token structure, then fill it with the chosen brand colors and typography. Name tokens by role rather than by hue.
4. Choose one representative page that exercises the hardest layout needs (long text, images, filters, or summary data). Design its mobile and desktop states together.
5. Validate that page's hierarchy, RTL, content wrapping, and interaction states. Only then extract components and expand to similar routes.
6. Document which decisions are invariants, which are defaults, and which are product-specific. This makes later AI changes less likely to turn an example into a global rule.

Avoid generating a full component library before a real page establishes what the components need to do. Avoid implementing only a wide desktop mockup and treating mobile as a smaller version afterward.

### 1. Identify the job of the screen

Write down, briefly:

- Who is using the screen and what they came to do.
- What they must notice first.
- What information supports the decision.
- What is the primary action, and which actions are secondary.
- What states exist: loading, empty, error, disabled, selected, expanded, saved, or success.

If the task does not give enough information, inspect the page and existing flows. Ask only when a decision materially changes the product and cannot be inferred.

### 2. Inspect before changing

- Read applicable repository instructions and design notes.
- Find the source of truth for colors, typography, cards, spacing, and data formatting.
- Inspect the current page at the state named by the user; include nearby sections, sticky bars, and fixed navigation.
- Find all responsive rules affecting the target selectors. Older narrow breakpoints can silently override newer styles.
- Check whether a similar component already exists and whether it has the same semantics, not merely a similar shape.

### 3. Make a small information map

Describe the hierarchy before choosing CSS:

```text
Page title
  Section purpose
    Main content / comparison
      Supporting details
    Primary action
    Secondary or optional information
```

Keep one clear reading path. Related values belong together. A control should sit close to the content it changes. Avoid repeating a product name or description when the page already states it clearly.

### 4. Choose a layout from the content

- Use a **media-object** row when an image identifies an item and compact comparison matters.
- Use a **hero** when the image is a major part of the decision; give it enough area to carry real visual weight.
- Use a **list** when users compare many items by text or values.
- Use a **grid** when items are independent and have similar scan priority.
- Use a **side panel** only when it remains useful at the available height and does not steal the reading edge.
- Use **tabs** for mutually exclusive related views, not to hide unrelated tasks.
- Use **disclosure** for optional detail; do not style a noninteractive label as a button.

For RTL, label alignment using inline-start/end. Do not infer a layout from “left” and “right” in a screenshot without checking the page direction.

### 5. Balance hierarchy and density

- A title should outrank its section labels and data badges through more than one subtle change. Use a deliberate size/weight/contrast step.
- Whitespace should separate groups or support scanning. Empty space at the bottom of a card is not useful merely because cards were assigned a fixed height.
- Equal-height cards can help comparison, but use content-driven height unless aligned actions or a shared grid row give equal height a real purpose.
- If a row needs aligned CTAs, reserve the flexible space in a deliberate content row; do not set an arbitrary `min-height` that makes every card feel hollow.
- Multiline explanatory copy normally follows the reading edge. Center alignment is for short labels, compact metrics, or a deliberately centered composition.
- Prefer one strong action per visual block. Secondary actions should be clearly quieter or grouped with the item they affect.

### 6. Reuse components deliberately

Reuse one component when its semantics, content contract, and interaction are the same. Use a named variant when the same content has a different density or placement. Keep domain-specific fields out of generic visual primitives. For repeated semantic values—such as an ingredient, status, or category—use one palette and formatting source across pages.

### 7. Turn subjective feedback into observable checks

Translate “too empty,” “doesn't align,” “low contrast,” or “not focused” into things that can be seen or measured:

| Feedback | Inspect |
|---|---|
| Looks empty | Card content height, unused area, image/text weight, action anchoring |
| Hard to scan | Heading hierarchy, grouping, line length, alignment edge |
| Colors clash | Semantic color roles, saturation, repeated values across components |
| Text is unclear | Contrast, font size/weight, line-height, clipping, script/font rendering |
| Misaligned | Shared inline edge, centers of value and label groups, grid tracks |
| Mobile feels cramped | Tap area, tab distribution, wrapping, fixed-edge collisions |
| Sticky content is cut off | Actual app-bar height, sticky inset, ancestor overflow, scroll target offset |

Fix the root layout or token rule when a symptom repeats. Avoid accumulating isolated overrides for one screenshot.
