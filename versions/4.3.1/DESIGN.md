---
version: "4.3.1"
name: "vue-element-admin-design-system"
description: >-
  A source-derived design specification for vue-element-admin 4.3.1 and its
  Element UI 2.13.2 component layer. It defines the pragmatic, desktop-first
  visual language used by the application so AI coding agents can extend admin
  interfaces without replacing the existing Vue 2 or Element UI conventions.
colors:
  primary: "#1890ff"
  primary-sidebar: "#409eff"
  success: "#13ce66"
  warning: "#ffba00"
  danger: "#ff4949"
  info: "#909399"
  tags-active: "#42b983"
  sidebar: "#304156"
  sidebar-hover: "#263445"
  submenu: "#1f2d3d"
  submenu-hover: "#001528"
  dashboard-canvas: "#f0f2f5"
  surface: "#ffffff"
  text-primary: "#303133"
  text-regular: "#606266"
  text-secondary: "#909399"
  text-placeholder: "#c0c4cc"
  border: "#dcdfe6"
  border-light: "#dfe4ed"
  border-lighter: "#e6ebf5"
typography:
  body:
    fontFamily: "'Helvetica Neue', Helvetica, 'PingFang SC', 'Hiragino Sans GB', 'Microsoft YaHei', Arial, sans-serif"
    fontSize: "14px"
    fontWeight: 400
    lineHeight: "24px"
  heading-large:
    fontSize: "20px"
    fontWeight: 500
    lineHeight: "28px"
  heading:
    fontSize: "18px"
    fontWeight: 500
    lineHeight: "26px"
  subheading:
    fontSize: "16px"
    fontWeight: 500
    lineHeight: "24px"
  small:
    fontSize: "13px"
    fontWeight: 400
    lineHeight: "20px"
  extra-small:
    fontSize: "12px"
    fontWeight: 400
    lineHeight: "18px"
---

# vue-element-admin 4.3.1 Design System

## Overview

This file records the visual system of vue-element-admin 4.3.1 in plain-text Markdown for AI coding agents. It describes what generated admin interfaces should look and feel like. It does not replace the official vue-element-admin or Element UI API documentation and must not be used to invent unsupported component behavior.

The system is pragmatic, desktop-first, and optimized for operational work. Its signature is a deep blue-gray navigation rail, a white utility header, blue action states, restrained gray surfaces, 14px body text, compact medium controls, and clear table-oriented composition. Interfaces should feel established and efficient, not promotional or decorative.

### Core Principles

1. **Extend the existing stack.** Prefer Vue 2 components, Element UI 2.13.2 `el-*` components, existing SVG icons, router metadata, and application helpers.
2. **Preserve the application shell.** Keep the sidebar, navbar, breadcrumb, tags view, and content geometry recognizable.
3. **Optimize repeated operations.** Filters, tables, forms, pagination, and row actions should remain easy to scan and quick to use.
4. **Use hierarchy before decoration.** Establish structure through spacing, white surfaces, thin borders, muted text, and restrained elevation.
5. **Reserve color for state.** Blue marks primary actions and focus; semantic colors communicate status; the deep sidebar anchors navigation.
6. **Adapt, do not redesign.** When modifying an established project, retain its routes, permissions, API contracts, component sizes, and local conventions.

### Source of Truth

Values are derived from the official vue-element-admin `4.3.1` source, particularly `src/styles`, `src/layout`, `src/views/dashboard`, `src/views/login`, and `src/layout/mixin/ResizeHandler.js`. The project imports and compiles Element UI `2.13.2` theme source through `src/styles/element-variables.scss`; those component tokens are part of this specification.

The demo-only `src/assets/custom-theme/index.css` is not the default product theme. Do not use its charcoal primary color as the application baseline. When project code and this document differ, preserve the project's actual code and update composition around it.

## Colors

### Primary and Semantic Colors

