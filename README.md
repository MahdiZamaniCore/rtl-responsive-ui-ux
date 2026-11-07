# RTL Responsive UI/UX Skill

**A practical, framework-independent design and implementation guide for Persian and other right-to-left interfaces.**

این بسته برای مدل‌ها و طراحانی نوشته شده که می‌خواهند رابط‌های RTL را با سلسله‌مراتب روشن، متن خوانا، چیدمان واکنش‌گرا و اجزای هماهنگ بسازند. قواعد از تجربه‌های واقعی بازطراحی یک محصول فارسی استخراج شده‌اند؛ تصمیم‌های مربوط به رنگ و برند آن محصول به‌عنوان قانون عمومی کپی نشده‌اند.

The skill focuses on repeatable decisions: what to inspect, how to choose a layout, how to handle RTL and mixed-direction text, and how to review the result at real screen sizes. It is intentionally independent of React, CSS, Tailwind, Flutter, SwiftUI, or any one product category.

## Contents

- `SKILL.md` — concise entry point and workflow.
- `references/` — detailed RTL, responsive, visual-system, component, accessibility, schematic, and QA guidance.
- `agents/openai.yaml` — optional UI metadata for compatible OpenAI skill surfaces. It is not required by other agents.

## Use it

For an agent that supports folder-based skills, install the full `rtl-responsive-ui-ux/` folder using that agent's documented skill location. For an agent that accepts project instructions but has no skill loader, add `SKILL.md` to its instruction context and keep the referenced `references/` files accessible. For a one-off task, provide `SKILL.md` and only the references relevant to that page.

Keep the core guidance intact when adapting it to another agent. Platform-specific metadata may change; the design principles and review criteria should remain linked to the same references.

## Core rule

Treat examples as evidence, not universal values. Preserve a project's brand and existing design language when appropriate. Choose dimensions and tokens from the content, interaction, accessibility needs, and real viewport—not by copying a screenshot's pixels blindly.

## Publishing

This skill is published in [MahdiZamaniCore/rtl-responsive-ui-ux](https://github.com/MahdiZamaniCore/rtl-responsive-ui-ux) under the [MIT License](LICENSE). You may use, copy, modify, and redistribute it under the license terms; include the copyright and permission notice with copies or substantial portions.

When sharing or adapting the skill, keep `SKILL.md` together with the referenced `references/` directory. If you adapt it for another agent, retain the original attribution and make any platform-specific changes in that agent's own metadata or installation instructions.
