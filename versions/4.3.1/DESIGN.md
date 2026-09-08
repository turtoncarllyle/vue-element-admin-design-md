---
version: "4.3.1"
updated: "2026-09-08"
upstream-commit: "f6d8204b0b6fbb794ada0c99391b7b85ce976380"
element-ui: "2.13.2"
token-scope: "Compiled baseline; runtime theme overrides require verification"
typography-scope: "Composition guidance, not a global body or heading CSS declaration"
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

This edition targets the official tag `4.3.1` (without a `v`), commit `f6d8204b0b6fbb794ada0c99391b7b85ce976380`. Local reference files were compared with all 307 upstream blobs with no differences. `package.json` pins Vue `2.6.10`, Element UI `2.13.2`, Vue Router `3.0.2`, Vuex `3.1.0`, and ECharts `4.2.1`. There is no lockfile or installed dependency tree in the reference checkout. Element UI behavior below was checked against its integrity-verified npm `2.13.2` source package, not a current Element Plus manual. Transitive dependency resolution and runtime rendering remain unverified. [S1] [E1]

Evidence labels used throughout this file:

| Label | Meaning | Agent action |
| --- | --- | --- |
| Source | Explicit application code, configuration, or demo behavior | Preserve the relevant contract, including documented limitations |
| Dependency | Behavior inherited from Element UI `2.13.2` | Preserve supported props, events, and component behavior |
| Guidance | A proposed rule for generated work, not an upstream implementation claim | Implement deliberately within the task's scope |
| Unverified | Requires a browser, resolved dependency tree, backend, or asset/license evidence | Report the limitation; do not claim acceptance |

Imperatives about new composition, accessibility, complete state handling, and mobile improvements are **Guidance** unless identified as Source or Dependency. Numeric tables describe source or dependency values except the normalized spacing and typography hierarchies, which are guidance.

Source precedence: match the actual host project's version and business contracts first; then inspect component props and local scoped/deep styles, application overrides, and the dependency implementation. CSS still follows specificity, `!important`, injection order, and stacking contexts, not a simplistic file-order rule. `src\main.js` loads Normalize, the compiled `element-variables.scss` theme, then `styles\index.scss`; runtime `ThemePicker` and the `/theme/index` demo can change the result. Frontmatter colors are the **compiled baseline**, not a claim about every runtime pixel. [S2] [S3] [S8]

The demo-only `src\assets\custom-theme\index.css` is a real alternate-theme example, not the default product theme or a complete dark-mode system. Do not use its charcoal primary as the baseline. The historical `v4.0.0` link is context only; this edition makes no compatibility claim for it.

### Reading and Version Selection

Read the matching `versions\4.3.1\DESIGN.md` or `DESIGN.zh-CN.md` in full, then inspect the target page and the evidence links for its module. Both editions carry the same rules. Select the page pattern before coding; do not force a login, editor, or error page into a CRUD table pattern. Keep routes, permissions, data formats, validation, and stores intact.

This is an update within upstream version `4.3.1`, with no new document revision number. `main/versions/4.3.1` contains the maintained specification; `v4.3.1` remains the initial snapshot. Use a full Git commit URL for reproducibility. The same Release distinguishes original attachments from date-labelled updates; a date is not a version number. This file is usable on its own; the companion audit records evidence and acceptance limits.

## Colors

### Primary and Semantic Colors

| Role | Value | Use |
| --- | --- | --- |
| Primary action | `#1890ff` | Compiled primary buttons, focused fields, selected Element UI controls |
| Sidebar active | `#409eff` | Active top-level sidebar item; intentionally distinct from the compiled primary |
| Success | `#13ce66` | Completed, healthy, approved, and positive states |
| Warning | `#ffba00` | Needs attention, pending, risky, or cautionary states |
| Danger | `#ff4949` | Delete, failure, invalid, destructive, and critical states |
| Info | `#909399` | Neutral informational state and secondary status |
| Active page tag | `#42b983` | Current item in the tags view only |

Do not merge `#1890ff`, `#409eff`, and `#42b983` into one generic accent. They identify different layers of the original interface. These are compiled/source defaults, subject to runtime theme handling. Plain anchors inherit their parent's color; `.link-type` uses `#337ab7` and hover `rgb(32, 160, 255)`, so not every link is primary blue. [S3] [S4] [S8]

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
| Table border shorthand | `1px solid #dfe6ec` | Explicit `$--table-border` override |
| Row hover | `#f5f7fa` | Table and list hover surface |

Use white as the dominant working surface. Gray backgrounds separate regions; they should not create a monochrome dark dashboard. Keep essential labels at regular or primary text contrast.

The table's pseudo-element edges and some dividers use `$--table-border-color`, inherited from `$--border-color-lighter` (`#e6ebf5`), while cells using `$--table-border` get `#dfe6ec`. Do not flatten these into one border color. Element hover/disabled/selection tints derive from SCSS mixing with white or black; retain the matching component styles rather than hand-copying a current-version palette. [S3] [E1]

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

**Guidance:** the following size/weight hierarchy and frontmatter line heights are composition defaults, not global CSS declarations. The application `body` sets a font family, but not a base font size or line height. Element UI provides `14px` and `24px` SCSS tokens only where components consume them. Application `label` sets weight `700`; the Settings title is `14px/22px`, KPI labels are `16px`, and KPI values are `20px`. Do not enforce `500` on every existing title or `400` on every label. [S3] [S6] [S7] [E1]

