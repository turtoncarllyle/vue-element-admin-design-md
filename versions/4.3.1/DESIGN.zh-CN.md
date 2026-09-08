---
version: "4.3.1"
updated: "2026-09-08"
upstream-commit: "f6d8204b0b6fbb794ada0c99391b7b85ce976380"
element-ui: "2.13.2"
token-scope: "Compiled baseline; runtime theme overrides require verification"
typography-scope: "Composition guidance, not a global body or heading CSS declaration"
name: "vue-element-admin-design-system"
description: >-
  基于 vue-element-admin 4.3.1 及其 Element UI 2.13.2 组件层源码整理的设计规范。
  它定义该应用务实、桌面优先的视觉语言，使 AI 编码 Agent 能够在不替换既有 Vue 2
  和 Element UI 约定的前提下扩展后台界面。
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

# vue-element-admin 4.3.1 设计系统

## 概览

本文档用纯文本 Markdown 记录 vue-element-admin 4.3.1 的视觉系统，供 AI 编码 Agent 读取。它描述生成的后台界面应呈现的视觉和体验，不替代 vue-element-admin 或 Element UI 官方 API 文档，也不能用来虚构组件不支持的行为。

该系统务实、桌面优先，服务于高频运营工作。其标志是深蓝灰导航侧栏、白色工具顶栏、蓝色操作状态、克制的灰色表面、14px 正文字号、紧凑的中等尺寸控件，以及以表格为中心的清晰编排。界面应显得成熟高效，而不是营销化或装饰化。

### 核心原则

1. **扩展既有技术栈。** 优先使用 Vue 2 组件、Element UI 2.13.2 `el-*` 组件、既有 SVG 图标、路由元数据和应用辅助能力。
2. **保留应用壳层。** 侧栏、顶栏、面包屑、标签栏和内容区几何关系必须保持可辨识。
3. **优化重复操作。** 筛选、表格、表单、分页和行操作应易于扫描并能快速使用。
4. **先建立层级，再考虑装饰。** 通过间距、白色表面、细边框、弱化文本和克制阴影形成结构。
5. **让颜色表达状态。** 蓝色用于主操作和焦点，语义色表达状态，深色侧栏稳定导航层级。
6. **适配，而不是重做。** 修改既有项目时，保留路由、权限、API 契约、组件尺寸和本地约定。

### 事实来源

本版对应官方标签 `4.3.1`（不带 `v`），提交 `f6d8204b0b6fbb794ada0c99391b7b85ce976380`。本地参考文件与上游全部 307 个文件逐一比对，无差异。`package.json` 固定 Vue `2.6.10`、Element UI `2.13.2`、Vue Router `3.0.2`、Vuex `3.1.0` 和 ECharts `4.2.1`。参考源码没有锁文件或已安装依赖树。下文 Element UI 行为核对的是经过完整性校验的 npm `2.13.2` 源码包，而不是当前 Element Plus 文档。传递依赖解析结果和运行时渲染仍待验证。[S1] [E1]

全文使用以下证据分类：

| 标记 | 含义 | Agent 的处理方式 |
| --- | --- | --- |
| 源码事实 | 应用代码、配置或演示中的明确行为 | 保留对应契约，同时识别已记录的限制 |
| 依赖继承 | Element UI `2.13.2` 提供的行为 | 保留受支持的属性、事件和组件行为 |
| 建议规则 | 为生成工作补充的规则，不代表上游已实现 | 在任务范围内有意识地实现 |
| 待验证 | 需要浏览器、已解析依赖树、后端或资源许可证据 | 明确限制，不宣称已经验收 |

除明确标为源码事实或依赖继承外，关于新增编排、无障碍、完整状态和移动端改善的指令均属于**建议规则**。数值表描述源码或依赖值，但归纳的间距及字体层级属于建议。

来源优先级：先匹配宿主项目的真实版本和业务契约，再检查组件属性、局部 scoped/deep 样式、应用覆盖和依赖实现。CSS 仍按选择器优先级、`!important`、注入顺序及层叠上下文生效，不能简化为文件先后顺序。`src\main.js` 依次加载 Normalize、编译后的 `element-variables.scss` 主题、`styles\index.scss`；运行时 `ThemePicker` 和 `/theme/index` 演示可能改变结果。元数据颜色是**编译基线**，不代表所有运行时像素。[S2] [S3] [S8]

`src\assets\custom-theme\index.css` 是实际存在的替代主题演示，不是默认产品主题或完整暗色模式。不要把其中的炭黑主色当成基线。历史 `v4.0.0` 链接仅供背景参考，本版不承诺兼容它。

### 读取入口与版本选择

完整读取匹配的 `versions\4.3.1\DESIGN.md` 或 `DESIGN.zh-CN.md`，再检查目标页面及其模块证据链接。两种语言规则相同。编码前先选择页面模式，不要把登录、编辑器或异常页强制套入 CRUD 表格模式。保留路由、权限、数据格式、校验和 Store。

本次在上游版本 `4.3.1` 内更新，不新增文档修订版本号。`main/versions/4.3.1` 是持续维护规范，`v4.3.1` 保留首发快照。需要复现时使用完整 Git 提交链接。同一 Release 区分原始附件与按日期标记的更新附件，日期不是版本号。本文可独立使用，配套审计记录保存证据及验收限制。

## 颜色

### 主色与语义色

| 角色 | 值 | 用途 |
| --- | --- | --- |
| 主操作色 | `#1890ff` | 编译后的主按钮、输入焦点、Element UI 选中控件 |
| 侧栏激活色 | `#409eff` | 顶级侧栏激活项；有意与编译后的主色区分 |
| 成功 | `#13ce66` | 已完成、健康、通过和正向状态 |
| 警告 | `#ffba00` | 需关注、待处理、风险和提醒状态 |
| 危险 | `#ff4949` | 删除、失败、无效、破坏性和严重状态 |
| 信息 | `#909399` | 中性信息和次要状态 |
| 当前页面标签 | `#42b983` | 仅用于标签栏中的当前项 |

不要把 `#1890ff`、`#409eff` 和 `#42b983` 合并成一个通用强调色，它们对应原始界面的不同层级。这些是编译或源码默认值，会受到运行时主题处理影响。普通链接继承父级颜色；`.link-type` 使用 `#337ab7`，悬停为 `rgb(32, 160, 255)`，并非所有链接都是主蓝色。[S3] [S4] [S8]

### 导航颜色

| 角色 | 值 | 用途 |
| --- | --- | --- |
| 侧栏背景 | `#304156` | 主导航侧栏 |
| 侧栏悬停 | `#263445` | 顶级菜单项悬停 |
| 子菜单背景 | `#1f2d3d` | 嵌套导航 |
| 子菜单悬停 | `#001528` | 嵌套项悬停 |
| 菜单文字 | `#bfcbd9` | 默认导航标签和图标 |
| 子菜单激活文字 | `#f4f4f5` | 选中的嵌套导航标签 |
| 侧栏 Logo 背景 | `#2b2f3a` | 可选 Logo 区域 |