| Role | Value | Use |
| --- | --- | --- |
| Primary action | `#1890ff` | Primary buttons, focused fields, links, selected Element UI controls |
| Sidebar active | `#409eff` | Active top-level sidebar item; intentionally distinct from the compiled primary |
| Success | `#13ce66` | Completed, healthy, approved, and positive states |
| Warning | `#ffba00` | Needs attention, pending, risky, or cautionary states |
| Danger | `#ff4949` | Delete, failure, invalid, destructive, and critical states |
| Info | `#909399` | Neutral informational state and secondary status |
| Active page tag | `#42b983` | Current item in the tags view only |

Do not merge `#1890ff`, `#409eff`, and `#42b983` into one generic accent. They identify different layers of the original interface. Use generated lighter primary tints for subtle hover, selection, and current-row surfaces instead of introducing unrelated blues.

### Navigation Colors

| Role | Value | Use |
| --- | --- | --- |
| Sidebar background | `#304156` | Main navigation rail |
| Sidebar hover | `#263445` | Top-level item hover |
| Submenu background | `#1f2d3d` | Nested navigation |
| Submenu hover | `#001528` | Nested item hover |
| Menu text | `#bfcbd9` | Default navigation labels and icons |
| Submenu active text | `#f4f4f5` | Selected nested navigation label |
| Sidebar logo background | `#2b2f3a` | Optional logo band |

Keep navigation dark and continuous from top to bottom. Do not turn each menu item into a detached card or use a light sidebar unless the host project already defines another supported theme.

### Surfaces, Text, and Borders

| Role | Value | Use |
| --- | --- | --- |
| Page / component surface | `#fff` | Navbar, cards, dialogs, forms, tables |
| Dashboard canvas | `#f0f2f5` | Dashboard page background |
| Primary text | `#303133` | Titles and high-emphasis content |
| Regular text | `#606266` | Body copy, form values, standard labels |
| Secondary text | `#909399` | Metadata and supporting copy |
| Placeholder | `#c0c4cc` | Input placeholders and unavailable hints |
| Base border | `#dcdfe6` | Inputs and standard component outlines |
| Light border | `#dfe4ed` | Overridden light border token |
| Lighter border | `#e6ebf5` | Cards, disabled outlines, subtle dividers |
| Table border | `#dfe6ec` | Explicit vue-element-admin table border |
| Row hover | `#f5f7fa` | Table and list hover surface |

Use white as the dominant working surface. Gray backgrounds separate regions; they should not create a monochrome dark dashboard. Keep essential labels at regular or primary text contrast.

### Dashboard Accents

Dashboard metric cards use limited categorical accents: `#40c9c6`, `#36a3f7`, `#f4516c`, and `#34bfa3`. Apply them to an icon or data series, not to every card background. Charts may use richer series colors, but controls and navigation must continue to use the core tokens.

## Typography

### Font Family

Use the application stack:

```css
"Helvetica Neue", Helvetica, "PingFang SC", "Hiragino Sans GB",
"Microsoft YaHei", Arial, sans-serif
```

Use Element UI's icon font for Element controls and the repository's `SvgIcon` system for application icons. Do not substitute text glyphs or unrelated icon styles when an existing icon is available.

### Hierarchy

| Level | Size | Weight | Guidance |
| --- | --- | --- | --- |
| Large page or metric value | `20px` | 500-700 | Important totals or rare top-level headings |
| Dialog / section title | `18px` | 500 | Dialog titles and major section labels |
| Compact heading | `16px` | 500 | Card titles, form sections, dashboard labels |
| Body / control | `14px` | 400 | Default labels, controls, menus, and table content |
| Compact metadata | `13px` | 400 | Pagination and supporting information |
| Small tag / row action | `12px` | 400 | Tags, mini buttons, compact statuses |

Use `24px` as the base text line-height reference. Keep headings compact inside panels. The login title is a context-specific `26px` bold exception; dashboard icons and numeric values may be larger when they communicate data. Never use viewport-scaled type, negative letter spacing, or marketing-scale headings inside the admin shell.

## Layout

### Application Shell

| Region | Dimension | Behavior |
| --- | --- | --- |
| Expanded sidebar | `210px` | Fixed left rail, full viewport height |
| Collapsed sidebar | `54px` | Icons remain visible; labels and submenu arrows hide |
| Navbar | `50px` | White top utility bar |
| Tags view | `34px` | Optional visited-page strip below navbar |
| Main content | `calc(100% - sidebar)` | Left margin follows expanded or collapsed sidebar |
| Standard page padding | `20px` | `.app-container` default |
| Dashboard padding | `32px` | Data overview canvas; reduce internal chart padding on narrower screens |