| Level | Size | Weight | Guidance |
| --- | --- | --- | --- |
| Large page or metric value | `20px` | 500-700 | Important totals or rare top-level headings |
| Dialog / section title | `18px` | 500 | Dialog titles and major section labels |
| Compact heading | `16px` | 500 | Card titles, form sections, dashboard labels |
| Body / control | `14px` | 400 | Default labels, controls, menus, and table content |
| Compact metadata | `13px` | 400 | Pagination and supporting information |
| Small tag / row action | `12px` | 400 | Tags, mini buttons, compact statuses |

Use `24px` as a suggested prose line-height, not a global override for controls, table rows, or headings. Keep headings compact inside panels. The login title is a context-specific `26px` bold exception; dashboard icons and numeric values may be larger when they communicate data. New work should not use viewport-scaled type, negative letter spacing, or marketing-scale headings inside the admin shell. [S10]

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

**Source:** `fixedHeader=false` by default. When enabled, `AppMain` compensates with `50px` top padding, or `84px` with tags. Mobile fixed headers are `100%` wide. While Element locks body scrolling for a modal, the fixed header receives `15px` right padding. Keep the compensation tied to the existing classes; do not double-offset a page. There is one vertical-sidebar layout, not a horizontal or mixed-layout switch. [S4] [S5]

### Grid and Content Composition

Use Element UI's 24-column grid and its responsive props. Common source-derived gutters are `8px` for tightly related panels, `32px` for chart groups, and `40px` for KPI cards. Prefer these patterns:

- filter toolbar, table, and pagination in one vertical workflow
- four KPI cards at `lg=6`, two per row at `xs=12` and `sm=12`
- three chart panels at `lg=8`, stacked at `xs=24` and `sm=24`
- two equal analytical panels at `lg=12`
- related secondary panels as `12 / 6 / 6` at large widths and stacked or paired below

Do not place every section inside an extra outer card. The page itself is a work surface; use cards for bounded data or tool units.

### Spacing

**Guidance:** normalize recurring values, but do not claim a strict 4px token system. Source also uses `5px`, `10px`, `18px`, `26px`, and `30px`; the names below are documentation aliases, not exported SCSS variables. [S3] [S7]

| Token | Value | Typical use |
| --- | --- | --- |
| `space-1` | `4px` | Tag offsets and very tight icon alignment |
| `space-2` | `8px` | Compact padding, toolbar gaps, chart padding on narrow screens |
| `space-3` | `10px` | Filter spacing and compact vertical gaps |
| `space-4` | `16px` | Card internals, row padding, grouped controls |
| `space-5` | `20px` | Standard page and card padding |
| `space-6` | `24px` | Section separation and notice padding |
| `space-7` | `30px` | Global pagination top margin and component-demo vertical margin |
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

### Stacking and Overlay Ownership

| Layer | Source value | Scope |
| --- | --- | --- |
| Fixed header | `9` | Layout's fixed-header wrapper |
| Mobile sidebar backdrop / sidebar | `999` / `1001` | Layout and sidebar stylesheet |
| Active vue-multiselect | `1000 !important` | Global third-party override |
| Element popups | Starts at `2000`, increments | Dependency PopupManager, not a fixed value per dialog |
| TinyMCE fullscreen | `10000` | Editor-specific override |
| Settings backdrop / panel | `20000` / `40000` | Custom RightPanel attached to body |
| Theme picker dropdown / message | `99999 !important` | ThemePicker override |

These are observed layers, not a recommended scale for new overlays. Element popups can fall below the settings panel; scoped CSS does not automatically reach body-mounted poppers or an editor iframe. Check ancestor transforms, append-to-body options, scroll locks, clipping, nested dialogs, and focus in the browser before changing a layer. [S3] [S4] [S6] [S8] [S13] [E2]

## Shapes

- Standard inputs, cards, and tags use `4px`; Element Dialog uses `2px`, while MessageBox uses `4px`. Keep component-specific radii. [E1] [E2]
- Use `2px` for compact or subtle shapes.
- Pagination size/jump inputs use `3px`; background pager controls use `2px`. [E1]
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

### Navigation and Settings Contracts

**Source:** router metadata is shared by navigation, permission filtering, breadcrumbs, search, and caching. [S5]

| Contract | Actual behavior |
| --- | --- |
| `hidden`, `alwaysShow` | Hide a route from navigation; retain a parent menu even with one visible child |
| `redirect: 'noRedirect'`, `meta.breadcrumb=false` | Make a breadcrumb non-clickable; omit it from the trail |
| `meta.roles` | Filter asynchronous routes by roles; frontend filtering is not server authorization |
| `meta.title`, `meta.icon` | Supply navigation/search labels and SVG or `el-icon-*` names |
| `meta.activeMenu` | Keep the list menu active on a hidden edit route |
| `name`, `meta.noCache` | `cachedViews` includes component names; `noCache` opts out; preserve route/component name matching |
| `meta.affix` | Keep fixed tags in close-others/close-all actions |
| Route path and query | Visited tags deduplicate by `path`; `router-view` is keyed by `route.path`; query-only variants are not independent cached workspaces |

The breadcrumb adds Dashboard when needed, uses matched routes, and respects non-link entries. HeaderSearch searches accessible titled routes with Fuse.js `3.4.4`; it is local route search, not a backend or business-record search. Keep nested menu resolution and external links intact. Tags provide refresh, close, close others, and close all, with affixed-page and active-page fallback handling. [S5]