导航应保持从顶部到底部连续的深色表面。不要把每个菜单项改成分离卡片；除非宿主项目已有受支持主题，否则不要改成浅色侧栏。

### 表面、文字与边框

| 角色 | 值 | 用途 |
| --- | --- | --- |
| 页面 / 组件表面 | `#fff` | 顶栏、卡片、弹窗、表单、表格 |
| 仪表盘画布 | `#f0f2f5` | 仪表盘页面背景 |
| 主要文字 | `#303133` | 标题和高强调内容 |
| 常规文字 | `#606266` | 正文、表单值和普通标签 |
| 次要文字 | `#909399` | 元数据和辅助说明 |
| 占位文字 | `#c0c4cc` | 输入占位和不可用提示 |
| 基础边框 | `#dcdfe6` | 输入框和标准组件轮廓 |
| 浅边框 | `#dfe4ed` | 项目覆盖后的浅边框令牌 |
| 更浅边框 | `#e6ebf5` | 卡片、禁用轮廓和弱分隔线 |
| 表格边框简写 | `1px solid #dfe6ec` | 明确覆盖的 `$--table-border` |
| 行悬停 | `#f5f7fa` | 表格和列表悬停表面 |

白色是主要工作表面，灰色背景负责分区，不要把整个后台做成单一深色仪表盘。关键标签应保持常规或主要文字对比度。

表格伪元素边缘和部分分隔线使用 `$--table-border-color`，继承 `$--border-color-lighter`（`#e6ebf5`）；使用 `$--table-border` 的单元格边框则是 `#dfe6ec`。不要把两者合并成一个颜色。Element 悬停、禁用、选中浅色由 SCSS 与白色或黑色混合生成，应保留对应组件样式，不要手抄新版调色板。[S3] [E1]

### 仪表盘强调色

仪表盘指标卡使用有限的分类强调色：`#40c9c6`、`#36a3f7`、`#f4516c` 和 `#34bfa3`。它们应用于图标或数据系列，而不是每张卡片的背景。图表可以使用更丰富的系列色，但控件和导航仍必须遵循核心令牌。

## 字体排印

### 字体族

使用应用原生字体栈：

```css
"Helvetica Neue", Helvetica, "PingFang SC", "Hiragino Sans GB",
"Microsoft YaHei", Arial, sans-serif
```

Element 控件使用 Element UI 图标字体，应用图标使用仓库的 `SvgIcon` 系统。已有合适图标时，不要用文字字符或无关图标风格替代。

### 层级

**建议规则：**下表字号、字重以及元数据行高是编排默认值，不是全局 CSS 声明。应用 `body` 设置了字体族，但未设置基础字号或行高；Element UI 的 `14px` 和 `24px` SCSS 令牌仅在组件引用处生效。应用 `label` 字重为 `700`；Settings 标题为 `14px/22px`，指标卡标签为 `16px`，指标值为 `20px`。不要把既有标题统一强制设为 `500`，也不要把所有标签强制设为 `400`。[S3] [S6] [S7] [E1]

| 层级 | 字号 | 字重 | 指引 |
| --- | --- | --- | --- |
| 大页面标题或指标值 | `20px` | 500-700 | 重要总量或少量顶级标题 |
| 弹窗 / 区块标题 | `18px` | 500 | 弹窗标题和主要区块标签 |
| 紧凑标题 | `16px` | 500 | 卡片标题、表单区块和仪表盘标签 |
| 正文 / 控件 | `14px` | 400 | 默认标签、控件、菜单和表格内容 |
| 紧凑元数据 | `13px` | 400 | 分页和辅助信息 |
| 小标签 / 行操作 | `12px` | 400 | 标签、迷你按钮和紧凑状态 |

`24px` 是段落正文的建议行高，不是对控件、表格行或标题的全局覆盖。面板内标题保持紧凑。登录标题是特定场景下的 `26px` 加粗例外；仪表盘图标和数字可因数据表达而更大。新增后台内容不应使用视口缩放字号、负字距或营销级超大标题。[S10]

## 布局

### 应用壳层

| 区域 | 尺寸 | 行为 |
| --- | --- | --- |
| 展开侧栏 | `210px` | 固定在左侧，占满视口高度 |
| 收起侧栏 | `54px` | 保留图标，隐藏标签和子菜单箭头 |
| 顶栏 | `50px` | 白色顶部工具栏 |
| 标签栏 | `34px` | 顶栏下方可选的访问页面条 |
| 主内容 | `calc(100% - sidebar)` | 左外边距跟随侧栏展开或收起 |
| 标准页面内边距 | `20px` | `.app-container` 默认值 |
| 仪表盘内边距 | `32px` | 数据总览画布；窄屏时减少图表内边距 |

顶栏、标签栏和主内容属于同一个连续工作区。固定顶栏时，其宽度必须在侧栏收起后从 `calc(100% - 210px)` 更新为 `calc(100% - 54px)`。启用标签栏时内容最小高度为 `calc(100vh - 84px)`，未启用时为 `calc(100vh - 50px)`。

**源码事实：**默认 `fixedHeader=false`。开启后，`AppMain` 补偿 `50px` 顶部内边距，启用标签时为 `84px`。移动端固定顶栏宽 `100%`。Element 弹窗锁定 body 滚动时，固定顶栏增加 `15px` 右内边距。保留既有类名对应的补偿，不要让页面重复偏移。源码只有纵向侧栏布局，没有水平或混合布局切换。[S4] [S5]

### 栅格与内容编排

使用 Element UI 24 栏栅格及其响应式属性。源码常见沟槽为：紧密面板 `8px`、图表组 `32px`、指标卡 `40px`。优先采用以下模式：

- 筛选工具栏、表格和分页组成一条纵向工作流
- 四张指标卡在 `lg=6` 时同排，在 `xs=12` 和 `sm=12` 时每行两张
- 三个图表面板在 `lg=8` 时同排，在 `xs=24` 和 `sm=24` 时堆叠
- 两个等权分析面板使用 `lg=12`
- 相关次要面板在大屏采用 `12 / 6 / 6`，小屏堆叠或成对排列

不要给每个区块再套一层外部卡片。页面本身就是工作表面，卡片只用于有明确边界的数据或工具单元。

### 间距

**建议规则：**归纳重复值，但不声称存在严格的 4px 令牌系统。源码也使用 `5px`、`10px`、`18px`、`26px` 和 `30px`；下列名称只是文档别名，不是导出的 SCSS 变量。[S3] [S7]

| 令牌 | 值 | 常见用途 |
| --- | --- | --- |
| `space-1` | `4px` | 标签偏移和极紧凑图标对齐 |
| `space-2` | `8px` | 紧凑内边距、工具栏间隙、窄屏图表内边距 |
| `space-3` | `10px` | 筛选间距和紧凑纵向间隙 |
| `space-4` | `16px` | 卡片内部、行内边距和控件分组 |
| `space-5` | `20px` | 标准页面和卡片内边距 |
| `space-6` | `24px` | 区块分隔和提示区域 |
| `space-7` | `30px` | 全局分页顶部外边距和组件演示纵向外边距 |
| `space-8` | `32px` | 仪表盘内边距和图表分隔 |
| `space-10` | `40px` | 指标卡栅格沟槽 |