The navbar, tags view, and main content belong to one continuous workspace. If the header is fixed, its width must update from `calc(100% - 210px)` to `calc(100% - 54px)` when the sidebar collapses. With tags enabled, the content minimum height is `calc(100vh - 84px)`; without tags it is `calc(100vh - 50px)`.

### Grid and Content Composition

Use Element UI's 24-column grid and its responsive props. Common source-derived gutters are `8px` for tightly related panels, `32px` for chart groups, and `40px` for KPI cards. Prefer these patterns:

- filter toolbar, table, and pagination in one vertical workflow
- four KPI cards at `lg=6`, two per row at `xs=12` and `sm=12`
- three chart panels at `lg=8`, stacked at `xs=24` and `sm=24`
- two equal analytical panels at `lg=12`
- related secondary panels as `12 / 6 / 6` at large widths and stacked or paired below

Do not place every section inside an extra outer card. The page itself is a work surface; use cards for bounded data or tool units.

### Spacing

Use a practical 4px-based rhythm with these recurring values:

| Token | Value | Typical use |
| --- | --- | --- |
| `space-1` | `4px` | Tag offsets and very tight icon alignment |
| `space-2` | `8px` | Compact padding, toolbar gaps, chart padding on narrow screens |
| `space-3` | `10px` | Filter spacing and compact vertical gaps |
| `space-4` | `16px` | Card internals, row padding, grouped controls |
| `space-5` | `20px` | Standard page and card padding |
| `space-6` | `24px` | Section separation and notice padding |
| `space-7` | `30px` | Pagination and major form separation |
| `space-8` | `32px` | Dashboard padding and chart separation |
| `space-10` | `40px` | KPI grid gutter |

Keep vertical spacing consistent within a workflow. Avoid large empty hero spacing in list and form pages.

## Elevation

Use shallow, functional elevation:

| Level | Shadow | Use |
| --- | --- | --- |
| Header | `0 1px 4px rgba(0, 21, 41, .08)` | Navbar separation |
| Tags | `0 1px 3px rgba(0,0,0,.12), 0 0 3px rgba(0,0,0,.04)` | Tags-view strip |
| Card | `4px 4px 40px rgba(0,0,0,.05)` | Dashboard metric cards |
| Floating menu | `2px 2px 3px rgba(0,0,0,.3)` | Tags-view context menu |
| Dialog | `0 1px 3px rgba(0,0,0,.3)` | Element UI modal surface |
| Fixed table edge | `0 0 10px rgba(0,0,0,.12)` | Fixed columns only |

Borders should carry most structural separation. Do not apply heavy shadows to every card, table, or form section.

## Shapes

- Use `4px` as the standard control, card, menu, tag, and dialog radius.
- Use `2px` for compact or subtle shapes.
- Use `3px` for pagination controls.
- Use circles only for status dots, icon buttons designed as circles, avatars, and radio controls.
- The navbar avatar uses a source-specific `10px` radius at `40px` square.
- Avoid pill-shaped containers unless using Element UI's explicit round button, tag, switch, or input affordance.
- Avoid large `12px+` radii on ordinary admin cards and panels.

## Components

### Sidebar Navigation

Use existing route metadata and the `SidebarItem` hierarchy. Keep the sidebar `210px` wide, menu text `#bfcbd9`, active top-level text `#409eff`, and nested backgrounds progressively darker. Application SVG icons use a `16px` right gap; submenu icon alignment uses the existing `12px` spacing.

When collapsed to `54px`, center the icon, hide text and arrows, and expose nested menus through Element UI's vertical popup. On mobile, treat the sidebar as an off-canvas drawer with a black `30%` overlay; do not squeeze it into a miniature permanent column.

### Navbar and Breadcrumb

Keep the navbar `50px` high, white, and lightly elevated. The left side holds the hamburger and breadcrumb. The right side holds search, error log, fullscreen, size selection, and the avatar menu; hide nonessential utilities on mobile as the source does.