`src\settings.js` defaults: `showSettings=true`, `tagsView=true`, `fixedHeader=false`, `sidebarLogo=false`, `errorLog='production'`. Settings exposes the theme color plus tags, fixed-header, and logo switches. Settings values live in Vuex without persistence; sidebar state (`sidebarStatus`) and Element size (`size`) use cookies. Do not promise that theme or layout settings survive refresh. ErrorLog records frontend Vue errors in enabled environments, not an operations-log backend. [S2] [S6] [S21]

RightPanel is a custom right-side settings surface, **not `el-drawer`**: width `100%`, max-width `260px`, height `100vh`, a `48px` handle at default `250px` top, content padding `24px`. It mounts under body and toggles by its handle; outside-click closure depends on `clickNotClose`. It does not implement an Escape handler, focus trap, or focus return. No routed business drawer exists in this checkout. [S6]

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

Use `el-table` for structured data. Compiled default text is `#606266`, headers use `#909399`, and row hover is `#f5f7fa`; border shorthand and edge color differ as described under Colors. Keep headers concise and align numeric data consistently. [S3] [E1]

- Use selection columns only when bulk actions exist.
- Keep status columns narrow and centered; the project uses `0 10px` status-cell padding.
- Use mini buttons for row actions and a stable action-column width.
- Use `5px` left/right cell padding only in explicitly dense `.small-padding` tables.
- Use tags for compact statuses, not as decoration on every value.
- Preserve existing selection, sorting, and pagination contracts; explicitly implement loading and error recovery where the demo lacks them.
- Keep wide tables internally scrollable and essential columns reachable. Optional-column reduction or a detail view is guidance, not an existing universal mobile-table behavior.

### Pagination

**Source:** reuse `src\components\Pagination\index.vue`. Its white wrapper has `padding: 32px 16px` and also receives the global `.pagination-container { margin-top: 30px }`; it does **not** set right alignment. Default props are `page=1`, `limit=20`, `pageSizes=[10,20,30,50]`, `background=true`, `autoScroll=true`, `hidden=false`, and `layout='total, sizes, prev, pager, next, jumper'`. Bind `page.sync` and `limit.sync`, supply required `total`, and handle `pagination({ page, limit })`. Page/size changes scroll to the top over `800ms` unless `autoScroll=false`. [S9]

**Dependency:** pagination text is `13px`, standard buttons are `28px` high with minimum width `35.5px`; background-style pager items use their own `30px` minimum width and `2px` radius, so the base `3px` token is not universal. **Guidance:** wrap or simplify secondary controls on narrow screens without losing page state; reset a filter query to page `1` explicitly and define behavior after deleting the last item on a page. [E1]

### Cards and Panels

Use `el-card` or a plain white panel for genuinely bounded content. Standard card padding is `20px`, radius `4px`, and a light border. Dashboard KPI cards are `108px` high with restrained `4px 4px 40px rgba(0,0,0,.05)` elevation; the icon block uses `16px` padding and `6px` radius.

Do not nest cards inside cards. Charts usually sit on white surfaces with `16px 16px 0` padding and `32px` bottom separation. Make titles and actions compact so the data remains the focal point.

### Dialogs, Drawers, and Popovers

**Dependency:** Element Dialog has width `50%`, default top `15vh`, white background and `2px` radius. Standard header padding is `20px 20px 10px`, body `30px 20px`, footer `10px 20px 20px`; title is `18px/24px`, body `14px` with no universal `24px` body line-height. The application's override resets dialog margin/transform/position, while inline `top` and `width` props still matter. MessageBox is a different `4px`-radius component. [S3] [E2]

Dialog supports modal click and Escape closure by default, `visible.sync`, `before-close`, and close events, but confirm loading and duplicate-submit prevention belong to the page. It has dialog ARIA attributes, yet it does not use MessageBox's `aria-dialog` focus-management implementation. Do not promise a focus trap or focus return for every overlay. **Guidance:** preserve unsaved data on cancel/error, keep confirmation last, and deliberately implement and test focus entry, containment, and return. [E2]

Use a dialog for short focused work and a full route for complex workflows. The only source-backed drawer-like shell surface is custom RightPanel; adding a business `el-drawer` requires an explicit new requirement, not an invented existing page. Do not place long tables or multi-stage forms inside a small dialog.

### Dropdowns and Context Menus

Dropdowns are compact white floating surfaces. Menu links must fill the item hit area. Context menus use `12px` text, `5px 0` outer padding, `7px 16px` item padding, `4px` radius, and light gray hover. Keep actions ordered from common to destructive and separate destructive actions when appropriate.

### Tabs, Tags, and Status

Use Element UI tabs for alternate views within one page and the tags view for visited routes; do not confuse the two. Standard tags use `12px` text, `4px` radius, and `0 10px` padding. Map business states consistently to success, warning, danger, and info rather than choosing colors ad hoc.

### Alerts, Messages, and Loading

Use Element UI feedback components with their existing semantic colors and icons. Inline validation belongs next to the control; page-level failure belongs near the failed content; transient completion can use a message. Confirm destructive actions before execution. Loading states should preserve container dimensions to prevent layout jumps.

Include intentional empty, no-results, permission-denied, and error states. A blank table body is not a complete state.

### Uploads

Use the actual upload wrapper for the task; not every source upload uses `el-upload`. The `100%` wide, `200px` high dragger override applies only under `.upload-container .el-upload`. Element's progress/success/error/remove hooks do not supply a complete product retry flow. State accepted types and limits, and implement recovery explicitly. [S3] [S16]

