# Case notes: lessons from a Persian product interface

This is a set of reusable lessons from one real Persian café application. It is evidence for the design decisions, not a universal café theme or a fixed token sheet. A different product should keep its own brand and content model.

## Lessons that generalized

### 1. Give each title a clear level

When a section title and its nested card title had similar size and weight, the page hierarchy disappeared. Give page, section, card, and metadata distinct roles. Check them together in the same viewport; changing one title in isolation can simply move the ambiguity elsewhere.

### 2. Treat palette consistency as data consistency

The same ingredient could appear in Result, Menu, and Barista. Per-page color choices made identical values look like different concepts. A shared semantic palette made each value stable. The transferable lesson is one source of truth for repeated meaning; the actual warm pastel colors remain specific to that brand.

### 3. Remove artificial card height

Several cards had less content than the card height implied, leaving empty areas that weakened the composition. A compact variant was better than stretching the few chips or labels. Equal heights were useful only when comparing a row and aligning its action.

### 4. Keep data attached to its label

Summary metrics had drifted far from their heading and from one another. A bounded grid/strip kept each label adjacent to its value. This applies to measurements, statistics, status, and profile summaries.

### 5. Protect numbered text and separators

Step copy was almost touching its number; a line crossed the marker column. Separate marker and copy into layout tracks, start the divider after the marker, and preserve a visible gap. Around 8–12px was a useful starting point in that product, not a universal constant.

### 6. Do not compress mobile tabs to save a row

Right-aligned, tiny tabs looked cramped and unbalanced. A two-column grid or intentional horizontal scroll preserved tap size and made the active view easier to find. Choose based on tab count and label length.

### 7. Make Persian measurements read naturally

The stored quantity and the user-facing phrase were different concerns. Persian copy should read as number then unit (for example, «۳۰ میلی‌لیتر»), with a direction-isolated run where necessary. Never assume CSS `direction` alone fixes mixed-script ordering.

### 8. Put an action beside the decision it affects

Two unequal learning actions had been stacked below their content, so their relationship and priority were unclear. Group the suggested item with its relevant action, and give the primary action a stronger but singular visual treatment.

### 9. Check sticky elements after scrolling

A tab strip can appear correct at the top and clip under a fixed header once it sticks. Measure the actual header, use a shared offset, and make the destination heading clear the sticky region.

### 10. Empty states need a visual anchor and a useful next step

A bare informational sentence looked unfinished when no recommendation existed. A small contextual icon, one neutral explanation, and a clear next action made the state feel intentional without implying a result.

## Use these notes carefully

- Keep the principle; re-evaluate the implementation for the new content and brand.
- Do not make every card a pastel chip panel or every action a filled warm CTA.
- Do not center all content to “balance” it. Multiline reading copy usually needs a stable reading edge.
- Do not expand a task into unrelated pages. Inspect adjacent content only where it affects the target flow.