Right-side icon targets span the full navbar height with `0 8px` padding and an `18px` icon size. Hover uses `rgba(0,0,0,.025)`. Use tooltips for unfamiliar icon-only actions.

### Tags View

The optional tags view is `34px` high. Individual tags are `26px` high with `12px` text, a `1px` border, `0 8px` padding, and `5px` horizontal separation. The active tag uses `#42b983` with white text and an `8px` white status dot.

Preserve middle-click close, close icon, and context-menu behavior when present. Do not restyle visited pages as oversized tabs or card chips.

### Buttons

Use Element UI button variants and sizes before custom CSS.

| Size | Font | Padding | Radius |
| --- | --- | --- | --- |
| Default | `14px` | `12px 20px` | `4px` |
| Medium application default | `14px` | `10px 20px` | `4px` |
| Small | `12px` | `9px 15px` | `3px` |
| Mini | `12px` | `7px 15px` | `3px` |

The app sets Element UI's global size to `medium` unless the user has stored another size. Use `#1890ff` for primary, `#13ce66` for success, `#ffba00` for warning, and `#ff4949` for danger. Button weight is explicitly `400`.

Place one clear primary action per local task group. Keep destructive actions red and require confirmation where data loss is possible. Use icon-only buttons only for familiar tools and provide accessible labels or tooltips.

### Forms and Inputs

Use `el-form`, `el-form-item`, and the matching Element UI controls. The effective application default is medium: `36px` input height, `14px` text, `4px` radius, white fill, and `#dcdfe6` base border. Other supported sizes are default `40px`, small `32px`, and mini `28px`.

- Labels should be concise and consistently aligned within one form.
- Use `#c0c4cc` for placeholders, never as a substitute for labels.
- Focus uses the `#1890ff` primary border.
- Disabled controls retain visible boundaries and communicate state beyond color.
- Validation errors use `#ff4949` next to the affected control.
- Group related fields into sections; use `20-24px` between sections, not decorative cards around every row.
- Preserve native Element UI keyboard, clear, show-password, autocomplete, and validation behavior.

The login screen is a deliberate exception: full-height `#2d3a4b`, a centered form up to `520px` wide, `47px` transparent inputs, light text, and `5px` field-group radius. Do not apply login styling to ordinary admin forms.

### Selection Controls and Switches

Use Element UI checkbox, radio, switch, select, cascader, date, and time components. Checked and focused states use the primary or semantic token supplied by the component. Keep labels at `14px`, checkboxes compact, and switch labels close to the control. Never create a checkbox-shaped button or a text button for a binary setting when the existing control fits.

For selects and date ranges inside filter toolbars, keep widths stable so state changes do not shift neighboring controls. The project explicitly preserves inline-flex date-range layout.

### Filter Toolbars

Place filters directly above the result table. `.filter-container` uses `10px` bottom padding; each `.filter-item` is inline-block, vertically centered, and has `10px` bottom margin. Use medium or small controls, short labels, and predictable search/reset actions.

On narrow screens, allow controls to wrap into multiple rows. Do not force a desktop toolbar to overflow horizontally.

### Tables

Use `el-table` for structured data. Default text is `#606266`, headers use `#909399`, borders use the overridden `#dfe6ec`, and row hover uses the light gray background. Keep headers concise and align numeric data consistently.

- Use selection columns only when bulk actions exist.
- Keep status columns narrow and centered; the project uses `0 10px` status-cell padding.
- Use mini buttons for row actions and a stable action-column width.
- Use `5px` left/right cell padding only in explicitly dense `.small-padding` tables.
- Use tags for compact statuses, not as decoration on every value.
- Preserve loading, empty, error, selection, sorting, and pagination states.
- Avoid horizontal scrolling where a responsive column strategy or detail view can preserve readability.

### Pagination

Place pagination below the table with about `30px` top separation, usually aligned to the right on desktop. Element UI pagination uses `13px` text, `28px` button height, about `35.5px` button width, and `3px` radius. Keep total count, page size, current page, and navigation controls in a consistent order. On narrow screens, wrap or simplify secondary controls without hiding the current page state.