**Source:** avatar cropping (`ImageCropper`, crop `300x300` in the demo) and Dropzone use `https://httpbin.org/post`; article/TinyMCE upload demos also contain placeholder endpoints. `UploadExcel` is local FileReader/XLSX parsing, not server upload: one file, first sheet, an `onSuccess({ results, header })` callback; its picker accepts `.xlsx,.xls`, while drag validation also accepts `.csv`. Its drop area is `600x160px` with `24px` text and has no complete parse-error/finally recovery. Seven-cow/Qiniu upload source exists without a corresponding route. Do not present it as an installed storage service. [S16] [S17]

**Guidance:** align picker/drop validation, guard size/type before parsing, retain the file on failure, reset loading in all outcomes, expose retry/removal and keyboard selection, and make the fixed drop area fit its container. Use synthetic local files and mocked endpoints for verification; never send user files to demonstration services.

### Dashboard and Charts

Use charts to answer operational questions, not as decoration. Dashboard panels sit on `#f0f2f5` with white chart surfaces. Keep legends, axes, units, comparison periods, loading, empty, and error states legible. Pair color with labels or shapes and keep categorical palettes stable across charts.

Metric cards should present one label, one value, and at most one compact comparison or icon. Avoid promotional copy, oversized illustrations, and decorative gradients.

### Icons

Use repository SVG icons through `SvgIcon` and Element UI icons inside Element controls. Keep stroke/fill treatment consistent within a toolbar. Familiar tools may be icon-only with a tooltip; commands with ambiguous meaning should use icon plus text. Do not manually draw substitute SVGs when a matching local icon exists.

## Themes and Dependency Boundaries

| Theme surface | Source behavior | Boundary |
| --- | --- | --- |
| Compiled Element theme | SCSS overrides primary/semantic colors, button weight and borders before importing theme-chalk | Baseline for this file, not necessarily the final runtime stylesheet |
| Settings ThemePicker | Downloads `element-ui@<installed version>/lib/theme-chalk/index.css` from unpkg, derives primary tints/shade, injects `chalk-style`, scans style tags for color replacement | Initial watcher can also trigger injection; not limited to an explicit user color change |
| `/theme/index` switch | Toggles `body.custom-theme` with bundled precompiled `src\assets\custom-theme\index.css` | Separate demo skin, not a complete or automatically synchronized dark mode |
| Sidebar, tags, charts | Have explicit SCSS/component color values and chart series | Do not assume every fixed value changes with the Element theme |
| Editors and upload previews | TinyMCE iframe/content CSS, CodeMirror rubyblue, Toast UI/Dropzone styles | Separate theme and asset ownership; need explicit adaptation |

ThemePicker's request resolves only for HTTP `200`, with no rejection or timeout path; the indefinite compiling message can remain open after failure. Injected full Element CSS may override compiled semantic colors or component dimensions; development style tags and production extracted CSS may interact differently. **Unverified:** final colors, successive color changes, CDN failure recovery, body-mounted poppers, custom-theme interaction, chart contrast, and editor fullscreen layers. Do not claim theme-wide consistency from token inspection alone. [S8] [S13] [S14] [S15] [S16]

**Guidance:** retain a usable compiled fallback, report loading failure and allow retry, verify each theme surface, and scope third-party overrides by component. Adding persistence, dark mode, or replacing a CDN is a separate implementation decision, not a hidden part of a visual edit.

## Source Page Patterns

These patterns describe actual routes and components, not a claim that all demos are production-complete. Router modules are the inventory authority. [S5]

| Pattern | Existing composition and contract | Missing behavior to address in generated work |
| --- | --- | --- |
| Complex table | Filters, bordered table, mini row actions, pagination, create/edit Dialog, export; `published/success`, `draft/info`, `deleted/danger` | List failure has no catch/finally; create/update have no pending lock; delete only splices local rows, without confirmation or delete API [S9] |
| Dynamic / drag / inline table | Checkbox-selected columns; SortableJS row reordering; `originalTitle` for inline cancel | Preserve row IDs, ordering and cancel semantics; drag and inline success do not prove server persistence [S9] |
| Article list / create / edit | List links to hidden edit route; shared `ArticleDetail`, Sticky status/action bar, metadata form, preview URL, image, TinyMCE body | Fetch on edit uses an API wrapper, but submit/draft only update local state and show timed notifications; there is no save request or asynchronous save timer [S11] |
| Permission page / directive | Role-switch demo; `v-permission` for elements, `checkPermission` with `v-if` for dynamically rendered tabs/table columns | Preserve route filtering and conditional rendering; hiding DOM is not server authorization [S5] [permission-demo] |
| Role administration | Role table plus Dialog with Name, Desc and checkbox `el-tree`; `node-key='path'`, children/title props; checked keys rebuild route tree | Edit temporarily enables `checkStrictly` while restoring checked nodes, then disables it; delete confirms and calls role API. Add pending/error handling and render untrusted names as text, not the demo's HTML notification [S12] |
| Login | `520px` maximum form, `160px 35px 0` padding, username/password validation, Caps Lock hint, password reveal, Enter submission, loading and redirect | Credentials and third-party dialog are demos; guard concurrent attempts and retain error recovery [S10] |
| Dashboard | Admin/editor role switch; admin KPI selection updates line data, with chart groups, transaction table, Todo, box/profile content | Sample data and animation are not live metrics; define units, loading/error/empty and accessible chart summaries [S7] |
| Profile / in-page tabs | Profile `6/18` split with `xs=24`, Activity/Timeline/Account tabs; `/tab/index` synchronizes active tab to query and lazy tables | Account save is a success-message demo, not persistence; preserve route-tab versus in-page-tab distinction [S24] |
| Error and redirect | Standalone `/401`,`/404`, shell-contained `/error/401`,`/error/404`; 401 back/home and 404 home; hidden redirect/auth callback helpers | 404 uses fixed `1200px` composition; 401 uses `800px` max-width container with grid. Mobile fit is not guaranteed [S19] |
| Excel / ZIP / PDF | Filename, book type/auto-width, selected export, merged headers, import preview; ZIP helper; separate PDF download/print route | Selected export warns when selection is empty and clears it on success; preserve column mapping, time formatting, selection and download loading. No bulk-delete workflow is implemented [S17] |
| Documentation / guide / icons / clipboard / error-log / external link | Resource links, Driver.js tour, SVG/Element icon catalog, clipboard feedback and frontend-error demo | Preserve external-link behavior; a tour, clipboard success message, or frontend error list is not a backend feature [S18] [S21] [S22] |

