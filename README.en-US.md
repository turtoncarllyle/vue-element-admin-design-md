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

It does not implement routing, permissions, state management, APIs, or business logic, but records source contracts that visual work must preserve. It distinguishes Source, Dependency, Guidance, and Unverified rules so demonstration flows are not mistaken for production capabilities.

## Design Context

This repository targets admin applications rather than corporate sites, marketing landing pages, or editorial portals. The specification focuses on:

- the dark sidebar, top utility bar, breadcrumb, and multi-tab application shell
- data lists, filters, complex tables, pagination, and bulk actions
- create, edit, query, login, and settings forms
- dashboard metrics, charts, cards, and task information
- dialogs, the custom right-side settings panel, uploads, messages, confirmations, and error feedback
- role permission trees, rich-text/Markdown/JSON editors, drag tools, and import/export

The goal is to preserve vue-element-admin's clear hierarchy, moderate information density, and repeated-action efficiency instead of applying an unrelated dashboard style.

## Supported Versions

| vue-element-admin version | Canonical English | Simplified Chinese | GitHub Release |
| --- | --- | --- | --- |
| `4.3.1` | [DESIGN.md](versions/4.3.1/DESIGN.md) | [DESIGN.zh-CN.md](versions/4.3.1/DESIGN.zh-CN.md) | [v4.3.1](https://github.com/turtoncarllyle/vue-element-admin-design-md/releases/tag/v4.3.1) |

The English `DESIGN.md` is the canonical ecosystem-compatible edition. The Chinese edition follows the same sections, tokens, and rules.

The [4.3.1 audit and update record](versions/4.3.1/AUDIT.md) contains concrete findings, source evidence, a coverage matrix, and acceptance limits. The audit is maintained in Chinese; either language edition of the design specification remains independently usable.

## Usage

1. Select the directory matching your project's vue-element-admin version.
2. Use either language edition as the project's root `DESIGN.md`; compare and merge an existing customized specification instead of overwriting it.
3. Read the full specification, select the actual list/editor/dashboard/login pattern, and inspect its source and business contracts.
4. Require the agent to distinguish source facts from guidance and report recovery behavior and verification limits; static document checks are not UI acceptance.

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
Read DESIGN.md in full. Use vue-element-admin 4.3.1, Vue 2.6.10 and Element UI 2.13.2. Choose the actual source page pattern and distinguish Source, Dependency, Guidance and Unverified rules. Preserve routing, permissions, APIs, stores and data formats; include loading, empty, failure/retry, validation and duplicate-submit handling. Check 991/992/993px, themes, long text and overlays. Report static checks separately from browser verification; do not upgrade dependencies or treat demo saves as persistence.
```

## Coverage

- Visual theme, design principles, and information density
- Color roles, type hierarchy, spacing, radii, shadows, and motion
- The `210px` sidebar, `50px` navbar, `34px` tags view, and content area
- Element UI 2.13.2 buttons, forms, tables, pagination, dialogs, and feedback states
- Dashboard cards, charts, filter toolbars, login page, and mobile sidebar
- Agent-facing Do / Don't rules and ready-to-use prompts
- Runtime theme injection and third-party boundaries, navigation/cache/settings contracts, actual page patterns and recovery
- Accessibility/content rules, icon/image licensing boundaries and explicit unverified items

## Version and Source

The current specification is based on the [vue-element-admin 4.3.1](https://github.com/PanJiaChen/vue-element-admin/tree/4.3.1) source. Its primary visual sources are `src\styles`, `src\layout`, `src\views\dashboard`, `src\views\login`, and the Element UI `2.13.2` theme tokens compiled by the project.

All 307 reference files match pinned upstream commit [`f6d8204`](https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380). The checkout has no lockfile or installed dependency tree; Element UI rules were separately checked against the npm `2.13.2` source package. This does not verify full dependency resolution or runtime behavior.

The supplied [vue-element-admin v4.0.0](https://github.com/PanJiaChen/vue-element-admin/tree/v4.0.0) is historical context only; its full source was not compared in this update and no `4.0.0` specification was added. The supported version remains `4.3.1`.

### Updates Within the Same Version

- Upstream version, directory and document `version` remain `4.3.1`. This update improves the specification without upgrading frontend dependencies or introducing a document revision number.
- The version directory on `main` is maintained content; Git commits and the `updated` date track changes.
- Preserve the original `v4.3.1` tag and launch attachments `DESIGN.md` and `DESIGN.zh-CN.md`. The tag and GitHub-generated Source code archives remain the launch snapshot, not current `main`.
- Append notes, update-commit links and date-labelled attachments to the same [v4.3.1 Release](https://github.com/turtoncarllyle/vue-element-admin-design-md/releases/tag/v4.3.1) without replacing historical assets. A date identifies a file snapshot, not a new version.
- For reproducibility, select a full SHA from the file's commit history and replace `main` in the download URL with it. The `main` download links above follow ongoing same-version updates.

This update performs document and static source checks only. It does not install dependencies, start the legacy frontend, capture screenshots or claim UI acceptance. Runtime theme cascade, keyboard/focus, mobile rendering, external assets and backend behavior remain subject to the audit's verification checklist.

This is an independently maintained design-system document. It is not affiliated with or endorsed by vue-element-admin, Element UI, or Google Stitch. Related project names and marks belong to their respective owners.

## License

Original documentation in this repository is released under the [MIT License](LICENSE). Use of vue-element-admin and Element UI remains subject to their respective open-source licenses.