同一工作流的纵向间距应一致。列表页和表单页不要使用类似 Hero 的大面积留白。

## 阴影层级

使用浅而有功能意义的阴影：

| 层级 | 阴影 | 用途 |
| --- | --- | --- |
| 顶栏 | `0 1px 4px rgba(0, 21, 41, .08)` | 分隔顶栏 |
| 标签栏 | `0 1px 3px rgba(0,0,0,.12), 0 0 3px rgba(0,0,0,.04)` | 标签栏条带 |
| 卡片 | `4px 4px 40px rgba(0,0,0,.05)` | 仪表盘指标卡 |
| 浮动菜单 | `2px 2px 3px rgba(0,0,0,.3)` | 标签栏上下文菜单 |
| 弹窗 | `0 1px 3px rgba(0,0,0,.3)` | Element UI 模态表面 |
| 固定表格边缘 | `0 0 10px rgba(0,0,0,.12)` | 仅用于固定列 |

大多数结构分隔依靠边框。不要给每张卡片、表格或表单区块都添加重阴影。

### 层叠与浮层归属

| 层级 | 源码值 | 作用范围 |
| --- | --- | --- |
| 固定顶栏 | `9` | Layout 的固定顶栏容器 |
| 移动侧栏遮罩 / 侧栏 | `999` / `1001` | Layout 与侧栏样式 |
| 激活的 vue-multiselect | `1000 !important` | 全局第三方样式覆盖 |
| Element 浮层 | 从 `2000` 开始递增 | 依赖 PopupManager，并非每个弹窗固定为该值 |
| TinyMCE 全屏 | `10000` | 编辑器特定覆盖 |
| 设置遮罩 / 面板 | `20000` / `40000` | 挂在 body 下的自定义 RightPanel |
| 主题选择下拉 / 消息 | `99999 !important` | ThemePicker 覆盖 |

这些是已观察的层级，不是新增浮层的推荐数列。Element 浮层可能低于设置面板；scoped 样式不会自动作用到 body 挂载的 popper 或编辑器 iframe。调整层级前，应在浏览器核对祖先 transform、append-to-body、滚动锁、裁剪、嵌套弹窗及焦点。[S3] [S4] [S6] [S8] [S13] [E2]

## 形状

- 标准输入、卡片和标签使用 `4px`；Element Dialog 使用 `2px`，MessageBox 使用 `4px`。保留各组件自己的圆角。[E1] [E2]
- 紧凑或弱化形状使用 `2px`。
- 分页尺寸/跳页输入使用 `3px`，背景式页码控件使用 `2px`。[E1]
- 圆形只用于状态点、明确设计为圆形的图标按钮、头像和单选控件。
- 顶栏头像为源码特例：`40px` 正方形、`10px` 圆角。
- 除 Element UI 明确的圆角按钮、标签、开关或输入外，不要使用胶囊容器。
- 普通后台卡片和面板避免 `12px+` 大圆角。

## 组件

### 侧栏导航

使用既有路由元数据和 `SidebarItem` 层级。侧栏保持 `210px` 宽，菜单文字 `#bfcbd9`，顶级激活文字 `#409eff`，嵌套背景逐级加深。应用 SVG 图标右侧保留 `16px`，子菜单图标遵循既有 `12px` 间距。

收起到 `54px` 时居中图标，隐藏文字和箭头，通过 Element UI 垂直弹出菜单展示嵌套项。移动端把侧栏视为带黑色 `30%` 遮罩的离屏抽屉，不要压缩成永久显示的迷你栏。

### 顶栏与面包屑

顶栏保持 `50px` 高、白色和轻阴影。左侧放折叠按钮与面包屑，右侧放搜索、错误日志、全屏、全局尺寸和头像菜单；移动端按源码隐藏非必要工具。

右侧图标热区占满顶栏高度，使用 `0 8px` 内边距和 `18px` 图标。悬停背景为 `rgba(0,0,0,.025)`。不熟悉的纯图标操作必须提供工具提示。

### 标签栏

可选标签栏高 `34px`。单个标签高 `26px`，文字 `12px`，边框 `1px`，内边距 `0 8px`，水平间隔 `5px`。激活标签使用 `#42b983`、白色文字和 `8px` 白色状态点。

已有时保留鼠标中键关闭、关闭图标和上下文菜单行为。不要把访问页面改成超大页签或卡片胶囊。

### 导航与设置契约

**源码事实：**路由元数据由导航、权限过滤、面包屑、搜索和缓存共同使用。[S5]

| 契约 | 实际行为 |
| --- | --- |
| `hidden`, `alwaysShow` | 从导航隐藏路由；即使只有一个可见子项也保留父菜单 |
| `redirect: 'noRedirect'`, `meta.breadcrumb=false` | 面包屑不可点击；从路径中省略该项 |
| `meta.roles` | 按角色过滤异步路由；前端过滤不是服务端授权 |
| `meta.title`, `meta.icon` | 提供导航、搜索标题，以及 SVG 或 `el-icon-*` 名称 |
| `meta.activeMenu` | 隐藏编辑路由仍高亮对应列表菜单 |
| `name`, `meta.noCache` | `cachedViews` 保存组件名称，`noCache` 排除缓存；保留路由与组件名称匹配 |
| `meta.affix` | 关闭其他或全部标签时保留固定标签 |
| 路由 path 与 query | 访问标签按 `path` 去重；`router-view` 以 `route.path` 为 key；仅 query 不同不代表独立缓存工作区 |

面包屑按需要补入 Dashboard，使用匹配路由，并保留不可点击项。HeaderSearch 用 Fuse.js `3.4.4` 搜索可访问且有标题的路由，是本地路由搜索，不是后端或业务数据搜索。保留嵌套菜单解析和外部链接。标签提供刷新、关闭、关闭其他、关闭全部，并处理固定页及当前页关闭后的回退。[S5]

`src\settings.js` 默认值：`showSettings=true`、`tagsView=true`、`fixedHeader=false`、`sidebarLogo=false`、`errorLog='production'`。设置面板提供主题色、标签栏、固定顶栏、Logo 开关。Settings 值保存在 Vuex，未实现持久化；侧栏状态 `sidebarStatus` 和 Element 尺寸 `size` 使用 Cookie。不要承诺主题或布局设置刷新后保留。ErrorLog 在启用环境中记录前端 Vue 错误，不是后端运维日志服务。[S2] [S6] [S21]

RightPanel 是自定义右侧设置面板，**不是 `el-drawer`**：宽 `100%`、最大 `260px`、高 `100vh`，手柄 `48px`，默认距顶 `250px`，内容内边距 `24px`。它挂在 body 下，手柄切换开关，外部点击关闭由 `clickNotClose` 决定。没有实现 Esc、焦点陷阱或焦点返回。当前源码没有已路由的业务抽屉页。[S6]

