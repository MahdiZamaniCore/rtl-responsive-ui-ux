# Map design intent to a platform

The design system is expressed in semantic roles and behavior. Translate those roles to the current framework's native primitives instead of copying CSS values or implementation details literally.

## Keep the design contract platform-neutral

Before implementation, define:

- Page and component hierarchy.
- Inline-start/end reading edge and content order.
- Responsive or adaptive states and the condition that triggers each change.
- Semantic token roles: text, surface, border, action, status, and focus.
- Interaction contract: action, selected state, disclosure, navigation, keyboard/focus, and accessibility name.
- Content behavior: wrapping, mixed-direction values, image crop, loading, empty, and error states.

These decisions should survive a change from web to native UI, or from one design library to another.

## Direction-aware primitives

| Intent | Web / CSS | Flutter | React Native | SwiftUI | Jetpack Compose |
|---|---|---|---|---|---|
| Start/end padding | Logical `padding-inline-start/end` | Directional `EdgeInsetsDirectional` | `start` / `end` style props where supported; verify library/version behavior | `leading` / `trailing` | `start` / `end` in layout modifiers |
| Start alignment | `text-align: start`, logical grid/flex placement | Directional alignment and `TextAlign.start` | Text alignment and layout direction from locale | Leading alignment in the active layout direction | `TextAlign.Start` and `LayoutDirection` |
| Base direction | `lang` + `dir` | `Directionality` | Locale + `I18nManager` behavior | Environment layout direction | `LocalLayoutDirection` |
| Safe edges | Safe-area CSS/env insets | `SafeArea` / view insets | Safe-area context or native insets | Safe-area layout guides | Window insets |

Names and APIs evolve. Confirm them in the target platform and framework version before implementation. The table is a translation aid, not a substitute for current API documentation.

## Platform-specific translation rules

### Web

- Use document `lang` and `dir`, logical CSS properties, native semantic controls, and actual CSS viewport units for responsive review.
- Check both DOM order and visual order. Use `<bdi>` or nested direction metadata for mixed-script runs.
- Prefer Grid/Flex relationships over absolute coordinates for content layout. Reserve absolute positioning for overlays or decoration.

### Flutter

- Use the app's locale and `Directionality`; choose directional padding/alignment so the same component adapts to RTL and LTR.
- Review text scale and device insets separately from width breakpoints. Keep long labels wrapping within their constraints.
- Verify behavior on representative device sizes; layout constraints and text scaling can differ from browser assumptions.

### React Native

- Confirm how the current React Native version and platform apply locale direction to flex, start/end styles, gestures, and images.
- Prefer direction-aware styles and native safe-area handling. Do not rely on a globally reversed row to fix all RTL semantics.
- Check iOS and Android if both are supported; font metrics, safe areas, and navigation bars can differ.

### SwiftUI

- Use semantic leading/trailing alignment and the environment's layout direction. Keep action meaning separate from a visual arrow's direction.
- Respect Dynamic Type and safe-area behavior. A fixed frame that matched one screenshot can clip at a larger accessibility text size.

### Jetpack Compose / native Android

- Use start/end and the active `LayoutDirection`, not hard-coded left/right padding for ordinary content.
- Use density-independent sizing for geometry and scalable text units for typography. Respect font scaling and system insets.
- Test the actual RTL locale because a mirrored container does not automatically make every icon, gesture, and semantic order correct.

### Design tools and component libraries

- Keep token names and component variants semantic in the design file. Record responsive behavior and direction behavior in component properties or documentation.
- Confirm that auto-layout, constraints, and direction mirroring preserve text reading order; a mirrored frame is not a complete RTL design.
- Treat library defaults as implementation details. Check whether default typography, button height, shadows, and breakpoints fit the product's visual contract.

## Units and density

Do not convert 16 CSS px to 16 dp or 16 pt mechanically. Preserve the intended relative hierarchy, readable text size, touch target, and spacing rhythm in the platform's unit model. Respect user text scaling and zoom. Use design tokens to express roles and allow platform adapters to map them to appropriate units.

## Verification by platform

- Web: browser screenshots at real CSS widths, computed styles, keyboard navigation, zoom, and sticky/fixed edge review.
- Native: simulator/emulator or device screenshots at representative screen sizes, text scaling, safe-area/navigation bars, and both supported OSes.
- Shared requirement: verify the same critical states—default, focused, selected, disabled, empty, loading, and error—using the interaction contract, not only appearance.
