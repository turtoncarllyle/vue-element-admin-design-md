# vue-element-admin-design-md

[简体中文](README.md) | [English](README.en-US.md)

[![vue-element-admin](https://img.shields.io/badge/vue--element--admin-4.3.1-1890ff)](https://github.com/PanJiaChen/vue-element-admin/tree/4.3.1)
[![DESIGN.md](https://img.shields.io/badge/DESIGN.md-AI%20ready-42b983)](https://stitch.withgoogle.com/docs/design-md/overview/)
[![License](https://img.shields.io/badge/license-MIT-304156)](LICENSE)

面向 AI 编码 Agent、专注后台管理系统的 vue-element-admin 版本化设计系统文档。

`DESIGN.md` 是 Google Stitch 提出的设计系统文档格式：用纯文本 Markdown 记录设计系统，让 AI 编码 Agent 能够生成风格一致的 UI。它描述界面应呈现的视觉结果、组件状态和响应式规则，不替代 vue-element-admin 或 Element UI 的组件 API 文档。

本仓库从 vue-element-admin 官方源码及其对应的 Element UI 版本中提取真实的颜色、字体、尺寸、间距、圆角、阴影、应用壳层和交互状态，并按 vue-element-admin 版本独立维护。

## DESIGN.md 的目的与用途

`DESIGN.md` 把依赖人工判断的视觉规范转化为 AI Agent 可以直接读取的上下文，使不同页面、不同任务和不同开发阶段生成的界面保持同一种 vue-element-admin 设计语言。

它主要用于：

- 在 AI 新建后台页面前，提供统一的颜色、字体、布局和组件规则
- 在 AI 修改既有页面时，约束新增内容不偏离 vue-element-admin 4.3.1 风格
- 在代码审查或 UI 验收时，作为可检查的视觉一致性基线
- 在项目升级 vue-element-admin 时，通过版本目录选择匹配的设计规范

它不提供路由、权限、状态管理、接口或业务逻辑；这些内容仍应以项目代码和官方文档为准。

## 设计场景

本仓库面向后台管理系统，不是企业官网、营销落地页或内容型门户。规范重点覆盖：

- 带深色侧栏、顶部工具栏、面包屑和多页签的后台框架
- 数据列表、筛选、复杂表格、分页和批量操作
- 新增、编辑、查询、登录和设置表单
- 仪表盘指标、图表、卡片和待办信息
- 弹窗、抽屉、上传、消息、确认和异常反馈

目标是保持 vue-element-admin 原生的清晰层级、适中信息密度和高频操作效率，而不是套用另一套通用仪表盘视觉风格。

## 支持版本

| vue-element-admin 版本 | 英文标准版 | 简体中文版 | GitHub Release |
| --- | --- | --- | --- |
| `4.3.1` | [DESIGN.md](versions/4.3.1/DESIGN.md) | [DESIGN.zh-CN.md](versions/4.3.1/DESIGN.zh-CN.md) | [v4.3.1](https://github.com/turtoncarllyle/vue-element-admin-design-md/releases/tag/v4.3.1) |

英文 `DESIGN.md` 是默认的生态兼容版本；中文版本遵循相同章节、令牌和规则。

## 使用方法

1. 选择与项目 vue-element-admin 版本一致的目录。
2. 将英文版或中文版下载到项目根目录，并命名为 `DESIGN.md`。
3. 告诉 AI 编码 Agent 在生成或修改 UI 时严格遵循该文件。

Windows PowerShell 下载英文标准版：

```powershell
Invoke-WebRequest `
  -Uri "https://raw.githubusercontent.com/turtoncarllyle/vue-element-admin-design-md/main/versions/4.3.1/DESIGN.md" `
  -OutFile ".\DESIGN.md"
```

下载简体中文版：

```powershell
Invoke-WebRequest `
  -Uri "https://raw.githubusercontent.com/turtoncarllyle/vue-element-admin-design-md/main/versions/4.3.1/DESIGN.zh-CN.md" `
  -OutFile ".\DESIGN.md"
```

示例提示词：

```text
请读取项目根目录的 DESIGN.md，并严格按照其中的 vue-element-admin 4.3.1 设计令牌、应用壳层、组件状态和响应式规则实现这个后台页面。保留现有 Vue 2、Element UI、路由和权限契约。
```

## 规范覆盖范围

- 视觉主题、设计原则和信息密度
- 颜色角色、字体层级、间距、圆角、阴影和动效
- `210px` 侧栏、`50px` 顶栏、`34px` 标签栏和内容区
- Element UI 2.13.2 的按钮、表单、表格、分页、弹窗和反馈状态
- 仪表盘卡片、图表、筛选工具栏、登录页和移动端侧栏
- 面向 AI Agent 的 Do / Don't 与可直接使用的提示词

## 版本与来源

当前规范基于 [vue-element-admin 4.3.1](https://github.com/PanJiaChen/vue-element-admin/tree/4.3.1) 源码，核心视觉来源为 `src\styles`、`src\layout`、`src\views\dashboard`、`src\views\login`，以及项目实际依赖并编译的 Element UI `2.13.2` 主题令牌。

你提供的 [vue-element-admin v4.0.0](https://github.com/PanJiaChen/vue-element-admin/tree/v4.0.0) 用作历史参考；仓库当前正式支持的规范版本是 `4.3.1`。

本项目是独立整理的设计系统文档，与 vue-element-admin、Element UI 或 Google Stitch 官方无隶属或背书关系。相关项目和标识归其各自权利人所有。

## 许可

本仓库中的原创文档采用 [MIT License](LICENSE) 发布。使用 vue-element-admin 和 Element UI 时仍应分别遵守它们各自的开源许可。