### 按钮

优先使用 Element UI 按钮变体和尺寸，而不是自定义 CSS。

| 尺寸 | 字号 | 内边距 | 圆角 |
| --- | --- | --- | --- |
| 默认 | `14px` | `12px 20px` | `4px` |
| 应用默认 Medium | `14px` | `10px 20px` | `4px` |
| Small | `12px` | `9px 15px` | `3px` |
| Mini | `12px` | `7px 15px` | `3px` |

除非用户保存了其他尺寸，应用把 Element UI 全局尺寸设为 `medium`。主按钮使用 `#1890ff`，成功 `#13ce66`，警告 `#ffba00`，危险 `#ff4949`。按钮字重明确为 `400`。

每个局部任务组只设置一个清晰主操作。破坏性操作保持红色，并在可能丢失数据时要求确认。只有熟悉工具才能使用纯图标按钮，同时提供无障碍名称或工具提示。

### 表单与输入

使用 `el-form`、`el-form-item` 和配套 Element UI 控件。应用实际默认是 Medium：输入高 `36px`、文字 `14px`、圆角 `4px`、白色填充、基础边框 `#dcdfe6`。其他支持尺寸为默认 `40px`、Small `32px`、Mini `28px`。

- 标签应简洁，同一表单内对齐方式一致。
- 占位文字使用 `#c0c4cc`，但不能代替标签。
- 焦点边框使用 `#1890ff`。
- 禁用控件仍保留可见边界，并通过颜色以外方式表达状态。
- 校验错误使用 `#ff4949`，紧邻对应控件。
- 相关字段组成区块，区块之间使用 `20-24px`，不要给每行字段套装饰卡片。
- 保留 Element UI 的键盘、清除、显示密码、自动完成和校验行为。

登录页是明确例外：全高 `#2d3a4b` 背景，表单居中且最大宽 `520px`，透明输入高 `47px`，使用浅色文字和 `5px` 字段组圆角。普通后台表单不得复用登录页样式。

### 选择控件与开关

使用 Element UI 的复选框、单选框、开关、选择器、级联、日期和时间组件。选中与焦点状态使用组件提供的主色或语义色。标签保持 `14px`，复选框紧凑，开关标签靠近控件。已有控件适用时，不要用复选框形按钮或文字按钮表达二元设置。

筛选工具栏里的选择器和日期范围应保持稳定宽度，避免状态变化导致相邻控件位移。项目明确保留日期范围的 inline-flex 布局。

### 筛选工具栏

筛选项直接放在结果表格上方。`.filter-container` 底部内边距为 `10px`；每个 `.filter-item` 使用 inline-block、垂直居中和 `10px` 下外边距。采用 Medium 或 Small 控件、短标签以及可预测的搜索与重置操作。

窄屏时允许控件换成多行，不要让桌面工具栏强制产生横向溢出。

### 表格

结构化数据使用 `el-table`。编译后默认文字 `#606266`，表头 `#909399`，行悬停 `#f5f7fa`；边框简写与边缘颜色不同，详见颜色章节。表头应简洁，数字数据保持一致对齐。[S3] [E1]

- 只有存在批量操作时才使用选择列。
- 状态列应窄且居中；项目使用 `0 10px` 状态单元格内边距。
- 行操作采用 Mini 按钮，并保持操作列宽度稳定。
- 只有明确的高密度 `.small-padding` 表格才把单元格左右内边距降为 `5px`。
- 标签只用于紧凑状态，不要装饰每个值。
- 保留既有选择、排序和分页契约；演示缺少加载或错误恢复时应明确实现。
- 宽表保留内部滚动和关键列可达性。减少可选列或提供详情视图属于建议，不是现成的通用移动表格行为。

### 分页

**源码事实：**复用 `src\components\Pagination\index.vue`。白色容器使用 `padding: 32px 16px`，同时应用全局 `.pagination-container { margin-top: 30px }`，**没有**设置右对齐。默认属性为 `page=1`、`limit=20`、`pageSizes=[10,20,30,50]`、`background=true`、`autoScroll=true`、`hidden=false`、`layout='total, sizes, prev, pager, next, jumper'`。绑定 `page.sync`、`limit.sync`，提供必需的 `total`，处理 `pagination({ page, limit })`。翻页或改变条数后会在 `800ms` 内滚至顶部，除非设置 `autoScroll=false`。[S9]

**依赖继承：**分页文字 `13px`，标准按钮高 `28px`、最小宽 `35.5px`；背景式页码有自己的 `30px` 最小宽和 `2px` 圆角，因此基础 `3px` 令牌不是通用最终值。**建议规则：**窄屏换行或简化次要控件时保留当前页状态；筛选需显式重置到第 `1` 页，并定义删除当前页最后一条后的行为。[E1]

### 卡片与面板

真正有边界的内容使用 `el-card` 或普通白色面板。标准卡片内边距 `20px`、圆角 `4px`、浅色边框。仪表盘指标卡高 `108px`，采用克制的 `4px 4px 40px rgba(0,0,0,.05)` 阴影；图标块内边距 `16px`、圆角 `6px`。

禁止卡片嵌套卡片。图表通常位于白色表面，内边距 `16px 16px 0`，底部间隔 `32px`。标题和操作保持紧凑，让数据成为视觉焦点。

### 弹窗、抽屉与浮层

**依赖继承：**Element Dialog 宽 `50%`，默认距顶 `15vh`，白色背景、`2px` 圆角。标准头部内边距 `20px 20px 10px`、主体 `30px 20px`、底部 `10px 20px 20px`；标题为 `18px/24px`，主体文字 `14px`，没有统一的 `24px` 主体行高。应用覆盖了弹窗的 margin、transform、position，内联 `top` 和 `width` 属性仍需考虑。MessageBox 是圆角 `4px` 的另一组件。[S3] [E2]

Dialog 默认支持遮罩点击、Esc 关闭，以及 `visible.sync`、`before-close` 和关闭事件；确认 loading 与防重复提交由页面负责。它有 dialog ARIA 属性，但没有使用 MessageBox 的 `aria-dialog` 焦点管理实现。不要承诺所有浮层都有焦点陷阱或焦点返回。**建议规则：**取消或失败时保留未保存数据，把确认操作放在最后，显式实现并测试焦点进入、约束和返回。[E2]

短而聚焦的任务使用弹窗，复杂流程使用完整路由。源码有依据的抽屉式壳层只有自定义 RightPanel；新增业务 `el-drawer` 需要明确需求，不能虚构为现有页面。不要把长表格或多阶段表单塞进小弹窗。

### 下拉菜单与上下文菜单

下拉菜单是紧凑白色浮动表面，链接必须铺满菜单项点击区域。上下文菜单使用 `12px` 文字、`5px 0` 外层内边距、`7px 16px` 项内边距、`4px` 圆角和浅灰悬停。操作按常用到破坏性排序，必要时分隔破坏性操作。

### 页签、标签与状态

