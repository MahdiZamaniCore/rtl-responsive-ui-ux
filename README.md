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

## Install

This repository is a portable Agent Skill. Install the complete skill folder so `SKILL.md` and its `references/` remain together.

### One command for several coding agents

Install Node.js 22.20 or later, open a terminal in your project, then run:

```sh
npx skills add MahdiZamaniCore/rtl-responsive-ui-ux --skill rtl-responsive-ui-ux --agent codex --agent claude-code --agent gemini-cli --agent cursor --agent opencode --agent github-copilot
```

This installs the skill in the current project. Add `--global` to install it for your user account instead. Remove any `--agent` options for tools you do not use, or choose another supported agent ID from the [supported agents list](https://github.com/vercel-labs/skills/blob/main/docs/agents.md). The installer supports many more clients; its target list changes over time.

### DeepSeek Harness

DeepSeek Harness can discover skills in project `.agents/skills/` and `.dsh/skills/`, and in the user folders `~/.agents/skills/` and `~/.dsh/skills/`. The easiest project-level install is:

```sh
npx skills add MahdiZamaniCore/rtl-responsive-ui-ux --skill rtl-responsive-ui-ux --agent codex
```

Here, `--agent codex` selects the shared `.agents/skills/` folder; it does **not** require Codex to be installed. For a user-level install, add `--global`:

```sh
npx skills add MahdiZamaniCore/rtl-responsive-ui-ux --skill rtl-responsive-ui-ux --agent codex --global
```

DeepSeek Harness scans both shared paths above, so the same skill can be used by multiple agents. To install manually, clone this repository as `rtl-responsive-ui-ux` inside one of those skill directories. Keep the whole folder, including `references/`. After installing, start or refresh the Harness session and confirm that `rtl-responsive-ui-ux` appears in its available skills. See the [DeepSeek Harness filesystem skill provider](https://github.com/deepseek-ai/deepseek-harness/blob/master/packages/skill/skill-filesystem/README.md) for its discovery paths.

The DeepSeek model by itself (for example, a plain chat/API session) does not scan local skill folders. The host application must support loading Agent Skills; otherwise, provide `SKILL.md` and the needed reference files in that host's context.

### Gemini CLI

Gemini CLI can install the repository directly. For the current user:

```sh
gemini skills install https://github.com/MahdiZamaniCore/rtl-responsive-ui-ux --scope user
```

Use `--scope workspace` to install it for the current project. Then run `/skills list` inside Gemini CLI to confirm discovery. See the [Gemini CLI Agent Skills guide](https://geminicli.com/docs/cli/skills/).

For other compatible agents, use the one-command installer above or install the complete folder in the skill directory documented by that agent. The [npx skills CLI](https://github.com/vercel-labs/skills) and its [agent path matrix](https://github.com/vercel-labs/skills/blob/main/docs/agents.md) list current options.

## Core rule

Treat examples as evidence, not universal values. Preserve a project's brand and existing design language when appropriate. Choose dimensions and tokens from the content, interaction, accessibility needs, and real viewport—not by copying a screenshot's pixels blindly.

## Publishing

This skill is published in [MahdiZamaniCore/rtl-responsive-ui-ux](https://github.com/MahdiZamaniCore/rtl-responsive-ui-ux) under the [MIT License](LICENSE). You may use, copy, modify, and redistribute it under the license terms; include the copyright and permission notice with copies or substantial portions.

When sharing or adapting the skill, keep `SKILL.md` together with the referenced `references/` directory. If you adapt it for another agent, retain the original attribution and make any platform-specific changes in that agent's own metadata or installation instructions.