The article `.sub-navbar` is a source-specific `50px` high, right-aligned action bar with a blue linear gradient; `draft` and `deleted` classes use `#d0d0d0`. This is an existing page exception, not permission to add gradients throughout the admin UI. Sticky defaults to `stickyTop=0` and `zIndex=1`; coordinate its offset with the shell when changing header behavior. [S3] [S11] [S18]

### Editors and Interactive Tools

| Tool | Versioned source contract | Adaptation boundary |
| --- | --- | --- |
| TinyMCE | CDN `tinymce-all-in-one@4.9.3`, default height `360`, English; `input` emits HTML; initializes/destroys on keep-alive activation/deactivation | Preserve editor ID, content changes and cleanup; iframe content theme and fullscreen need separate checks [S13] |
| MarkdownEditor | `tui-editor 1.3.3`, default height `300px`, language `en_US`, `input` emits Markdown | Do not replace with a current Toast UI API or assume host CSS reaches all editor internals [S14] |
| JsonEditor | CodeMirror `5.45.0`, JSON lint, rubyblue, minimum height `300px`; initial and changed incoming values use `JSON.stringify`, `changed` and `input` emit strings | Preserve the object/string boundary: external string input can be quoted again, while equal editor-text echoes are skipped by the watcher; invalid JSON remains editable text [S15] |
| SplitPane / Sticky / BackToTop / CountTo | Resizable split demos, a scroll-pinned action surface, scroll return and animated numbers | Preserve measured widths, listener cleanup, scroll offsets and stable dimensions; add keyboard/reduced-motion alternatives deliberately [S18] |
| DragDialog / DragSelect / DndList / Kanban | Dialog drag directive, sortable selected tags, paired drag lists, grouped columns via SortableJS/vuedraggable | Preserve identity, selection and group rules; mouse dragging alone is not accessible reordering or backend persistence [S18] |
| Charts | ECharts `4.2.1`, keyboard/line/mixed chart routes plus dashboard charts; resize mixin listens to window and sidebar transitions | Keep disposal/resize behavior; chart name "keyboard" does not establish keyboard accessibility [S7] [S18] |

## Interaction and Recovery

| State | Source / Dependency evidence | Guidance for a complete generated workflow |
| --- | --- | --- |
| Default, hover, active, selected | Element component variants and compiled theme; route-active/sidebar/tag state [S3] [S5] [E1] | Use component APIs and preserve selection semantics; do not substitute decorative colors |
| Focus and keyboard | Element controls provide component-specific handling; global anchors/divs suppress outlines [S3] [E2] | Restore a visible focus treatment and test the entire task, not just a component |
| Disabled and pending | Medium controls inherit disabled styling; buttons accept loading; login/export have local loading flags [S9] [S10] [S17] | Lock the operation in the handler as well as the button; release in finally; leave cancel/navigation policy explicit |
| Empty and no results | Element table provides empty text; demo list pages mainly supply data/loading [E1] [S9] | Distinguish an empty collection, no filter matches, and request failure; keep filters and offer clear/reset/retry actions |
| Validation failure | Login and ArticleDetail use form rules; complex-table Dialog clears validation on opening [S9] [S10] [S11] | Keep field values, show adjacent errors, focus the first invalid field, and prevent invalid API submission |
| Request failure | Axios wrapper emits a 5-second error Message and rejects; it does not reset page loading or retain retry state [S20] | Keep prior data where safe, show persistent local failure with retry, and prevent stale responses overwriting newer searches |
| Success and cancel | Complex table notifies after API wrappers; inline edit restores `originalTitle`; many editors use simulated success [S9] [S11] | Announce success only after the actual operation, retain drafts on error, and return focus after closing |
| Batch and dangerous actions | Selected Excel export exists; role delete has confirmation; complex-table delete does not [S12] [S17] [S9] | Identify affected count/scope, confirm irreversible actions, distinguish cancel from failure, and handle partial failures if a real batch API is added |

**Source data contract:** `src\utils\request.js` uses `timeout: 5000`, sends `X-Token`, and considers `res.code === 20000` successful. Codes `50008`, `50012`, `50014` offer re-login confirmation, then reset token/reload on confirmation. Transport and business errors reject the promise. Preserve this response envelope, cancellation semantics, auth flow, and Vuex/permission integration unless explicitly asked to change them. Production `main.js` enables MockJS in this demo; success does not establish a deployed backend. [S2] [S20]

## Accessibility and Content