同页不同视图使用 Element UI Tabs，已访问路由使用标签栏，两者不能混淆。标准 Tag 使用 `12px` 文字、`4px` 圆角和 `0 10px` 内边距。业务状态应稳定映射到成功、警告、危险和信息色，不要临时随意选色。

### 提示、消息与加载

使用 Element UI 反馈组件及其既有语义色和图标。行内校验放在控件旁，页面级失败放在失败内容附近，短暂完成反馈可用 Message。执行破坏性操作前必须确认。加载状态应保持容器尺寸，防止布局跳动。

必须设计空数据、无结果、无权限和错误状态。空白表格主体不是完整状态。

### 上传

按任务复用真实上传封装，并非所有源码上传都使用 `el-upload`。宽 `100%`、高 `200px` 的拖拽覆盖仅作用于 `.upload-container .el-upload`。Element 的进度、成功、失败、移除钩子不等于完整产品重试流程。说明类型和限制，并明确实现恢复路径。[S3] [S16]

**源码事实：**头像裁剪（`ImageCropper`，演示裁剪尺寸 `300x300`）和 Dropzone 使用 `https://httpbin.org/post`；文章和 TinyMCE 上传演示也包含占位端点。`UploadExcel` 是 FileReader/XLSX 本地解析，不是服务端上传：单文件、首个工作表、`onSuccess({ results, header })` 回调；选择器接受 `.xlsx,.xls`，拖拽校验还接受 `.csv`。其拖拽区为 `600x160px`、文字 `24px`，没有完整解析错误和 finally 恢复。存在七牛/Qiniu 上传源码但无对应路由，不能说已安装存储服务。[S16] [S17]

**建议规则：**统一选择和拖拽校验，解析前检查类型和大小，失败保留文件，所有结果下结束 loading，提供重试、移除、键盘选择，并约束固定拖拽区适应容器。验收使用合成的本地文件和模拟端点，绝不向演示服务发送用户文件。

### 仪表盘与图表

图表用于回答运营问题，而不是装饰。仪表盘面板位于 `#f0f2f5` 画布上，图表表面为白色。图例、坐标轴、单位、对比周期、加载、空数据和错误状态必须清晰。颜色同时搭配标签或形状，且同类数据系列跨图表保持稳定。

指标卡只表达一个标签、一个数值，以及最多一个紧凑对比或图标。避免营销文案、超大插画和装饰渐变。

### 图标

应用图标通过 `SvgIcon` 使用仓库 SVG，Element 控件内部使用 Element UI 图标。同一工具栏的描边或填充方式应一致。熟悉工具可用带提示的纯图标，语义不明确的命令使用图标加文字。已有本地图标时，不要手绘替代 SVG。

## 主题与依赖边界

| 主题表面 | 源码行为 | 边界 |
| --- | --- | --- |
| 编译后的 Element 主题 | 导入 theme-chalk 前由 SCSS 覆盖主色、语义色、按钮字重和边框 | 本文基线，不一定是运行时最终样式 |
| Settings ThemePicker | 从 unpkg 下载 `element-ui@<installed version>/lib/theme-chalk/index.css`，派生主色明暗值，注入 `chalk-style` 并扫描 style 标签替换颜色 | 初始 watcher 也可能触发注入，并非只有用户主动换色 |
| `/theme/index` 开关 | 配合自带预编译 `src\assets\custom-theme\index.css` 切换 `body.custom-theme` | 独立演示皮肤，不是完整或自动同步的暗色模式 |
| 侧栏、标签、图表 | 各有显式 SCSS、组件色值和图表系列色 | 不要假设固定值都随 Element 主题改变 |
| 编辑器与上传预览 | TinyMCE iframe 和内容 CSS、CodeMirror rubyblue、Toast UI/Dropzone 样式 | 各自拥有主题和资源边界，需要显式适配 |

ThemePicker 请求仅在 HTTP `200` 时 resolve，无 reject 或超时路径，失败可能让无限时长的编译提示一直显示。注入的完整 Element CSS 可能覆盖编译语义色或组件尺寸；开发 style 标签与生产提取 CSS 的交互也可能不同。**待验证：**最终颜色、连续换色、CDN 失败恢复、body 挂载浮层、custom-theme 交互、图表对比度和编辑器全屏层级。仅检查令牌不能宣称全主题一致。[S8] [S13] [S14] [S15] [S16]

**建议规则：**保留可用的编译主题回退，失败后提示并允许重试，逐一验证主题表面，按组件限定第三方覆盖。增加持久化、暗色模式或替换 CDN 是独立实现决策，不应暗含在视觉修改中。

## 源码页面模式

以下模式描述真实路由和组件，不代表所有演示已具备生产完整性。路由模块是页面清单依据。[S5]

| 模式 | 既有组合与契约 | 生成工作需要补齐的行为 |
| --- | --- | --- |
| 复杂表格 | 筛选、有边框表格、Mini 行操作、分页、新增编辑 Dialog、导出；`published/success`、`draft/info`、`deleted/danger` | 列表失败无 catch/finally；新增更新无 pending 锁；删除只移除本地行，无确认或删除 API [S9] |
| 动态 / 拖拽 / 行内表格 | 复选框选择列，SortableJS 行排序，`originalTitle` 支持取消行内编辑 | 保留行 ID、顺序和取消语义；拖拽和行内成功不代表服务端持久化 [S9] |
| 文章列表 / 新建 / 编辑 | 列表链接到隐藏编辑路由；共享 `ArticleDetail`、Sticky 状态操作栏、元数据表单、预览 URL、图片和 TinyMCE 正文 | 编辑读取使用 API 封装，但发布/草稿只更新本地状态并显示定时通知，没有保存请求或异步保存计时器 [S11] |
| 页面 / 指令权限 | 角色切换演示，元素使用 `v-permission`，动态渲染的标签和表格列使用 `checkPermission` 配合 `v-if` | 保留路由过滤和条件渲染；隐藏 DOM 不是服务端授权 [S5] [permission-demo] |
| 角色管理 | 角色表格及含 Name、Desc、复选 `el-tree` 的 Dialog；`node-key='path'`、children/title 属性；勾选键重建路由树 | 编辑恢复勾选时临时开启 `checkStrictly` 再关闭；删除有确认并调用角色 API。补 pending/error，用户输入名称应按文本渲染，不照搬 HTML 通知 [S12] |
| 登录 | 最大 `520px` 表单、`160px 35px 0` 内边距、账号密码校验、大写锁定提示、显示密码、Enter 提交、loading 和重定向 | 凭据与第三方弹窗是演示；增加并发提交保护并保留错误恢复 [S10] |
| 仪表盘 | admin/editor 角色视图切换；管理员点击指标更新折线数据，另有图表组、交易表、Todo、个人信息内容 | 示例数据和动画不代表实时指标；补单位、加载、失败、空数据和可访问图表摘要 [S7] |
| 个人中心 / 页内标签 | 个人中心 `6/18` 栅格且 `xs=24`，Activity/Timeline/Account 标签；`/tab/index` 同步当前标签到 query 并懒加载表格 | Account 保存只有成功消息，无持久化；保留路由标签与页内标签区别 [S24] |
| 异常与重定向 | 独立 `/401`,`/404`，壳层内 `/error/401`,`/error/404`；401 返回/首页、404 首页；隐藏 redirect/auth 回调工具路由 | 404 为固定 `1200px` 编排；401 是 `800px` 最大宽容器与栅格，不能保证移动端适配 [S19] |
| Excel / ZIP / PDF | 文件名、文件类型/自适应宽度、选中导出、合并表头、导入预览、ZIP 工具、独立 PDF 下载打印路由 | 选中导出在空选择时警告，成功后清除选择；保留列映射、时间格式、选择和下载 loading。没有批量删除流程 [S17] |
| 文档 / 引导 / 图标 / 剪贴板 / 错误日志 / 外部链接 | 资料链接、Driver.js 引导、SVG/Element 图标目录、复制反馈、前端错误演示 | 保留外链行为；引导、复制成功消息和前端错误列表不是后端功能 [S18] [S21] [S22] |