### Cards and Panels

Use `el-card` or a plain white panel for genuinely bounded content. Standard card padding is `20px`, radius `4px`, and a light border. Dashboard KPI cards are `108px` high with restrained `4px 4px 40px rgba(0,0,0,.05)` elevation; the icon block uses `16px` padding and `6px` radius.

Do not nest cards inside cards. Charts usually sit on white surfaces with `16px 16px 0` padding and `32px` bottom separation. Make titles and actions compact so the data remains the focal point.

### Dialogs, Drawers, and Popovers

Use Element UI overlays and preserve focus, close, escape, loading, and confirmation behavior. Dialogs use white surfaces, `18px` titles, `14px` content, `24px` line height, `20px` primary padding, and a shallow shadow. Keep the primary confirmation action last and visually clear.

Use a dialog for short focused work, a drawer for longer contextual editing when already supported, and a full route for complex workflows. Do not place long tables or multi-stage forms inside a small dialog.

### Dropdowns and Context Menus

Dropdowns are compact white floating surfaces. Menu links must fill the item hit area. Context menus use `12px` text, `5px 0` outer padding, `7px 16px` item padding, `4px` radius, and light gray hover. Keep actions ordered from common to destructive and separate destructive actions when appropriate.

### Tabs, Tags, and Status

Use Element UI tabs for alternate views within one page and the tags view for visited routes; do not confuse the two. Standard tags use `12px` text, `4px` radius, and `0 10px` padding. Map business states consistently to success, warning, danger, and info rather than choosing colors ad hoc.

### Alerts, Messages, and Loading

Use Element UI feedback components with their existing semantic colors and icons. Inline validation belongs next to the control; page-level failure belongs near the failed content; transient completion can use a message. Confirm destructive actions before execution. Loading states should preserve container dimensions to prevent layout jumps.

Include intentional empty, no-results, permission-denied, and error states. A blank table body is not a complete state.

### Uploads

Use `el-upload` and preserve its file input, validation, progress, success, failure, retry, and removal behavior. The source's full-width dragger override is `100%` wide and `200px` high. State accepted types and size limits near the control. Do not use a drag area when a compact upload button is more appropriate.

### Dashboard and Charts

Use charts to answer operational questions, not as decoration. Dashboard panels sit on `#f0f2f5` with white chart surfaces. Keep legends, axes, units, comparison periods, loading, empty, and error states legible. Pair color with labels or shapes and keep categorical palettes stable across charts.

Metric cards should present one label, one value, and at most one compact comparison or icon. Avoid promotional copy, oversized illustrations, and decorative gradients.

### Icons

Use repository SVG icons through `SvgIcon` and Element UI icons inside Element controls. Keep stroke/fill treatment consistent within a toolbar. Familiar tools may be icon-only with a tooltip; commands with ambiguous meaning should use icon plus text. Do not manually draw substitute SVGs when a matching local icon exists.

## Responsive Behavior

### Breakpoints

| Boundary | Source behavior |
| --- | --- |
| `< 470px` | Hide the login page's third-party action |
| `< 550px` | Simplify KPI card composition and center the description |
| `< 768px` | Element UI `xs`; stack most content and forms |
| `< 992px` | Application mobile mode; sidebar becomes an off-canvas drawer |
| `>= 992px` | Element UI `md`; multi-column admin layouts may resume |
| `>= 1200px` | Element UI `lg`; full dashboard grid |
| `>= 1920px` | Element UI `xl`; use extra width selectively, not by stretching all forms |

The dashboard reduces chart padding at `1024px` and below. Treat this as a local density adjustment, not a second application-shell breakpoint.

### Mobile Rules

- Remove the main content's left margin.
- Hide the sidebar off-canvas with `translate3d(-210px, 0, 0)` when closed.
- Show a full-page black overlay at `30%` opacity when the sidebar opens.
- Hide nonessential navbar utilities while retaining navigation and the user menu.
- Stack grids and let filter controls wrap.
- Keep essential row actions reachable; move overflow actions into a menu if needed.
- Avoid horizontal page scrolling. Tables may reduce optional columns or expose a detail view.
- Keep touch targets usable even when the visual control is compact.