**Source limits:** `a:focus`, `a:active`, and `div:focus` lose outlines; `SvgIcon` hides SVGs from assistive technology, while several custom click targets are divs/spans. MessageBox includes focus-management code that custom RightPanel and Element Dialog do not share. A tooltip is not automatically a button's accessible name. There is no comprehensive reduced-motion or WCAG compliance implementation. [S3] [S6] [S22] [E2]

**Guidance for new work:** use semantic buttons/links and associated labels; give icon-only controls an accessible name; provide visible focus, logical Tab order and Enter/Space activation. Test Escape, focus entry/return, and background interaction for each overlay. Give sortable tools a keyboard alternative and charts a textual summary. Expose loading/error/success to assistive technology without repeated announcements. Respect `prefers-reduced-motion`, including CountTo, chart animations, route transitions, sidebar and pagination scrolling.

**Measured token limitation, not a rendered-page audit:** white against compiled primary `#1890ff` is approximately `3.24:1`; `#909399` against white is `3.08:1`. These fail `4.5:1` for normal text. Preserve documented source colors as evidence; for accessibility improvements, approve and test local contrast adjustments (including hover, disabled/focus and themes), rather than claiming the original palette is AA-compliant. [S3] [E1]

| Content | Source behavior | Guidance |
| --- | --- | --- |
| Dates and time | `parseTime` uses local Date getters, converts 10-digit timestamps from seconds, default `{y}-{m}-{d} {h}:{i}:{s}`; `formatTime` has Chinese relative labels | Define timezone, invalid/missing fallback and exact-date access; do not silently switch API units or treat display strings as UTC [S23] |
| Numbers | `numberFormatter` abbreviates with `k/M/G`, `toThousandFilter` groups thousands; `timeAgo` uses English strings | Preserve stored precision; show units/currency and full values where abbreviated [S23] |
| Language | Element UI starts in English; application labels and helpers contain mixed languages; no complete locale switch | This bilingual specification does not add app i18n. Validate long Chinese/English labels, punctuation and date controls [S2] [S23] |
| Status and long text | Complex-table status keys map to tag types; some titles use tooltips and fixed columns | Keep backend enum keys unchanged, pair color with a label, allow field labels to wrap, and expose truncated content to keyboard/touch as well as hover [S9] |
| Rich text | TinyMCE emits HTML; role notification interpolates HTML; Markdown/JSON tools have different output types | Treat backend/user content as untrusted, sanitize rich HTML at the rendering boundary, and do not turn plain names into HTML notifications [S12] [S13] [S14] [S15] |

## Assets and Preservation Rules

**Source:** application icons are SVG sprite assets under `src\icons\svg`, loaded by `svg-sprite-loader` and referenced as `#icon-<name>`; Element controls use the package's icon font under `lib\theme-chalk\fonts`. Body text uses system fonts, not a bundled commercial typeface. `src\assets` contains local error-page images and custom-theme resources; demos also use external `wpimg.wallstcn.com` images, TinyMCE/unpkg CDN assets, and Dropzone preview markup referencing Material Icons. External image/font availability and independent rights are **Unverified**. [S1] [S3] [S16] [S22]

The upstream application and Element UI declare MIT licenses; this repository's original documentation is MIT. That does not automatically clear third-party photos, marks, icon sets, editor packages or CDN assets for redistribution. Retain upstream notices, verify each reused asset/dependency license, and prefer existing verified local assets. Do not bundle the ignored reference checkout, credentials, mock tokens, user uploads or generated dependency trees into this documentation repository.

Visual work must preserve route names/paths/meta, permission filtering and server authorization boundaries, `X-Token`/response envelopes, Vuex keys, component events and `.sync` bindings, editor serialization, row identity/order, form validation, and export column mappings. Demo endpoints are not production contracts. Changing these or upgrading dependencies is outside this specification update.

## Responsive Behavior

### Breakpoints

| Boundary | Source behavior |
| --- | --- |
| `<= 470px` | Login `max-width: 470px` hides the third-party action |
| `<= 550px` | KPI `max-width: 550px` hides the entire description (label and value) and centers the icon, not the description |
| `<= 767px` | Element UI `xs` uses `max-width: 767px`; only explicitly configured grid spans respond |
| `>= 768px` | Element UI `sm` |
| `rect.width - 1 < 992` | Exact application mobile test; integer widths `<= 992px` remain mobile, `993px` is desktop |
| `>= 992px` | Element UI `md`; at `992px`, grid `md` and mobile shell coexist |
| `>= 1200px` | Element UI `lg`; full dashboard grid |
| `>= 1920px` | Element UI `xl`; use extra width selectively, not by stretching all forms |

The dashboard reduces chart padding at `1024px` and below. Treat this as a local density adjustment, not a second application-shell breakpoint. On mobile resize the shell closes the sidebar without animation; navigation while it is open also closes it. The JS check uses body bounding-rect width, not an Element grid media query. [S4] [S7] [S10] [E1]

### Mobile Rules

- Remove the main content's left margin.
- Hide the sidebar off-canvas with `translate3d(-210px, 0, 0)` when closed.
- Show a full-page black overlay at `30%` opacity when the sidebar opens.
- Hide nonessential navbar utilities while retaining navigation and the user menu.
- **Guidance:** stack relevant grids and let filter controls wrap; the source does not make all forms responsive automatically.
- **Guidance:** keep essential row actions reachable; use internal table scrolling or a deliberate column/detail strategy.
- **Guidance:** prevent page-wide overflow while retaining inspection of wide data; keep touch targets usable even when compact.

