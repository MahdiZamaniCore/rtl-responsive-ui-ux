---
name: rtl-responsive-ui-ux
description: Design, implement, or review responsive right-to-left interfaces, especially Persian UI. Use for RTL layout, mixed-script content, component hierarchy, mobile/desktop behavior, or visual QA.
---

# RTL Responsive UI/UX

Create interfaces whose hierarchy, content, and interactions remain clear in RTL at every supported viewport. Treat visual design as a system of deliberate decisions, not a collection of decorative CSS changes.

## Workflow

1. **Understand the user and task.** Identify the primary user goal, the information they need first, the main action, important secondary actions, and the states the screen must handle. Preserve the user's requested visual direction and product behavior.
2. **Inspect the actual project.** Read applicable project instructions. Find existing tokens, components, routes, localization rules, and responsive styles. Open the live page when possible; inspect the entire target section and the adjacent content that affects its spacing or sticky behavior. Extend an existing system when it fits; do not create a parallel one without a reason.
3. **Set the hierarchy before styling.** Map content into page, section, component, and supporting-text levels. Choose a layout that fits the information density and scan path. Decide what should align, wrap, move, collapse, scroll, or stick at each viewport.
4. **Use semantic tokens and reusable patterns.** Keep brand-specific colors configurable. Give repeated semantic values the same source of truth. Reuse a component when its meaning and behavior are the same; use explicit variants when only the layout differs.
5. **Implement with logical direction.** Keep visual order, reading order, and keyboard order coherent. Prefer logical start/end and block/inline concepts over physical left/right rules. Preserve complete meaningful text and the user's data.
6. **Review the rendered result.** Use real CSS viewport sizes, including narrow mobile, a common mobile width, tablet, and desktop. Check the whole section, long text, sticky/fixed edges, and interactive states. Read computed layout/color values when a visual symptom is ambiguous. Fix connected issues found in the same user journey.
7. **Report concretely.** Summarize what changed, the viewports and states actually reviewed, and any remaining limitation. Never claim a viewport or state was verified if it was not.

## Decision rules

- The content and user task determine the layout. Centering everything, making every card equal-height, or copying a reference component wholesale are not default solutions.
- In horizontal Persian RTL, inline-start is normally the right edge. Keep headings, body copy, values, and actions aligned to a deliberate reading edge. Center short labels or metrics only when their grouping stays visually obvious.
- Meaningful text, titles, values, and actions must remain visible. Change the available width, layout, or copy before clipping or breaking words.
- A strong color, filled surface, outline, icon, or shadow changes visual weight and perceived interactivity. Use each with a clear role; do not add decoration to compensate for weak hierarchy.
- Use a shared component when content semantics and interaction match. Keep visual variants explicit and small. Never make two different actions look equally primary by accident.
- Treat reference screenshots and project documentation as design evidence. Extract the underlying rule, then check whether the new product has the same content and constraints. Do not turn one brand's exact palette, radii, or breakpoints into universal rules.
- Distinguish hard requirements (complete content, correct direction, keyboard access, no hidden controls) from tunable recommendations (spacing, radii, density, number of columns).

## Read the relevant reference

- For analysis and design decisions: [decision-workflow.md](references/decision-workflow.md)
- For Persian, Arabic, Hebrew, or mixed-direction content: [rtl-and-bidi.md](references/rtl-and-bidi.md)
- For breakpoint behavior, sticky elements, and mobile/desktop patterns: [responsive-layouts.md](references/responsive-layouts.md)
- For color, typography, spacing, and surface tokens: [visual-tokens-and-type.md](references/visual-tokens-and-type.md)
- For reusable UI structures: [component-patterns.md](references/component-patterns.md)
- To translate the same design intent across web and native stacks: [platform-mapping.md](references/platform-mapping.md)
- For wireframe schematics: [schematics.md](references/schematics.md)
- For interaction and accessibility: [accessibility-and-interaction.md](references/accessibility-and-interaction.md)
- Before delivery or when visual polish is requested: [visual-review.md](references/visual-review.md)
- To learn from a real Persian product redesign without inheriting its brand: [case-notes.md](references/case-notes.md)
