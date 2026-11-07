# Accessibility and interaction details

Use this reference whenever a visual change affects controls, text contrast, focus, motion, or content access.

## Semantic controls

- Use a button for an action, a link for navigation, a tab for switching a tab panel, and a disclosure control for expandable content. Styling does not change semantics.
- Ensure accessible names describe the result of an icon-only action. Hide decorative icons from assistive technology.
- Keep DOM order aligned with the visual reading sequence. Avoid using CSS to create a visual order that differs from keyboard navigation.
- Use headings in a meaningful hierarchy; do not select a heading level solely because its default font matches the mockup.
- Associate form labels, descriptions, and validation messages with their controls. State errors in text as well as color.

## Keyboard, focus, and touch

- Every interactive element must be reachable and usable with keyboard input.
- Provide a visible focus indicator that works on every surface and remains distinguishable from hover and selected states.
- Keep touch targets comfortably large. Use 44×44 CSS px as a practical design target for primary mobile controls when space allows; preserve enough separation between adjacent targets.
- Do not make tiny text or a decorative icon the only hit area for an important action.
- When opening a dialog, menu, or disclosure, manage focus and make the close/return path clear.

## Contrast, motion, and non-color cues

- Verify text and meaningful UI graphics against their actual background in normal, hover, selected, disabled, and focus states.
- Do not communicate selected, error, success, or category using hue alone. Pair color with label, icon, shape, or pattern.
- Keep disabled controls distinguishable from normal text while making their disabled status clear.
- Respect reduced-motion preferences. Animation should explain state or guide attention, not delay access to content.
- Check that zoom and enlarged text do not hide actions, overlap fixed navigation, or clip headings.

## Content and language access

- Do not truncate information needed to choose, understand, or complete an action.
- Keep instructions and validation messages near the relevant control.
- Preserve the correct language and direction metadata for mixed-language content.
- Use meaningful alternative text for images that convey information. Do not repeat adjacent text in alt text when it adds no information.
