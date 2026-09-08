# vue-element-admin 4.3.1 规范审计与更新记录

审计日期：2026-09-08。版本继续使用 `4.3.1`，不新增修订版本号。本记录用于说明本次文档修正及证据，不是前端漏洞修复报告或 UI 验收报告。

## 总体结论

原规范能约束普通列表、表单和仪表盘的基础视觉，但不足以单独指导精确响应式、主题切换、角色权限树、富文本工具、导入导出和完整状态恢复。主要风险不是篇幅不足，而是将归纳建议写成源码默认行为、遗漏真实页面组合，以及把组件支持与页面实际实现混为一谈。

本次已在同一版本中同步修正中英文规范，补充证据分类、来源优先级、页面模式、状态恢复、资源许可和验收边界。更新后可作为这些场景的静态实现上下文，但不能仅凭文档保证运行时主题、移动端渲染、可访问性或真实后端行为。

## 审计基线与边界

- 文档仓库：[turtoncarllyle/vue-element-admin-design-md](https://github.com/turtoncarllyle/vue-element-admin-design-md)，本地 `E:\github\admin-ui-design-md\vue-element-admin-design-md`，分支 `main`。
- 更新前本地、远端和 `v4.3.1` 标签均为 [`32169bd2fe6f1691ab9e630c6964b5bf94a82959`](https://github.com/turtoncarllyle/vue-element-admin-design-md/tree/32169bd2fe6f1691ab9e630c6964b5bf94a82959)，工作区干净，仅跟踪六个文档/元数据文件。
- 本地前端参考：`vue-element-admin-4.3.1`，已被 `.gitignore` 排除。本次未改动或提交前端源码，不涉及相邻其他 `*-design-md` 仓库。
- 上游真实标签为 [`4.3.1`](https://github.com/PanJiaChen/vue-element-admin/tree/4.3.1)，不带 `v`；提交 [`f6d8204b0b6fbb794ada0c99391b7b85ce976380`](https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380)。通过 Git blob hash 与递归 tree 比较全部 307 个文件，差异 0。
- `package.json` 固定 Vue `2.6.10`、Element UI `2.13.2`、Vue Router `3.0.2`、Vuex `3.1.0`、ECharts `4.2.1`。没有锁文件或 node_modules，不能宣称完整依赖树已复现。
- Element UI 从 npm `2.13.2` 发布包临时读取，核对 registry SHA512 完整性后检查源码；没有安装前端依赖。
- 用户提供的 [v4.0.0](https://github.com/PanJiaChen/vue-element-admin/tree/v4.0.0) 是历史参考，当前本地没有该目录；本次不宣称做过两个版本的完整差异核对。
- 参考任务：[设计 layui 2.13.9 规范并推送](codex://threads/019ffe2b-3393-71c1-87b8-8909411ea54e)。只借鉴双语和同版本维护方式，不把 Layui 内容引入本规范。

## 问题清单

严重度表示对 Agent 生成结果的影响，不是对前端进行的安全评级。原文位置均指上述首发提交中的双语同名章节；当前对应章节已同步修正。

| ID / 优先级 | 原文问题及位置 | 可核实证据 | 影响与本次处理 | 验证方式 |
| --- | --- | --- | --- | --- |
| A01 / P1 | Responsive Behavior 把壳层写成 `<992px`，把 KPI 小屏描述写反，470/550 未含边界 | [ResizeHandler.js](https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/layout/mixin/ResizeHandler.js) 的 `rect.width - 1 < WIDTH`；[PanelGroup.vue](https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/dashboard/admin/components/PanelGroup.vue) 的 `max-width:550px`；登录页 `max-width:470px` | 992px 会被误判为桌面；新增页面可能丢失 KPI 信息。改为精确表达式和隐藏整块说明事实，保留数值标为改善 | 静态表达式与媒体查询核对；运行时测试 991/992/993 和 549/550/551 待做 |
| A02 / P1 | Source of Truth / Colors 只弱提示演示主题，缺运行时全量 CSS 注入边界 | [ThemePicker](https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/ThemePicker/index.vue)、`src\views\theme\index.vue`、`src\assets\custom-theme\index.css` | 会把编译色当最终主题、误称完整暗色或忽略失败常驻消息。补初始 watcher、CDN、级联、第三方及失败限制 | 静态核对请求和注入；连续换色、CDN 故障与生产样式级联待浏览器验证 |
| A03 / P1 | Tables / Feedback 泛称保留完整状态，没有指出页面缺失；编辑器保存模式缺失 | [complex-table.vue](https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/table/complex-table.vue)、[ArticleDetail.vue](https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/example/components/ArticleDetail.vue)、`src\utils\request.js` | 可能复制无 finally、无防重、无删除确认或假保存。新增状态矩阵，区分 API 封装、模拟本地反馈、生产 MockJS 和建议恢复路径 | 核对调用链、reject、状态更新；真实持久化和异常注入待实现时验证 |
| A04 / P1 | Overlays 把焦点管理视为统一既有行为，误导无障碍验收 | [Element Dialog](https://unpkg.com/element-ui@2.13.2/packages/dialog/src/component.vue)、[MessageBox](https://unpkg.com/element-ui@2.13.2/packages/message-box/src/main.vue)、`src\components\RightPanel\index.vue`、`src\styles\index.scss` | Dialog/RightPanel 不共享 MessageBox 焦点管理；全局移除部分 outline。分开依赖事实和新增焦点/键盘要求，记录对比度限制 | 依赖源码核对；令牌对比度计算通过；实际键盘、读屏与焦点返回待验证 |
| A05 / P2 | Pagination / Shapes / Dialogs 的对齐、圆角、内边距和行高泛化不正确 | [Pagination](https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/Pagination/index.vue)、[Dialog SCSS](https://unpkg.com/element-ui@2.13.2/packages/theme-chalk/src/dialog.scss)、分页 SCSS | 分页并不默认右对齐，wrapper `32px 16px`；Dialog `2px` 而 MessageBox `4px`，标题24px不等于主体行高。已修正属性、事件、滚动和组件差异 | 源码属性、全局与局部 CSS 叠加核对；不宣称截图一致 |
| A06 / P2 | Typography / Spacing / Colors 把归纳层级当全局令牌，表格边框简化为一个颜色 | [styles](https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/styles)、[Element var.scss](https://unpkg.com/element-ui@2.13.2/packages/theme-chalk/src/common/var.scss) | body 没有全局14/24，label为700，间距不是严格4px；边框简写与颜色令牌不同。增加元数据范围和组件优先级 | 逐项检查声明与消费位置，双语元数据结构化比较 |
| A07 / P2 | Application Shell / Navigation 缺元数据、缓存、搜索和设置持久化契约，抽屉类型不清 | [router](https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/router)、`src\layout`、`src\store\modules`、HeaderSearch、RightPanel | 可能破坏 activeMenu、affix、route/component name 和 query 行为。补 fixedHeader 补偿、默认设置、Cookie/Vuex 差异及真实自定义设置面板 | 核对路由消费者与 Store；无混合布局或业务抽屉标为不适用 |
| A08 / P2 | Components 缺角色树、页面/指令权限和三类编辑器的契约 | [role.vue](https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views/permission/role.vue)、`src\views\permission\directive.vue`、`src\components\Tinymce/MarkdownEditor/JsonEditor` | 树勾选会被错误简化；HTML/Markdown/JSON 字符串和对象可能混淆；角色 HTML 通知不应复制。补数据边界、焦点和安全渲染建议 | 核对 node-key/checkStrictly、事件/序列化、权限条件渲染；外部编辑器执行待验证 |
| A09 / P2 | Uploads 泛化为 el-upload，缺本地 Excel 与远端演示端点的区别 | [UploadExcel](https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/UploadExcel/index.vue)、Dropzone、ImageCropper、Excel/ZIP/PDF 页面 | 接受类型不一致、固定600px、解析异常无恢复；可能误传文件到 httpbin。补首sheet/回调、类型和合成文件验收边界 | 静态读取处理函数；未上传文件或调用演示写接口 |
| A10 / P2 | 覆盖范围缺 profile、401/404、动态/拖拽/行内表格、导出、页内标签等真实组合 | [src\views](https://github.com/PanJiaChen/vue-element-admin/tree/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/views) 与 router 模块 | Agent 容易把所有页面做成通用列表，忽略固定宽度风险。补页面模式和交互工具表，并指出无持久化/无移动保证 | 逐路由归类并核对目标组件；不以章节数或关键词计为完整 |
| A11 / P2 | Known Gaps / Icons 缺日期单位、混合语言、资源许可与危险 HTML 边界 | `src\utils\index.js`、`src\filters\index.js`、[SvgIcon](https://github.com/PanJiaChen/vue-element-admin/blob/f6d8204b0b6fbb794ada0c99391b7b85ce976380/src/components/SvgIcon/index.vue)、`src\assets` | 时间单位/时区、枚举、图标名称和资源权利易被误改。补格式及资源表，不承诺 i18n 或第三方图片已授权 | 源码逻辑核对；未对外部素材做完整许可或可用性验收 |
| A12 / P2 | README 和 Provenance 未区分同版本维护内容、首发标签和附件，来源不够可追溯 | 原 `v4.3.1` 指向 `32169bd`，原两个附件在 2026-08-14 发布 | 直接覆盖会丢历史，保留却不说明会下载旧文档。更新读取说明、固定上游提交、日期附件及 SHA 固定方式 | 推送后核对 main、标签、Release 说明、附件哈希及中英文仓库描述 |

没有发现需要改动的部分：编译主色/语义色、侧栏 `210px/54px`、顶栏 `50px`、标签栏 `34px`、应用默认 Medium 和主体栅格模式均与 `src\styles`、`src\layout`、`src\main.js`、PanelGroup 对应源码一致。保留这些值，仅补作用范围与边界。

## 覆盖矩阵

状态针对文档能否说明已存在的模块，不代表前端能力完整或运行验收通过。“完整”限于本次静态核对边界；“部分覆盖”表示仍依赖宿主业务或运行证据。

| 模块 | 更新前 | 更新后 | 当前依据与限制 |
| --- | --- | --- | --- |
| 目的、读取、非目标、Agent 提示词 | 部分覆盖 | 完整 | README + 规范概览，按页面选模式和四类证据 |
| 版本、上游来源、依赖边界 | 部分覆盖 | 部分覆盖 | 固定 commit/声明版本；无完整依赖解析树 |
| 颜色与组件主题令牌 | 部分覆盖 | 完整 | 编译基线、表格边缘例外和运行覆盖分开 |
| 字体、间距、尺寸、形状、阴影、动效 | 部分覆盖 | 完整 | 明确归纳值与真实声明，不虚构全局行高 |
| 侧栏、顶栏、固定头、移动遮罩 | 部分覆盖 | 完整 | 精确几何、设置默认值、补偿与断点表达式 |
| 面包屑、搜索、标签与缓存 | 部分覆盖 | 完整 | router 消费者、path/name/query/affix 合同 |
| 混合布局、业务 el-drawer | 不适用 | 不适用 | 当前路由和布局未实现；RightPanel 单独记录 |
| 设置面板与层级 | 缺失 | 完整 | 类型、属性、挂载、层级、持久化和焦点限制 |
| 编译主题、ThemePicker、custom-theme | 部分覆盖 | 部分覆盖 | 静态机制完整；最终级联、CDN 故障待验证 |
| 按钮、输入、选择、日期和表单 | 部分覆盖 | 完整 | Element 继承和源码例外；产品业务校验另定 |
| 表格、筛选、分页 | 部分覆盖 | 完整 | 四类表格、分页事件和缺失恢复的明确建议 |
| 角色树、页面和指令权限 | 缺失 | 完整 | path/checkStrictly、条件渲染和服务端授权边界 |
| Dialog、MessageBox、上下文菜单 | 部分覆盖 | 完整 | 各自形状、层级、关闭与焦点行为分开 |
| 登录、文章编辑、个人中心、页内标签 | 部分覆盖 | 完整 | 实际组合、回退和模拟保存限制 |
| admin/editor 仪表盘、图表 | 部分覆盖 | 部分覆盖 | 静态组合和 resize；业务单位、实时状态另定 |
| 401/404、redirect/auth 回调 | 缺失 | 完整 | 独立与壳层路由、返回入口、固定宽风险 |
| TinyMCE、Markdown、JSON | 缺失 | 完整 | 精确版本、输出类型和主题/生命周期边界 |
| 上传、Excel、ZIP、PDF | 部分覆盖 | 完整 | 本地解析、占位远端、列映射和合成测试要求 |
| SplitPane、Sticky、拖拽、CountTo、BackToTop | 缺失 | 部分覆盖 | 使用契约和适配边界已补；第三方完整交互待运行 |
| Guide、文档、图标、剪贴板、ErrorLog、外链 | 部分覆盖 | 完整 | 真实工具用途，不虚构后台服务 |
| 失败、空数据、防重、确认与恢复 | 部分覆盖 | 部分覆盖 | 已标源码缺失并给出规则，尚未改动前端实现 |
| 窄屏表单、宽表、长文本 | 部分覆盖 | 部分覆盖 | 风险与补充策略明确，未做响应式 UI 验收 |
| 无障碍、对比度与减弱动效 | 部分覆盖 | 部分覆盖 | 计算原令牌并记录代码缺陷；真实键盘/读屏待验证 |
| 日期、数字、状态、语言 | 缺失 | 完整 | 本地时区/秒毫秒、格式助手、混合语言与枚举 |
| 图片、字体、第三方许可 | 部分覆盖 | 待验证 | 已建立边界，尚无逐资源权利证明 |
| 双语一致、稳定链接、发布追溯 | 部分覆盖 | 完整 | 同版本目录、对应章节和共享来源，历史标签保留 |

## 本次实施映射

| 优先级 | 修改文件 | 具体内容 |
| --- | --- | --- |
| P1 | `versions\4.3.1\DESIGN.md`、`DESIGN.zh-CN.md` | 修正断点/主题/保存/焦点事实；新增四类证据、交互恢复矩阵、主题及依赖边界 |
| P2 | 同上 | 修正分页/Dialog/字体/表格令牌；补导航设置、层级、页面模式、角色树、编辑器、上传导出、内容与资源、固定来源和验收边界 |
| P2 | `README.md`、`README.en-US.md` | 补读取步骤和提示词、审计入口、同版本维护与首发快照区别、未验证范围 |
| P2 | `versions\4.3.1\AUDIT.md` | 保存本审计、问题及处理、模块覆盖、版本策略和可复核验收清单 |

不修改 `.gitignore`、LICENSE、前端源码、业务逻辑、依赖、其他仓库；不新增上游版本目录。

## 版本与发布策略

这是 `4.3.1` 规范的内容维护，不是前端升级。文档 `version`、目录、现有标签和 Release 名称保持不变，没有 `4.3.1.x`、`rev` 或其他新修订编号。新增 `updated` 日期和 Git 提交提供追踪。

`main` 保存维护内容；原 `v4.3.1` 标签仍指向首发提交。原附件和 GitHub 自动生成的 Source code 压缩包仍代表首发快照。在同一个 Release 追加本次提交链接、日期标记的双语规范及审计附件，保留原附件名称、ID 和内容。不删除、不移动标签，不覆盖原附件。

原附件 SHA256 基线：

| 附件 | SHA256 |
| --- | --- |
| `DESIGN.md` | `e87ae1393a96a86043d40ad43d748dfb9d3bd10de2177c1703dfab058d78c62c` |
| `DESIGN.zh-CN.md` | `db287897b89d9edf3ea5a3efaa1a8abb15998bdaa19df3537315e0c5a95b8151` |

## 验收标准与已验证范围

| 类别 | 本次静态验收 | 不应替代的验证 |
| --- | --- | --- |
| 文件与文档 | UTF-8 严格解码；YAML 实际解析；双语非翻译元数据、色值、尺寸、代码契约、证据集合对应；Markdown 引用和本地链接检查；`git diff --check` | 不能仅以同章节或同关键词宣称语义完整，仍需逐条阅读双语规则 |
| 源码 | 307 文件官方 hash 比对；包版本；源码数值/表达式/属性/事件和行为调用核对；Element npm 完整性与消费位置 | 未安装/构建前端，未解析全部传递依赖，不代表实际 CSS 编译结果 |
| 内容对比度 | 用 sRGB 相对亮度公式计算白色对 `#1890ff` 约 `3.24:1`、白色对 `#909399` 约 `3.08:1` | 不是全页面 WCAG 或主题对比度验收 |
| 发布 | 只提交本次五个文档；推送后核对 main 提交和 blob、原标签、附件哈希与原始说明保留；仓库描述保持中英文 | 标签及首发附件不是本次最新快照，必须结合 Release 说明选取 |

已执行的静态检查结果：5 个文件严格 UTF-8 解码通过；双语 YAML 解析后非翻译字段一致；352 种代码/数值字面量及出现次数对应；56 个证据引用定义一致；420 处 Markdown 链接引用完成本地路径或固定来源路径核对；47 项源码/依赖断言通过；991/992/993 的移动判断分别为 true/true/false；`git diff --check` 通过。另已逐条核对双语规则和页面组合。以上数字用于复核检查过程，不作为知识完整性评分，也不代表所有外部 URL 的实时可用性或 UI 通过。

运行验收清单留给实际前端实现，不在本次假称已通过：

1. `375px`、`1440px`，470/550/768/992/1024/1200 边界两侧，特别是 `991/992/993px`；检查长中英文、页面横向溢出、表格内部滚动和弹窗边缘。
2. 侧栏开关、标签栏/固定顶栏各组合、弹窗滚动锁、路由缓存与 query 变化、角色切换及 activeMenu。
3. 默认编译主题、初始 CDN 注入、连续换色、CDN 超时/非200、custom-theme、body 挂载浮层和第三方编辑器全屏。
4. 完整键盘和读屏路径、可见焦点、Esc、焦点进入/返回、排序替代、图表文本摘要和减弱动效。
5. 加载、空数据、无匹配、校验失败、请求失败、重试、重复提交、取消危险操作、选中导出与部分失败；合成 Excel 文件的正常和失败解析。
6. 使用合成数据及模拟端点；不向 httpbin、七牛或其他演示服务发送用户文件。记录浏览器、依赖解析、截图和断言后，才可声明相应 UI/行为通过。

剩余限制：未运行旧版前端、未做截图/像素验证、未验证真实后端或上传、未全面审查第三方资源权利及所有传递依赖。文档已把这些边界显式传递给 Agent，本次没有通过文字补充把它们视为已经实现。
