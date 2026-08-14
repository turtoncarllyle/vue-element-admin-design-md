# vue-element-admin-design-md

[简体中文](README.md) | [English](README.en-US.md)

[![vue-element-admin](https://img.shields.io/badge/vue--element--admin-4.3.1-1890ff)](https://github.com/PanJiaChen/vue-element-admin/tree/4.3.1)
[![DESIGN.md](https://img.shields.io/badge/DESIGN.md-AI%20ready-42b983)](https://stitch.withgoogle.com/docs/design-md/overview/)
[![License](https://img.shields.io/badge/license-MIT-304156)](LICENSE)

A versioned vue-element-admin design-system document for AI coding agents building admin applications.

`DESIGN.md` is a design-system document format introduced by Google Stitch. It records a design system in plain-text Markdown so AI coding agents can generate visually consistent UI. It defines the intended visual result, component states, and responsive behavior; it does not replace the vue-element-admin or Element UI component API documentation.

This repository extracts real colors, typography, dimensions, spacing, radii, shadows, application-shell rules, and interaction states from the official vue-element-admin source and its matching Element UI dependency. Each vue-element-admin version is maintained independently.

## Purpose and Use

`DESIGN.md` turns visual decisions that usually depend on human judgment into context an AI agent can read directly. Pages generated across different tasks and development stages can therefore retain one vue-element-admin visual language.

Use it to:

- establish shared color, type, layout, and component rules before an agent creates an admin page
- keep additions aligned with vue-element-admin 4.3.1 when an agent modifies an existing page
- provide a reviewable visual-consistency baseline for code review and UI acceptance
- select a matching design specification when a project upgrades vue-element-admin

It does not define routing, permissions, state management, APIs, or business logic. Those contracts remain governed by the project and official documentation.

## Design Context

This repository targets admin applications rather than corporate sites, marketing landing pages, or editorial portals. The specification focuses on:

- the dark sidebar, top utility bar, breadcrumb, and multi-tab application shell
- data lists, filters, complex tables, pagination, and bulk actions
- create, edit, query, login, and settings forms
- dashboard metrics, charts, cards, and task information
- dialogs, drawers, uploads, messages, confirmations, and error feedback

The goal is to preserve vue-element-admin's clear hierarchy, moderate information density, and repeated-action efficiency instead of applying an unrelated dashboard style.

## Supported Versions

| vue-element-admin version | Canonical English | Simplified Chinese | GitHub Release |
| --- | --- | --- | --- |
| `4.3.1` | [DESIGN.md](versions/4.3.1/DESIGN.md) | [DESIGN.zh-CN.md](versions/4.3.1/DESIGN.zh-CN.md) | [v4.3.1](https://github.com/turtoncarllyle/vue-element-admin-design-md/releases/tag/v4.3.1) |

The English `DESIGN.md` is the canonical ecosystem-compatible edition. The Chinese edition follows the same sections, tokens, and rules.

## Usage

1. Select the directory matching your project's vue-element-admin version.
2. Download either language edition to the project root and name it `DESIGN.md`.
3. Tell your AI coding agent to follow the file whenever it generates or modifies UI.

Download the canonical English edition with Windows PowerShell:

```powershell
Invoke-WebRequest `
  -Uri "https://raw.githubusercontent.com/turtoncarllyle/vue-element-admin-design-md/main/versions/4.3.1/DESIGN.md" `
  -OutFile ".\DESIGN.md"
```

Download the Simplified Chinese edition:

```powershell
Invoke-WebRequest `
  -Uri "https://raw.githubusercontent.com/turtoncarllyle/vue-element-admin-design-md/main/versions/4.3.1/DESIGN.zh-CN.md" `
  -OutFile ".\DESIGN.md"
```

Example prompt:

```text
Read DESIGN.md in the project root. Implement this admin page using its vue-element-admin 4.3.1 tokens, application shell, component states, and responsive rules. Preserve the existing Vue 2, Element UI, routing, and permission contracts.
```

## Coverage

- Visual theme, design principles, and information density
- Color roles, type hierarchy, spacing, radii, shadows, and motion
- The `210px` sidebar, `50px` navbar, `34px` tags view, and content area
- Element UI 2.13.2 buttons, forms, tables, pagination, dialogs, and feedback states
- Dashboard cards, charts, filter toolbars, login page, and mobile sidebar
- Agent-facing Do / Don't rules and ready-to-use prompts

## Version and Source

The current specification is based on the [vue-element-admin 4.3.1](https://github.com/PanJiaChen/vue-element-admin/tree/4.3.1) source. Its primary visual sources are `src\styles`, `src\layout`, `src\views\dashboard`, `src\views\login`, and the Element UI `2.13.2` theme tokens compiled by the project.

The supplied [vue-element-admin v4.0.0](https://github.com/PanJiaChen/vue-element-admin/tree/v4.0.0) is a historical reference. The repository currently publishes `4.3.1` as its supported specification.

This is an independently maintained design-system document. It is not affiliated with or endorsed by vue-element-admin, Element UI, or Google Stitch. Related project names and marks belong to their respective owners.

## License

Original documentation in this repository is released under the [MIT License](LICENSE). Use of vue-element-admin and Element UI remains subject to their respective open-source licenses.