文章 `.sub-navbar` 是源码特定的 `50px` 高、右对齐操作栏，使用蓝色线性渐变；`draft` 和 `deleted` 类使用 `#d0d0d0`。这是既有页面例外，不代表可在整个后台新增渐变。Sticky 默认 `stickyTop=0`、`zIndex=1`；改变顶栏行为时应协调它与壳层的偏移。[S3] [S11] [S18]

### 编辑器与交互工具

| 工具 | 对应版本源码契约 | 适配边界 |
| --- | --- | --- |
| TinyMCE | CDN `tinymce-all-in-one@4.9.3`，默认高 `360`、英文，`input` 输出 HTML，keep-alive 激活/停用时初始化和销毁 | 保留编辑器 ID、内容变化和清理；iframe 内容主题与全屏需单独核对 [S13] |
| MarkdownEditor | `tui-editor 1.3.3`，默认高 `300px`、语言 `en_US`，`input` 输出 Markdown | 不替换成当前 Toast UI API，不假设宿主 CSS 能到达所有编辑器内部 [S14] |
| JsonEditor | CodeMirror `5.45.0`、JSON lint、rubyblue、最小高 `300px`；初始和变更的传入值使用 `JSON.stringify`，`changed` 与 `input` 输出字符串 | 保留对象与字符串边界：外部字符串输入可能再次加引号；等于编辑器文本的回传值被 watcher 跳过；无效 JSON 仍是可编辑文本 [S15] |
| SplitPane / Sticky / BackToTop / CountTo | 可调整分割面板、滚动固定操作面、回顶、数字动画 | 保留测量宽度、监听清理、滚动偏移和稳定尺寸；有意识地补键盘或减弱动效替代 [S18] |
| DragDialog / DragSelect / DndList / Kanban | 弹窗拖拽指令、已选标签排序、双拖拽列表、SortableJS/vuedraggable 分组列 | 保留标识、选中和分组规则；鼠标拖拽不等于无障碍排序或后端持久化 [S18] |
| 图表 | ECharts `4.2.1`，keyboard/line/mixed 路由及仪表盘；resize mixin 监听窗口和侧栏过渡 | 保留释放和 resize；图表名 keyboard 不代表已实现键盘无障碍 [S7] [S18] |

## 交互与恢复

| 状态 | 源码 / 依赖证据 | 完整生成流程的建议 |
| --- | --- | --- |
| 默认、悬停、激活、选中 | Element 变体和编译主题；路由、侧栏、标签激活状态 [S3] [S5] [E1] | 使用组件 API 并保留选择语义，不改成装饰色 |
| 焦点与键盘 | Element 按组件提供处理；全局链接和 div 移除轮廓 [S3] [E2] | 恢复可见焦点，测试完整任务而非单个组件 |
| 禁用与 pending | Medium 继承禁用样式，按钮支持 loading；登录和导出有局部 loading [S9] [S10] [S17] | 处理函数也要加操作锁，不只禁用按钮；finally 释放，明确取消和导航策略 |
| 空数据与无结果 | Element table 提供空文字；演示列表主要只传数据/loading [E1] [S9] | 区分无数据、无筛选匹配和请求失败；保留筛选并提供清除、重置、重试 |
| 校验失败 | 登录和 ArticleDetail 使用表单规则；复杂表格打开 Dialog 时清理校验 [S9] [S10] [S11] | 保留字段值，显示相邻错误，聚焦首个无效字段，阻止无效 API 提交 |
| 请求失败 | Axios 封装显示 5 秒错误 Message 后 reject，不重置页面 loading 或保存重试状态 [S20] | 安全时保留旧数据，局部持续显示失败与重试，防旧请求覆盖新查询 |
| 成功与取消 | 复杂表格在 API 封装后通知，行内取消恢复 `originalTitle`，不少编辑页是模拟成功 [S9] [S11] | 实际操作成功后才提示，错误保留草稿，关闭后返回焦点 |
| 批量与危险操作 | 有 Excel 选中导出和角色删除确认；复杂表格删除没有确认 [S12] [S17] [S9] | 明确影响条数和范围，不可逆操作前确认，区分取消与失败；接入真实批量 API 时处理部分失败 |

**源码数据契约：**`src\utils\request.js` 使用 `timeout: 5000`、发送 `X-Token`，以 `res.code === 20000` 判断成功。`50008`、`50012`、`50014` 提供重新登录确认，确认后清除 token 并刷新。网络和业务错误都会 reject。除非明确要求改变，否则保留响应封装、取消语义、认证和 Vuex/权限集成。演示的生产 `main.js` 还会启用 MockJS，因此成功不代表已部署真实后端。[S2] [S20]

## 无障碍与内容

**源码限制：**`a:focus`、`a:active`、`div:focus` 移除轮廓；`SvgIcon` 对辅助技术隐藏 SVG，部分自定义点击目标仍是 div/span。MessageBox 有焦点管理代码，RightPanel 和 Element Dialog 并不共享这套实现。Tooltip 不自动等于按钮无障碍名称。没有完整减弱动效或 WCAG 合规实现。[S3] [S6] [S22] [E2]

**新增工作建议：**使用语义按钮、链接和关联标签，为纯图标提供无障碍名称；实现可见焦点、合理 Tab 顺序和 Enter/Space 激活。逐浮层测试 Esc、焦点进入/返回和背景交互。排序工具提供键盘替代，图表提供文本摘要。为辅助技术暴露加载、错误和成功，避免重复播报。尊重 `prefers-reduced-motion`，覆盖 CountTo、图表动画、路由、侧栏和分页滚动。

**已计算的令牌限制，不是页面渲染审计：**白色与编译主色 `#1890ff` 对比度约 `3.24:1`，`#909399` 与白色约 `3.08:1`，不满足普通文本 `4.5:1`。保留原始颜色作为证据；无障碍改良应确认并测试局部对比度调整，包含悬停、禁用/焦点和主题，不能声称原配色已满足 AA。[S3] [E1]