Known fixed-width cases: complex-table Dialog form `400px` plus `50px` left margin and a `230px` action column; UploadExcel `600px` drop area; 404 `1200px` composition; default Element Dialog `50%` width; component demos use `30px 50px` margins. New responsive implementations should constrain forms to available width, wrap long labels, keep dialogs within viewport gutters, and test table/popover overflow. Retaining KPI labels/values below `550px` is an explicit usability improvement over source, not source parity. [S3] [S9] [S17] [S19]

## Motion

- Border and color transitions: `0.2s` using Element UI's standard easing.
- Sidebar width and main-content offset: `0.28s`.
- Navbar and icon hover background: `0.3s`.
- Tags-view close affordance: `0.3s` with the Element UI cubic-bezier curve.
- Route fade: `0.28s`; route transform and breadcrumb transitions: `0.5s`.
- Dashboard icon hover: `0.38s ease-out`.

Motion should clarify state or spatial change. The source does not provide a complete reduced-motion mode; add and test one for new work. Pagination uses an `800ms` scroll, Element Dialog fade/translate uses `.3s`, and demo-only `600ms` custom buttons and `1.5s` logo fades are local exceptions. Do not generalize these to all transitions. [S3] [S7] [S9] [E2]

## Do / Don't

### Do

- Use Element UI 2.13.2 components and the existing Vue 2 patterns.
- Preserve the `210px / 54px` sidebar and `50px + 34px` header geometry.
- Use `#1890ff` for primary application action and `#409eff` for sidebar active state.
- Keep list pages organized as filter toolbar, result table, then pagination.
- Use white working surfaces on a restrained gray canvas.
- Keep typography compact and information easy to scan.
- Add loading, empty, validation, error, disabled, and permission states.
- Verify desktop and mobile layouts at `991px`, `992px`, and `993px`, including the grid/shell mismatch at `992px`.

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
Read the selected 4.3.1 DESIGN.md in full. Use Vue 2.6.10 and Element UI 2.13.2, then select the matching source page pattern: list, editor, profile, dashboard, login, or error page. Preserve routes, permissions, APIs, stores and component events. Distinguish Source, Dependency, Guidance and Unverified rules. Implement required loading, empty, failure/retry, validation and duplicate-submit handling without pretending demo saves are persistent. Check theme and mobile boundaries and report verification limits.
```

### Existing Page Revision

```text
Read DESIGN.md and inspect the existing page before editing. Keep its API, router, permission, validation, store and serialization contracts unchanged. Make the smallest requested UI change within the vue-element-admin 4.3.1 system. Reuse Element UI components and local SVG icons, then verify 991/992/993px, narrow mobile, long text, themes, overlays and recovery states. Separate static checks from actual browser evidence; do not upgrade dependencies or copy demo vulnerabilities.
```

### Review Checklist

```text
Review this UI against DESIGN.md. Report deviations in application-shell geometry, token use, component choice, spacing, type hierarchy, table workflow, responsive behavior, accessibility, and state coverage. Distinguish source-backed requirements from optional improvements and do not propose a framework migration.
```

## Known Gaps

- vue-element-admin 4.3.1 is a Vue 2 and Element UI 2.13.2 system. Its visual rules are not a drop-in contract for Vue 3 or Element Plus.
- The source is desktop-first; the exact mobile expression is `rect.width - 1 < 992`. Fixed-width demos and hidden mobile KPI values remain upstream limitations.
- Accessibility tokens, reduced-motion behavior, minimum touch targets, and full keyboard flows are not comprehensively documented in the upstream source. New work should improve them without changing established behavior.
- The repository contains demonstration pages and a demo-only alternate theme. Treat core shell and compiled theme files as stronger evidence than one-off demos.
- Spacing is recurrent rather than formally tokenized upstream. The spacing scale here normalizes observed values; preserve local project conventions where they are more specific.
- English Element locale is enabled by default, but application/helper strings are mixed-language; bilingual documentation is not application localization.
- Charts provide examples, not a complete data-visualization standard. Define units, legends, accessible labels, and series semantics from the product domain.
- Runtime theme cascade, external assets, complete keyboard/focus paths, responsive screenshots, backend persistence and the resolved dependency tree are unverified. This update did not install dependencies, run the frontend, or perform a UI acceptance test.

## Acceptance Boundaries

Documentation acceptance checks UTF-8, parsed frontmatter, matching bilingual metadata/tokens/rules, evidence links, route/module coverage, and unchanged version `4.3.1`. Source acceptance checks the upstream commit, declared dependency versions, CSS values, breakpoint expression, props/events, simulated versus API-backed actions, and repository scope. These checks do not establish visual correctness in a browser.

When implementation requires runtime evidence, use synthetic data and controlled endpoints. Test `375px` and desktop `1440px`, each side of `470/550/768/992/1024/1200px` boundaries (especially `991/992/993px`), sidebar open/closed, tags and fixed-header combinations, long bilingual content and constrained dialogs/tables. Exercise compiled/CDN/custom themes, CDN failures, nested overlays/editor fullscreen, keyboard/focus and reduced motion. Check loading/empty/invalid/failed/retry/success, repeated submit, canceled delete and empty/selected export. Record screenshots, assertions, environment and remaining gaps before claiming UI acceptance.

## Provenance

This specification is an independent, source-derived reference based on the official vue-element-admin `4.3.1` tag and Element UI `2.13.2`. It is not official documentation and does not imply endorsement by vue-element-admin, Element UI, or Google Stitch.

### Versioned Evidence Index

Application links below are pinned to the audited commit. Directory links group closely related files; the paths named in each row identify what to inspect. Dependency links select the exact published npm package, not latest documentation.

| ID | Source and covered files |
| --- | --- |
| S1 | [package.json][S1]: pinned application/dependency versions; upstream LICENSE is at the same commit |
| S2 | [src\main.js][S2]: import order, locale, size cookie and production MockJS |
| S3 | [src\styles][S3]: `element-variables.scss`, `variables.scss`, `index.scss`, `element-ui.scss`, `sidebar.scss`, `transition.scss`, `btn.scss` |
| S4 | [src\layout][S4]: `index.vue`, `components\AppMain.vue`, `Navbar.vue`, `Sidebar`, `mixin\ResizeHandler.js` |
| S5 | [src\router][S5]: `index.js`, `modules`; also [Tags store][tags-store], [Breadcrumb][breadcrumb], [HeaderSearch][search], [TagsView][tags-view], [permission guard][permission] |
| S6 | [src\settings.js][S6], [RightPanel][right-panel], [Settings][settings-panel], [settings store][settings-store], [app store][app-store] |
| S7 | [src\views\dashboard][S7]: role switch, admin/editor pages, PanelGroup, charts and resize mixin |
| S8 | [ThemePicker][S8], [theme page][theme-page], [custom-theme CSS][custom-theme] |
| S9 | [src\views\table][S9]: complex/dynamic/drag/inline tables; [Pagination][pagination] |
| S10 | [src\views\login\index.vue][S10] |
| S11 | [src\views\example][S11]: list/create/edit and `components\ArticleDetail.vue` |
| S12 | [src\views\permission\role.vue][S12] |
| S13 | [src\components\Tinymce][S13]: editor, toolbar/plugins, CDN script and image upload |
| S14 | [src\components\MarkdownEditor\index.vue][S14] |
| S15 | [src\components\JsonEditor\index.vue][S15] |
| S16 | [src\components][S16]: Upload, ImageCropper, Dropzone, UploadExcel; [upload demos][demos] |
| S17 | [src\views\excel][S17], [ZIP][zip], [PDF][pdf], [export helpers][vendor] |
| S18 | [src\views\components-demo][S18], [charts][charts], [guide][guide], [clipboard][clipboard]; matching local wrappers/directives |
| S19 | [src\views\error-page][S19] |
| S20 | [src\utils\request.js][S20] |
| S21 | [src\utils\error-log.js][S21], [ErrorLog component][error-log] |
| S22 | [src\icons][S22], [SvgIcon][svg-icon], [assets][assets] |
| S23 | [src\utils\index.js][S23], [filters][filters] |
| S24 | [src\views\profile][S24], [tab page][tab] |
| E1 | [Element 2.13.2 theme variables][E1], [table styles][element-table], [pagination styles][element-pagination] |
| E2 | [Dialog styles][E2], [Dialog component][element-dialog], [MessageBox][element-messagebox], [PopupManager][element-popup] |

[S1]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/package.json
[S2]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/main.js
[S3]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/styles
[S4]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/layout
[S5]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/router
[S6]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/settings.js
[S7]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/dashboard
[S8]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/ThemePicker/index.vue
[S9]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/table
[S10]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/login/index.vue
[S11]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/example
[S12]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/permission/role.vue
[S13]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/Tinymce
[S14]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/MarkdownEditor/index.vue
[S15]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/JsonEditor/index.vue
[S16]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components
[S17]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/excel
[S18]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/components-demo
[S19]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/error-page
[S20]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/utils/request.js
[S21]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/utils/error-log.js
[S22]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/icons
[S23]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/utils/index.js
[S24]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/profile
[tags-store]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/store/modules/tagsView.js
[breadcrumb]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/Breadcrumb/index.vue
[search]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/HeaderSearch/index.vue
[tags-view]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/layout/components/TagsView/index.vue
[permission]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/permission.js
[permission-demo]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/permission/directive.vue
[right-panel]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/RightPanel/index.vue
[settings-panel]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/layout/components/Settings/index.vue
[settings-store]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/store/modules/settings.js
[app-store]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/store/modules/app.js
[theme-page]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/theme/index.vue
[custom-theme]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/assets/custom-theme/index.css
[pagination]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/Pagination/index.vue
[demos]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/components-demo
[zip]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/zip
[pdf]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/pdf
[vendor]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/vendor
[charts]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/charts
[guide]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/guide
[clipboard]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/clipboard
[error-log]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/ErrorLog/index.vue
[svg-icon]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/SvgIcon/index.vue
[assets]: https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/assets
[filters]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/filters/index.js
[tab]: https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/tab/index.vue
[E1]: https://unpkg.com/element-ui@2.13.2/packages/theme-chalk/src/common/var.scss
[E2]: https://unpkg.com/element-ui@2.13.2/packages/theme-chalk/src/dialog.scss
[element-table]: https://unpkg.com/element-ui@2.13.2/packages/theme-chalk/src/table.scss
[element-pagination]: https://unpkg.com/element-ui@2.13.2/packages/theme-chalk/src/pagination.scss
[element-dialog]: https://unpkg.com/element-ui@2.13.2/packages/dialog/src/component.vue
[element-messagebox]: https://unpkg.com/element-ui@2.13.2/packages/message-box/src/main.vue
[element-popup]: https://unpkg.com/element-ui@2.13.2/src/utils/popup/popup-manager.js
