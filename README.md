# Recipkg 标准库

**从开源软件提取可复用的配方，记录行为，也记录尚未验证的部分。**

[Recipkg](https://github.com/recipkg/recipkg) · [配方格式](https://github.com/recipkg/recipkg/blob/main/docs/SPEC.md) · [黑盒验证](https://github.com/recipkg/standard-library-verification)

![从软件与依赖整理配方，再交给 Agent 重建](https://raw.githubusercontent.com/recipkg/recipkg/main/assets/recipkg-cover.png)

本仓库按软件类别整理配方和覆盖状态。每个配方在独立仓库维护，保存软件行为、接口、依赖、验收条件和已知缺口，供 Agent 根据配方重建；本目录不是包注册表，也不是完整配方的替代品。

找到适合的条目后，先读其 `RECIPE.md` 和 `COVERAGE.md`，再按固定提交声明依赖。打包会收集递归材料；软件是否可重建，仍需运行实际验收。

## 已开始

| 分类 | 配方 | 上游观察来源 | 状态 |
| --- | --- | --- | --- |
| 命令行 / 多媒体 | [ffmpeg](https://github.com/recipkg/ffmpeg) | [FFmpeg 9.0.2](https://github.com/FFmpeg/FFmpeg/tree/n9.0.2) | **提取中**：已实测多音轨、映射、音频过滤、部分视频处理及 ffprobe 流选择与 JSON 字段；库、格式、工具等大量行为未完成。 |
| 命令行 / JSON 处理 | [jq](https://github.com/recipkg/jq) | [jq 1.8.2](https://github.com/jqlang/jq/tree/34f7186b86743a083a589741b6cea95293524108) | **提取中**：部分过滤、绑定、函数、归约、JSON 解析和输入输出已对照本机；[独立重建](https://github.com/recipkg/jq-workspace)通过有限的函数、作用域、流式记录和序列恢复样本，高精度数字和 JSON 边界仍有验收失败。 |
| 命令行 / 文本搜索 | [ripgrep](https://github.com/recipkg/ripgrep) | [ripgrep 15.2.0](https://github.com/BurntSushi/ripgrep/tree/e89fff89ac9af12e8d4ce9d5fd07beb408ca730f) | **提取中**：本机对照忽略规则、glob、标准输入及 JSON 字节偏移，接入正则配方；完整行为及重建未验收。 |
| 基础能力 / 正则引擎 | [regex](https://github.com/recipkg/regex) | [rust-lang/regex 1.13.0](https://github.com/rust-lang/regex/tree/926af2e68eca3ce089815790541cf50759ba2c59) | **提取中**：上游库适配器验证少量字符串及字节匹配、Unicode 与错误；完整字节行为、语法和重建未完成。 |
| 通讯与社交 | [zulip](https://github.com/recipkg/zulip) | [Zulip 指定源码提交](https://github.com/zulip/zulip/tree/dd5adc2de6c43bd7bac7d1a0e6dc18c9364268a7) | **提取中**：整理频道、主题、消息及事件队列的部分源码合同；上游服务、权限、同步和实际客户端尚未运行验收。 |
| 内容与知识 | [miniflux](https://github.com/recipkg/miniflux) | [Miniflux 指定源码提交](https://github.com/miniflux/v2/tree/3945f3daa0a90040f761d79a5f62a678fe86ba4e) | **提取中**：列出全部 v1 路由，隔离实测部分权限、文章、RSS、OPML 和浏览器流程；接口合同、Web 与其他功能仍未完整提取或重建。 |
| 协作与办公 | [vikunja](https://github.com/recipkg/vikunja) | [Vikunja 指定源码提交](https://github.com/go-vikunja/vikunja/tree/e37ebc0d10db366ff111bc4bb74a696d7cfc912e) | **提取中**：隔离后端实测账户、任务、用户共享及重启；完整 API、真实 UI 和其他权限仍未完成验证。 |
| 文件与媒体 | [syncthing](https://github.com/recipkg/syncthing) | [Syncthing 指定源码提交](https://github.com/syncthing/syncthing/tree/ed38528d7fba3dd6a42c9c9fc6780af432dc15d2) | **提取中**：已测试隔离同机双进程新增、删除及离线冲突；真实设备、协议、安全与恢复尚未完整验收。 |
| Agent 应用 / 软件开发 | [openhands](https://github.com/recipkg/openhands) | [OpenHands Agent Canvas 指定源码提交](https://github.com/OpenHands/OpenHands/tree/17af119c331a87e881417e4afe95f83dd3c5cb2c) | **提取中**：整理会话和消息；用相近提交的 npm 发布包实测浏览器本地会话与历史恢复，固定提交及重建尚未运行。 |
| Agent 框架 / 执行引擎 | [openhands-agent-sdk](https://github.com/recipkg/openhands-agent-sdk) | [OpenHands Software Agent SDK 指定源码提交](https://github.com/OpenHands/software-agent-sdk/tree/46b1fa5cb91ada17e6ec938c7e8624a4fa19fa98) | **提取中**：实测本机会话、工具、模拟模型调用项目技能、服务端认证与重启及两种 WebSocket；远程协议、其他工具与安全行为尚未完整提取或重建。 |
| 开发者工具 / Git 协作 | [gitea](https://github.com/recipkg/gitea) | [Gitea 指定源码提交](https://github.com/go-gitea/gitea/tree/02c03d69d35963e40f9662d4a793a55d78649444) | **提取中**：议题 API 的创建和并发编辑已有部分源码合同；CSV 模块测试通过，完整服务未验收。 |
| AI 聊天 / Agent 管理 | [librechat](https://github.com/recipkg/librechat) | [LibreChat 指定源码提交](https://github.com/LibreChat-AI/LibreChat/tree/8d3da9bbb220a0a96be9330a2e1cbd385fb786d5) | **提取中**：部分消息 API、Agent 管理认证与权限已对照源码；仅做语法检查，服务和重建未验收。 |
| Agent 应用 / 个人助手 | [openclaw](https://github.com/recipkg/openclaw) | [OpenClaw 指定源码提交](https://github.com/openclaw/openclaw/tree/51420782b3810b4aa1230aa9621aec78f7dbbd3c) | **提取中**：已整理配对、技能与沙箱；不同提交的发布包通过模拟模型和正常重启样例，固定源码与重建未验收。 |
| 设计方法 / 质量合同 | [design-foundations](https://github.com/recipkg/design-foundations) | Apple、Microsoft、Android、IBM、GOV.UK、W3C 官方指南，详见配方来源 | **首版可用**：归档与依赖交付已检查；具体产品须独立验收。 |
| 设计方法 / 视觉方向 | [design-directions](https://github.com/recipkg/design-directions) | 基于产品任务、内容、平台与来源资料整理 | **首版可用**：包含阅读、工作台、服务、沉浸、品牌、原生和数据方向，递归依赖基础合同。 |

配方存在或 `recipkg check` 通过，并不代表配方已完整，也不代表软件已根据配方重建。每个仓库须明确记录源码版本、许可、已观察内容、未知项、可复现验收和重建验证状态。

## 可重复对照测试

[标准库黑盒样本测试](https://github.com/recipkg/standard-library-verification)提供 regex、jq、ripgrep、FFmpeg、Miniflux、Vikunja、Syncthing、OpenHands Agent SDK 和 OpenClaw 的样本与可执行断言，可指定上游或重建程序路径。OpenClaw 样本使用不同于固定源码的发布包。测试仓库不属于配方归档；仅检查已有的少量样本，跳过、通过或归档检查都不代表软件已完整重建。每份配方的 `COVERAGE.md` 是覆盖状态依据。

## 首批分类与候选来源

以下是候选，尚未提炼或验证其完整重建能力；开始前需再次核实项目版本、许可、范围及证据。星数只是发现信号，不代表完整性或质量。

| 分类 | 候选开源项目 |
| --- | --- |
| 通讯与社交 | [Zulip](https://github.com/zulip/zulip) |
| 内容与知识 | [Miniflux](https://github.com/miniflux/v2) |
| 协作与办公 | [Vikunja](https://github.com/go-vikunja/vikunja) |
| 文件与媒体 | [Syncthing](https://github.com/syncthing/syncthing) |
| 开发者工具 | [Gitea](https://github.com/go-gitea/gitea) |
| AI 聊天 | [LibreChat](https://github.com/LibreChat-AI/LibreChat)；开始提取前须核对指定提交及其完整许可。 |
| Agent 应用 / 软件开发 | [OpenHands Agent Canvas](https://github.com/OpenHands/OpenHands) |
| Agent 应用 / 个人助手 | [OpenClaw](https://github.com/openclaw/openclaw) |
| Agent 框架 / 执行引擎 | [OpenHands Software Agent SDK](https://github.com/OpenHands/software-agent-sdk)、[LangGraph](https://github.com/langchain-ai/langgraph) |
| Agent 工作流平台 | [Dify](https://github.com/langgenius/dify)；仓库许可含额外条件，提取前应核实具体版本的完整许可。 |
| 命令行 / 多媒体 | [FFmpeg](https://github.com/FFmpeg/FFmpeg) |
| 命令行 / 数据与搜索 | [jq](https://github.com/jqlang/jq)、[ripgrep](https://github.com/BurntSushi/ripgrep) |

后续可增加网络与基础设施、数据与存储、系统工具、安全与身份、商业与运营、教育与科研、设计与创作、游戏与娱乐等分类。软件可有多个标签；分类不等于依赖关系。

## 编写和验证

1. 固定上游源码提交，记录版本、来源、许可及观察范围，阅读相关源码、文档与测试并实际观察可运行行为。
2. 描述用户行为、接口、数据与错误，明确尚未观察的范围；源码、二进制、脚本及钩子不进入配方归档。
3. 声明实际需要的递归配方依赖，说明每个别名的职责和验收；外部系统和第三方服务单列为运行前提。依赖版本固定，不把普通源码仓库冒充配方。
4. 将可复现验收写进 `ACCEPTANCE.md`；执行配方检查、打包和离线构建提示词检查。它们只验证材料结构和交付。
5. 在独立目录按完整配方重建并运行验收，记录测试通过、失败、未验证及依赖缺口。只有覆盖声明范围并通过相应验收后，才能标为完成。

配方归档和 Agent 技能是不同用途。项目级技能可以作为固定提交的独立 Git 子模块保留脚本等资源；Markdown 配方归档不包含 Git 元数据或实现文件。