## Motion

- Border and color transitions: `0.2s` using Element UI's standard easing.
- Sidebar width and main-content offset: `0.28s`.
- Navbar and icon hover background: `0.3s`.
- Tags-view close affordance: `0.3s` with the Element UI cubic-bezier curve.
- Route fade: `0.28s`; route transform and breadcrumb transitions: `0.5s`.
- Dashboard icon hover: `0.38s ease-out`.

Motion should clarify state or spatial change. Respect reduced-motion preferences when adding new animation. Avoid long decorative animation; the demo-only `600ms` custom button and `1.5s` logo fade are exceptions, not defaults.

## Do / Don't

### Do

- Use Element UI 2.13.2 components and the existing Vue 2 patterns.
- Preserve the `210px / 54px` sidebar and `50px + 34px` header geometry.
- Use `#1890ff` for primary application action and `#409eff` for sidebar active state.
- Keep list pages organized as filter toolbar, result table, then pagination.
- Use white working surfaces on a restrained gray canvas.
- Keep typography compact and information easy to scan.
- Add loading, empty, validation, error, disabled, and permission states.
- Verify desktop and mobile layouts around the `992px` shell breakpoint.

### Don't

- Do not migrate to Vue 3, Element Plus, another component library, or a utility framework unless the task explicitly requires it.
- Do not replace the dark sidebar with floating navigation cards.
- Do not use oversized hero headings, marketing copy, decorative illustrations, or immersive landing-page composition in admin screens.
- Do not put every section in a rounded card or nest cards.
- Do not introduce large pill radii, glassmorphism, heavy gradients, or dense shadows.
- Do not use color as the only status signal.
- Do not hide core actions only to make a mobile screenshot look sparse.
- Do not alter routes, permissions, APIs, or state contracts as a side effect of visual work.

## Agent Prompt Guide

### New Page

```text
Read DESIGN.md before coding. Build this as a vue-element-admin 4.3.1 page using Vue 2 and Element UI 2.13.2. Preserve the existing application shell and route/permission conventions. Compose the page as a compact filter toolbar, data surface, and pagination workflow. Use the documented colors, medium control sizing, spacing, states, and responsive behavior. Include loading, empty, error, and disabled states.
```

### Existing Page Revision

```text
Read DESIGN.md and inspect the existing page before editing. Keep its API, router, permission, validation, and store contracts unchanged. Make the smallest UI change that brings the page into the vue-element-admin 4.3.1 visual system. Reuse existing Element UI components and local SVG icons, then verify desktop and sub-992px behavior.
```

### Review Checklist

```text
Review this UI against DESIGN.md. Report deviations in application-shell geometry, token use, component choice, spacing, type hierarchy, table workflow, responsive behavior, accessibility, and state coverage. Distinguish source-backed requirements from optional improvements and do not propose a framework migration.
```

## Known Gaps

- vue-element-admin 4.3.1 is a Vue 2 and Element UI 2.13.2 system. Its visual rules are not a drop-in contract for Vue 3 or Element Plus.
- The source is desktop-first and defines one explicit application mobile threshold at `992px`; individual demo pages add local breakpoints.
- Accessibility tokens, reduced-motion behavior, minimum touch targets, and full keyboard flows are not comprehensively documented in the upstream source. New work should improve them without changing established behavior.
- The repository contains demonstration pages and a demo-only alternate theme. Treat core shell and compiled theme files as stronger evidence than one-off demos.
- Spacing is recurrent rather than formally tokenized upstream. The spacing scale here normalizes observed values; preserve local project conventions where they are more specific.
- The source enables English Element UI locale by default, but the visual system is language-neutral. Allow Chinese and other labels enough width without changing component meaning.
- Charts provide examples, not a complete data-visualization standard. Define units, legends, accessible labels, and series semantics from the product domain.

## Provenance

This specification is an independent, source-derived reference based on the official vue-element-admin `4.3.1` tag and Element UI `2.13.2`. It is not official documentation and does not imply endorsement by vue-element-admin, Element UI, or Google Stitch.