| 内容 | 源码行为 | 建议 |
| --- | --- | --- |
| 日期与时间 | `parseTime` 使用本地 Date getter，十位时间戳从秒转毫秒，默认 `{y}-{m}-{d} {h}:{i}:{s}`；`formatTime` 含中文相对时间 | 明确时区、无效/缺失回退及精确日期入口；不静默改变 API 单位，不把显示字符串当 UTC [S23] |
| 数字 | `numberFormatter` 使用 `k/M/G`，`toThousandFilter` 千位分组，`timeAgo` 使用英文 | 保留存储精度，显示单位/币种，缩略时可查看完整值 [S23] |
| 语言 | Element UI 默认英文，应用标签和工具函数混合多语言，没有完整语言切换 | 双语规范不等于应用已实现 i18n；核对长中英文标签、标点和日期控件 [S2] [S23] |
| 状态与长文本 | 复杂表格状态键映射 Tag 类型；部分标题使用 Tooltip 和固定列 | 保留后端枚举键，颜色配合标签，字段标签允许换行；截断内容应可通过键盘/触摸查看，不只支持悬停 [S9] |
| 富文本 | TinyMCE 输出 HTML，角色通知插入 HTML，Markdown/JSON 各有输出类型 | 把后端/用户内容视为不可信，在渲染边界净化富 HTML，不把普通名称拼入 HTML 通知 [S12] [S13] [S14] [S15] |

## 资源与保留规则

**源码事实：**应用图标来自 `src\icons\svg` 的 SVG sprite，经 `svg-sprite-loader` 加载并以 `#icon-<name>` 引用；Element 控件使用包内 `lib\theme-chalk\fonts` 图标字体。正文字体使用系统字体，不是捆绑的商业字体。`src\assets` 包含异常页本地图片和自定义主题资源；演示还使用外部 `wpimg.wallstcn.com` 图片、TinyMCE/unpkg CDN 和引用 Material Icons 的 Dropzone 预览标记。外部图片/字体的可用性及独立使用权均**待验证**。[S1] [S3] [S16] [S22]

上游应用与 Element UI 声明 MIT 许可，本仓库原创文档也采用 MIT；这不自动授权再分发第三方照片、标识、图标集、编辑器包或 CDN 资源。保留上游声明，逐项核对复用资源和依赖许可，优先使用已验证的本地资源。不得把已忽略的参考源码、凭据、模拟 token、用户上传或生成依赖树打包进文档仓库。

视觉修改必须保留路由 name/path/meta、权限过滤与服务端授权边界、`X-Token` 和响应封装、Vuex 键、组件事件与 `.sync`、编辑器序列化、行标识/顺序、表单校验和导出列映射。演示端点不是生产契约。改变这些内容或升级依赖不属于本次规范更新。

## 响应式行为

### 断点

| 边界 | 源码行为 |
| --- | --- |
| `<= 470px` | 登录页 `max-width: 470px` 隐藏第三方操作 |
| `<= 550px` | 指标卡 `max-width: 550px` 隐藏整个说明区（标签和数值），居中图标而非说明 |
| `<= 767px` | Element UI `xs` 使用 `max-width: 767px`，只有显式配置的栅格跨度响应 |
| `>= 768px` | Element UI `sm` |
| `rect.width - 1 < 992` | 应用移动模式精确判断；整数宽度 `<= 992px` 仍移动，`993px` 是桌面 |
| `>= 992px` | Element UI `md`，在 `992px` 栅格 `md` 与移动壳层并存 |
| `>= 1200px` | Element UI `lg`，使用完整仪表盘栅格 |
| `>= 1920px` | Element UI `xl`，选择性利用额外宽度，不拉伸所有表单 |

仪表盘在 `1024px` 及以下减少图表内边距。这是局部密度调整，不是第二套应用壳层断点。窗口调整进入移动模式时无动画关闭侧栏；移动端打开侧栏后发生导航也会关闭。JS 判断使用 body 的 bounding-rect 宽度，不是 Element 栅格媒体查询。[S4] [S7] [S10] [E1]

### 移动端规则

- 清除主内容左外边距。
- 侧栏关闭时使用 `translate3d(-210px, 0, 0)` 移出屏幕。
- 侧栏打开时显示黑色、`30%` 不透明度的全页遮罩。
- 隐藏非必要顶栏工具，但保留导航与用户菜单。
- **建议规则：**相关栅格堆叠，筛选控件允许换行，源码不会自动让所有表单响应式。
- **建议规则：**核心行操作可达，使用表格内部滚动或经过设计的列/详情策略。
- **建议规则：**避免页面级溢出但保留宽数据查看能力，视觉紧凑时仍保证触控可用。

已知固定宽度：复杂表格 Dialog 表单 `400px` 加左外边距 `50px`、操作列 `230px`；UploadExcel 拖拽区 `600px`；404 编排 `1200px`；Element Dialog 默认宽 `50%`；组件演示外边距 `30px 50px`。新增响应式实现应约束表单适应可用宽度、允许长标签换行、让弹窗保留视口边缘空间，并测试表格和浮层溢出。在 `550px` 以下保留指标标签和值是明确的可用性改善，而不是复现源码。[S3] [S9] [S17] [S19]

## 动效

- 边框和颜色过渡：`0.2s`，使用 Element UI 标准缓动。
- 侧栏宽度和主内容偏移：`0.28s`。
- 顶栏和图标悬停背景：`0.3s`。
- 标签栏关闭控件：`0.3s`，使用 Element UI cubic-bezier 曲线。
- 路由淡入淡出：`0.28s`；路由位移和面包屑过渡：`0.5s`。
- 仪表盘图标悬停：`0.38s ease-out`。

动效用于说明状态或空间变化。源码未提供完整减弱动效模式，新增工作应补充并测试。分页滚动为 `800ms`，Element Dialog 淡入位移为 `.3s`；演示用 `600ms` 自定义按钮和 `1.5s` Logo 淡入是局部例外，不要推广为全部过渡默认值。[S3] [S7] [S9] [E2]

## 应做 / 禁止

### 应做

- 使用 Element UI 2.13.2 组件和既有 Vue 2 模式。
- 保留 `210px / 54px` 侧栏及 `50px + 34px` 顶部几何关系。
- 应用主操作使用 `#1890ff`，侧栏激活状态使用 `#409eff`。
- 列表页按筛选工具栏、结果表格、分页组织。
- 在克制灰色画布上使用白色工作表面。
- 保持字体紧凑、信息易扫描。
- 补齐加载、空数据、校验、错误、禁用和无权限状态。
- 在 `991px`、`992px`、`993px` 验证桌面和移动布局，包含 `992px` 的栅格与壳层差异。

### 禁止

- 除非任务明确要求，否则不得迁移到 Vue 3、Element Plus、其他组件库或工具类框架。
- 不要把深色侧栏替换成浮动导航卡片。
- 后台页面不使用超大 Hero 标题、营销文案、装饰插画或沉浸式落地页构图。
- 不要把每个区块都放进圆角卡片，也不要嵌套卡片。
- 不要引入大胶囊圆角、玻璃拟态、重渐变或密集阴影。
- 不要只靠颜色表达状态。
- 不要为了让移动端截图显得空旷而隐藏核心操作。
- 不要把视觉调整变成对路由、权限、API 或状态契约的修改。

