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

它不实现路由、权限、状态管理、接口或业务逻辑，但会记录视觉修改必须保留的源码契约。它明确区分源码事实、依赖继承、建议规则和待验证事项，避免把演示流程误当成生产能力。

## 设计场景

本仓库面向后台管理系统，不是企业官网、营销落地页或内容型门户。规范重点覆盖：

- 带深色侧栏、顶部工具栏、面包屑和多页签的后台框架
- 数据列表、筛选、复杂表格、分页和批量操作
- 新增、编辑、查询、登录和设置表单
- 仪表盘指标、图表、卡片和待办信息
- 弹窗、自定义右侧设置面板、上传、消息、确认和异常反馈
- 角色权限树、富文本/Markdown/JSON 编辑器、拖拽工具和导入导出

目标是保持 vue-element-admin 原生的清晰层级、适中信息密度和高频操作效率，而不是套用另一套通用仪表盘视觉风格。

## 支持版本

| vue-element-admin 版本 | 英文标准版 | 简体中文版 | GitHub Release |
| --- | --- | --- | --- |
| `4.3.1` | [DESIGN.md](versions/4.3.1/DESIGN.md) | [DESIGN.zh-CN.md](versions/4.3.1/DESIGN.zh-CN.md) | [v4.3.1](https://github.com/turtoncarllyle/vue-element-admin-design-md/releases/tag/v4.3.1) |

英文 `DESIGN.md` 是默认的生态兼容版本；中文版本遵循相同章节、令牌和规则。

[4.3.1 审计与更新记录](versions/4.3.1/AUDIT.md)包含具体问题、源码证据、覆盖矩阵及验收范围。审计记录为中文维护文档，双语设计规范本身均可独立使用。

## 使用方法

1. 选择与项目 vue-element-admin 版本一致的目录。
2. 选择英文版或中文版作为项目根目录的 `DESIGN.md`；已有定制规范时先比对合并，不直接覆盖。
3. 完整读取规范，按实际任务选择列表、编辑、仪表盘、登录等模式，并核对对应源码与业务契约。
4. 要求 Agent 区分来源事实与补充建议，交付状态恢复及验证限制；静态文档检查不等于 UI 验收。

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
请完整读取项目根目录的 DESIGN.md，使用 vue-element-admin 4.3.1、Vue 2.6.10 和 Element UI 2.13.2。按实际页面选择源码模式，区分源码事实、依赖继承、建议规则和待验证项。保留路由、权限、API、Store 和数据格式，补齐加载、空数据、失败重试、校验及防重复提交。核对 991/992/993px、主题、长文本及浮层，说明静态检查和浏览器验证各自覆盖范围；不要升级依赖或把演示保存当持久化。
```

## 规范覆盖范围

- 视觉主题、设计原则和信息密度
- 颜色角色、字体层级、间距、圆角、阴影和动效
- `210px` 侧栏、`50px` 顶栏、`34px` 标签栏和内容区
- Element UI 2.13.2 的按钮、表单、表格、分页、弹窗和反馈状态
- 仪表盘卡片、图表、筛选工具栏、登录页和移动端侧栏
- 面向 AI Agent 的 Do / Don't 与可直接使用的提示词
- 主题注入与第三方组件边界、路由缓存/设置契约、真实页面模式与状态恢复
- 无障碍与内容规则、图标/图片许可边界，以及明确的待验证事项

## 版本与来源

当前规范基于 [vue-element-admin 4.3.1](https://github.com/PanJiaChen/vue-element-admin/tree/4.3.1) 源码，核心视觉来源为 `src\styles`、`src\layout`、`src\views\dashboard`、`src\views\login`，以及项目实际依赖并编译的 Element UI `2.13.2` 主题令牌。

源码已对照固定提交 [`f6d8204`](https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380)，307 个文件内容一致。参考源码没有锁文件或已安装依赖树；Element UI 规则单独核对 npm `2.13.2` 源码包，不代表已验证完整依赖解析或运行效果。

你提供的 [vue-element-admin v4.0.0](https://github.com/PanJiaChen/vue-element-admin/tree/v4.0.0) 仅作历史背景；本次未对照其完整源码，也未新增 `4.0.0` 规范。正式支持版本仍为 `4.3.1`。

### 同版本更新约定

- 上游版本、目录和文档 `version` 始终保持 `4.3.1`；此次只补充规范，不升级前端依赖，不新增修订版本号。
- `main` 下的版本目录是当前维护内容；用 Git 提交及 `updated` 日期追踪更新。
- 保留原 `v4.3.1` 标签和首发附件 `DESIGN.md`、`DESIGN.zh-CN.md`。标签及 GitHub 自动生成的 Source code 压缩包仍是首发快照，不等于当前 `main`。
- 在同一 [v4.3.1 Release](https://github.com/turtoncarllyle/vue-element-admin-design-md/releases/tag/v4.3.1) 追加说明、更新提交链接和日期标记附件，不覆盖历史附件。日期只区分文件快照，不是新版本。
- 需要固定规范时，从该文件的提交历史选择完整 SHA，并把下载 URL 中的 `main` 替换为该 SHA。上面的 `main` 下载链接会随同版本维护更新。

本次只完成文档和源码静态核对；未安装依赖、启动旧版前端、执行截图或 UI 验收。运行时主题级联、键盘焦点、移动页面表现、外部资源和后端行为见审计记录中的待验证清单。

本项目是独立整理的设计系统文档，与 vue-element-admin、Element UI 或 Google Stitch 官方无隶属或背书关系。相关项目和标识归其各自权利人所有。

## 许可

本仓库中的原创文档采用 [MIT License](LICENSE) 发布。使用 vue-element-admin 和 Element UI 时仍应分别遵守它们各自的开源许可。