## Agent 提示词指南

### 新建页面

```text
完整读取所选 4.3.1 DESIGN.md。使用 Vue 2.6.10 和 Element UI 2.13.2，选择匹配的源码页面模式：列表、编辑、个人中心、仪表盘、登录或异常。保留路由、权限、API、Store 和组件事件。区分源码事实、依赖继承、建议规则和待验证事项。补齐需求中的加载、空数据、失败重试、校验和防重复提交，不把演示保存当持久化。核对主题及移动边界，说明验证限制。
```

### 修改既有页面

```text
请先读取 DESIGN.md 并检查现有页面。保持 API、路由、权限、校验、Store 和序列化契约不变，在 vue-element-admin 4.3.1 体系内完成需求中的最小 UI 改动。复用 Element UI 和本地 SVG，核对 991/992/993px、窄屏、长文本、主题、浮层和恢复状态。区分静态检查与真实浏览器证据，不升级依赖或复制演示中的漏洞。
```

### 审查清单

```text
请按照 DESIGN.md 审查这个界面，报告应用壳层几何、令牌使用、组件选择、间距、字体层级、表格工作流、响应式行为、无障碍和状态覆盖方面的偏差。区分源码支持的要求与可选改进，不要建议迁移框架。
```

## 已知缺口

- vue-element-admin 4.3.1 属于 Vue 2 与 Element UI 2.13.2 系统，其视觉规则不能直接作为 Vue 3 或 Element Plus 契约。
- 源码以桌面端为先，移动判断精确表达式为 `rect.width - 1 < 992`。固定宽度演示和移动端隐藏指标值仍属于上游限制。
- 上游源码没有完整定义无障碍令牌、减少动态效果、最小触控尺寸和全部键盘流程。新增功能应在不改变既有行为的前提下改善这些方面。
- 仓库包含演示页面和仅供演示的替代主题。核心壳层和编译主题文件的证据优先级高于一次性示例。
- 上游间距具有重复规律，但没有正式令牌体系。本文间距表是对观察值的归纳；更具体时应保留项目本地约定。
- Element 默认启用英文，但应用和辅助函数文案混合多语言；双语文档不是应用国际化。
- 图表源码提供示例，而不是完整的数据可视化标准。单位、图例、无障碍标签和系列语义应由产品领域补充。
- 运行时主题级联、外部资源、完整键盘焦点流程、响应式截图、后端持久化和已解析依赖树均待验证。本次没有安装依赖、运行前端或进行 UI 验收。

## 验收边界

文档验收检查 UTF-8、解析后的元数据、双语元数据/令牌/规则一致、证据链接、路由模块覆盖和版本仍为 `4.3.1`。源码验收检查上游提交、声明依赖版本、CSS 数值、断点表达式、属性事件、模拟与 API 操作区别以及仓库范围。这些检查不证明浏览器视觉正确。

实现需要运行证据时，应使用合成数据和受控端点。测试 `375px`、桌面 `1440px`，以及 `470/550/768/992/1024/1200px` 各边界两侧（尤其 `991/992/993px`），覆盖侧栏开关、标签栏与固定顶栏组合、长中英文内容、受限弹窗与表格。检查编译/CDN/custom 主题、CDN 失败、嵌套浮层和编辑器全屏、键盘焦点、减弱动效。覆盖加载、空数据、无效、失败、重试、成功、重复提交、取消删除和空选择/已选择导出。宣称 UI 验收前记录截图、断言、环境及剩余缺口。

## 来源说明

本规范是基于 vue-element-admin 官方 `4.3.1` 标签和 Element UI `2.13.2` 独立整理的源码派生参考，不是官方文档，也不代表 vue-element-admin、Element UI 或 Google Stitch 的背书。

### 版本化证据索引

下列应用链接固定到本次审计提交。目录链接归集紧密相关文件，每行列出应核对的路径。依赖链接使用准确的 npm 发布版本，不是最新文档。

| ID | 来源及覆盖文件 |
| --- | --- |
| S1 | [package.json][S1]：应用和依赖固定版本；上游 LICENSE 位于同一提交 |
| S2 | [src\main.js][S2]：导入顺序、语言、尺寸 Cookie 和生产 MockJS |
| S3 | [src\styles][S3]：`element-variables.scss`、`variables.scss`、`index.scss`、`element-ui.scss`、`sidebar.scss`、`transition.scss`、`btn.scss` |
| S4 | [src\layout][S4]：`index.vue`、`components\AppMain.vue`、`Navbar.vue`、`Sidebar`、`mixin\ResizeHandler.js` |
| S5 | [src\router][S5]：`index.js`、`modules`；另见 [Tags Store][tags-store]、[Breadcrumb][breadcrumb]、[HeaderSearch][search]、[TagsView][tags-view]、[权限守卫][permission] |
| S6 | [src\settings.js][S6]、[RightPanel][right-panel]、[Settings][settings-panel]、[settings Store][settings-store]、[app Store][app-store] |
| S7 | [src\views\dashboard][S7]：角色切换、admin/editor、PanelGroup、图表和 resize mixin |
| S8 | [ThemePicker][S8]、[主题页][theme-page]、[custom-theme CSS][custom-theme] |
| S9 | [src\views\table][S9]：复杂/动态/拖拽/行内表格；[Pagination][pagination] |
| S10 | [src\views\login\index.vue][S10] |
| S11 | [src\views\example][S11]：list/create/edit 和 `components\ArticleDetail.vue` |
| S12 | [src\views\permission\role.vue][S12] |
| S13 | [src\components\Tinymce][S13]：编辑器、工具栏和插件、CDN 脚本及图片上传 |
| S14 | [src\components\MarkdownEditor\index.vue][S14] |
| S15 | [src\components\JsonEditor\index.vue][S15] |
| S16 | [src\components][S16]：Upload、ImageCropper、Dropzone、UploadExcel；[上传演示][demos] |
| S17 | [src\views\excel][S17]、[ZIP][zip]、[PDF][pdf]、[导出工具][vendor] |
| S18 | [src\views\components-demo][S18]、[图表][charts]、[引导][guide]、[剪贴板][clipboard]；对应本地封装和指令 |
| S19 | [src\views\error-page][S19] |
| S20 | [src\utils\request.js][S20] |
| S21 | [src\utils\error-log.js][S21]、[ErrorLog 组件][error-log] |
| S22 | [src\icons][S22]、[SvgIcon][svg-icon]、[assets][assets] |
| S23 | [src\utils\index.js][S23]、[filters][filters] |
| S24 | [src\views\profile][S24]、[标签页][tab] |
| E1 | [Element 2.13.2 主题变量][E1]、[表格样式][element-table]、[分页样式][element-pagination] |
| E2 | [Dialog 样式][E2]、[Dialog 组件][element-dialog]、[MessageBox][element-messagebox]、[PopupManager][element-popup] |

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
