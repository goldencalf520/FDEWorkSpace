# FDE 工作台总体设计

状态：待产品方审批后进入实施规划  
日期：2026-10-28  
面向读者：产品、设计、架构、客户端、后端、AI、测试、安全与交付团队

## 1. 摘要

FDE 工作台是一套面向解决方案提供方 FDE 团队的“证据到交付”操作系统。它以一次企业交付（Delivery Engagement）为中心，把企业访谈、领域知识匹配、业务流程梳理、方案与技术选型、原型确认、多 Agent 开发、证据化测试、评审回退以及经验沉淀连接为同一条可追溯的交付链。

产品不是七个孤立工具的集合，也不是只能从第一步走到最后一步的向导。一次交付可以从企业调研开始，也可以直接导入整理好的需求，或接管已有半成品和代码；任何上游结论变化，都要能指出受影响的流程、原型、代码、测试和评审结论。

Windows 与 macOS 桌面端是 FDE 的完整工作台；浏览器端用于企业参与确认、评审及必要管理；控制平面管理共享交付状态、关系、权限与审计；本地或服务器执行节点承载模型、Agent、浏览器、构建和测试。产品集成飞书、录音文件、模型、Git、代码 Agent、Figma、原型库和第三方 API，但不试图取代这些专业工具。

## 2. 产品意图

### 2.1 要解决的问题

企业软件交付失败通常不是单点工具不足，而是交付意义在工具之间丢失：会议里说出的痛点变成无来源的摘要，行业经验被当成企业事实，流程细节没有进入原型，原型与开发任务脱节，Agent 声称完成却没有可复现证据，最终评分也无法定位应回退到哪里。

FDE 工作台的核心价值是保留这条因果链：

> 企业证据 → 可确认发现 → 当前流程 → 目标流程与差距 → 方案与原型 → 开发基线 → 任务与代码 → 测试证据 → 评审与业务结果 → 可复用经验

### 2.2 成功标准

- FDE 能更快把访谈材料转成可确认、可追溯的业务结论，而不是更快生成一篇会议摘要。
- 企业参与者能在有限范围内确认关键事实、流程、原型和验收结果，而不必学习完整工作台。
- 多 Agent 开发的每项工作都受开发基线、代码边界、预算和验收标准约束。
- 完成声明由实际执行的测试和证据支持，且测试 Agent 不通过修改产品来制造通过结果。
- 评审失败能回到最早责任区域，而不是机械地回到原型阶段。
- 历史经验能够改善未来推荐，同时不泄露企业录音、文档、代码和身份。
- 客户演示在数据、账号、材料、环境、降级路径和彩排证据齐备后才被标记为就绪。

### 2.3 非目标

- 不成为通用项目管理、聊天、网盘或 CRM 产品。
- 不成为基础模型供应商、Git 托管服务、完整 IDE、通用浏览器或完整 Figma 替代品。
- 不承诺任意技术组合、任意 Skill/MCP 或任意第三方平台天然兼容。
- 不把 AI 置信度等同于事实、企业确认或测试通过。
- 不自动用客户原始数据训练跨企业的全局模型。
- 不把可点击原型或视觉相似的生成页面称为生产级软件。

### 2.4 反目标

即使功能齐全，出现以下情况也视为失败：

- AI 生成内容失去原始证据或被静默升级为事实。
- 跨企业泄露录音、文档、源码、截图、提示词或身份。
- 未执行的测试被记录为通过，或测试 Agent 修改产品后自行宣布通过。
- 原型库、Figma 或 Capability 升级静默覆盖已确认交付物。
- Decision API 为节省费用绕过数据位置、授权、区域、健康或验证要求。
- Demo 使用真实服务时误发消息、扣款、签约或污染生产数据。

## 3. 用户与责任

### 3.1 主要用户

- **FDE**：工作台的日常主用户，负责证据整理、判断、方案、确认推进、风险接受和交付结果。
- **交付负责人**：查看跨项目状态、资源、预算、阻塞、风险与质量，审批关键策略。
- **企业参与者**：通过浏览器门户查看有限内容，确认事实、流程、原型或业务验收，不操作完整工作台。
- **组织管理员**：管理成员、能力目录、适配器、策略、更新通道、凭证和审计权限。
- **执行节点与 Agent**：不是人类角色；只能通过任务合同、临时权限和预算运行。

### 3.2 确认层级

所有重要陈述都必须区分：来源证据、AI 推断、FDE 确认、企业确认、具名责任确认和下游验证。系统不以模型置信度代替人的责任，也不因内容写入报告就把它视为事实。

## 4. 产品结构

### 4.1 三种入口

1. **Discovery**：从会议、录音、访谈和企业材料开始。
2. **Requirements**：FDE 已有整理好的需求文档，从结构化导入和差距检查开始，可跳过前面区域。
3. **Takeover**：已有半成品或代码。系统先形成供 FDE 修正的当前产品模型，再与目标需求和原型比较；默认增量接管，重写必须单独论证并批准。

所有导入内容先成为 Supplied Baseline，不会自动获得企业确认或验证状态。

### 4.2 七个交付区域

七个区域共享一个 Engagement Core 和一张追溯关系图，可以跳过、回退和并行工作。

#### A1 企业访谈与诊断

输入包括飞书会议、上传录音、录音笔文件、文档及手工记录。系统保存原始录音、原始转写、说话人状态、授权依据和人工修正；修正以注释存在，不覆盖原文。识别质量分别展示转写、说话人、语义提取和证据支持度，高后果金额、日期、接口、合规、权限及验收条件进入加强校验与 Review Queue。

现有 `tools/enterprise-ai-diagnosis-mac-qwen-lan-archive-20261020-122050` demo 作为交互经验来源：保留逐字段引导、下一必填项、回读确认、完整性导航、全程录音兜底、导出和报告预览；不迁移其 localStorage 主数据、固定六模块、最多三个痛点及无证据报告回填。六组主题成为可配置 Interview Template。

主要产物：Source Evidence、Evidence Segment、Source Transcript、Correction Annotation、Interview Finding、Enterprise Confirmation Pack、Delivery Report Version。

#### A2 领域知识与业务流程

领域库持续接收上传或连接的资料，并经历上传、解析、索引、审核和发布状态。每个片段保留来源、版本、范围、权限和许可；检索权限在模型访问前过滤。行业模式只能作为匹配候选和参考假设，不能覆盖企业证据。

系统分别保存当前流程、目标流程和 Transformation Gap。流程模型覆盖角色、步骤、系统、数据、规则、权限、判断点和异常路径，可渲染泳道、流程图、BPMN 或文本视图。进一步沟通绑定到具体发现或流程元素，而不是散落在通用聊天里。

主要产物：Domain Knowledge Source、Domain Pattern、Match Candidate、Current-State Process、Target-State Process、Transformation Gap、Clarification Question、Attached Discussion。

#### A3 方案与技术选型

系统同时管理 Prototype Pattern、Solution Profile 和 Code Starter，三者不能混为一种模板。中大型项目可推荐 RuoYi-Vue-Pro 完整版，小型项目可推荐其精简版、FastAPI-Vue、Next.js 或其他经验证组合；一个交付可包含采用不同方案的独立可部署子系统。

用户可自定义框架、数据库、中间件、地图、支付、合同、社媒等第三方服务。系统生成 Technology Bill of Materials，并检查版本兼容、部署、许可、费用、安全、升级风险和运维复杂度。自定义组合可以在披露风险后继续，但不能被冒充为已验证方案。Decision API 只在符合数据、授权、区域、预算、健康和验证策略的候选中优化能力、速度与价格。

主要产物：Decision Recommendation、Solution Profile、Custom Solution Configuration、Technology Bill of Materials、Third-Party Service Candidate、Development Baseline 草案。

#### A4 原型与 Mock 数据

原型从业务流程对齐的低保真骨架进入高保真可交互版本。页面、动作、字段、角色、成功与异常状态都连接到流程、数据或验收条件；覆盖分析同时发现缺失需求与无来源设计。

原型模板库作为独立产品存在，工作台通过窄接口进行搜索、候选解析、授权状态查询、导入和结果反馈。候选返回稳定 ID、版本、预览、来源、使用权、适用能力、匹配理由、替代方案和导入方式。搜索上下文仅发送 FDE 选择的行业、流程、角色、终端、设计偏好、截图和技术约束。

设计来源包括内部模板、企业私有模板、Figma、持证 UI8 素材、公开或已授权参考网站/小程序，以及 AI 生成内容。它们进入“Reference Capture → Design Interpretation → Prototype Version”的来源链。提供参考、授权复现和自有产品迁移三种 Design Conversion Mode。字体、图片、图标、视频和品牌元素分别记录权利状态；权利不明时使用占位或合规替代。

Figma 使用官方受限授权及文件能力；修改通过重新导入、差异审查、选择合并和新版本进入工作台，不做首版实时双向同步。UI8 类市场由持证用户主动选择和导入，不做爬库、共享账号或源文件跨组织再分发。导入后形成 engagement-owned branch，上游更新不得覆盖企业已确认版本。

Prototype Version 是正式交付记录，可关联 Figma 文件、内部流程和预览。可编辑原型与 Generated Code Candidate 是两个独立产物；未选择 Solution Profile 时不生成正式框架源码。Mock Dataset 默认使用保持业务关系和异常状态的合成数据。

#### A5 多 Agent 开发与测试

开发必须以 FDE 确认的 Development Baseline 为入口，包含范围、目标流程、验收条件、关键数据、外部接口和明确排除项。系统将工作拆成 Development Task Graph；每个任务拥有输入、输出、代码范围、接口合同、验收条件和禁止变更。

默认 Engineering Workflow Pack 采用版本锁定的 [`mattpocock/skills`](https://github.com/mattpocock/skills)，将确认后的基线整理为 Development Spec，再拆成可追踪、带依赖和验收条件的开发任务，并投影到 GitHub 或 Gitee Issues。它是默认而不是强制：FDE 或组织可以选择自定义 Workflow Pack、声明自己的 Spec/Issue 规则，或在满足同一输入输出与追溯合同的前提下完全替换默认包。包版本随 Development Baseline 和 Agent Run Record 锁定；升级不得静默重写已生成的 Spec、Issue 或验收关系。Issue Tracker Projection 服务于外部协作，工作台仍保存业务含义、完整任务图、权限、预算、证据和最终状态。

任务按责任至少区分 Development、Connection、Environment/Deployment、Verification 和 Integration。Development Agent 主要修改受限代码范围且默认不接触生产凭证；Connection Agent 负责第三方 API、MCP、模型、CI、服务器及其他外部对接，只获得任务必需的适配器范围和 Credential Grant。两类任务可以属于同一 Spec，但默认形成不同任务、不同 Agent Work Contract 和不同权限；Verification Agent 独立验证组合行为，Integration Agent 才能按依赖合并已验证结果。

每个 Workbench Task 使用稳定的工作台 ID，并可关联父 Spec、GitHub/Gitee Issue、代码仓库、分支或 Worktree、Pull/Merge Request、Orca Run/Task/Dispatch 以及测试证据。外部 Issue 和 Orca 状态只更新对应投影，不能覆盖工作台中的业务范围、权限、验收条件和最终结论；外部对象被关闭、删除或失联时，工作台保留映射和异常状态供恢复与审计。

Agent Placement 先检查 Content Location Policy、代码与凭证所在位置、任务所需 Agent/模型/Skill/MCP、节点信任和健康，再比较容量、预计时间与成本。Development、Connection、Environment/Deployment、Verification 和 Integration 可以落在不同的本地或远程节点；Decision API 不能为了低成本把任务路由到不满足数据、代码、凭证或能力边界的节点。

Connection Agent 默认使用 Mock 或 Sandbox。真实支付、合同签署、对外消息、生产数据写入、生产部署、不可逆迁移及其他高后果外部动作必须经过与具体任务和目标绑定的 Decision Gate；Gate 记录可选项、决策人、时间、依据和结果，不能由执行该动作的 Agent 自行批准。被批准的是一次明确作用域的动作，不是对服务或凭证的长期开放授权。

用户设置 Agent 并发上限、运行平台和模型；调度器只运行依赖与代码边界允许的并行任务。实现发生在隔离工作区，由 Integration Agent 按依赖顺序增量合并。每次 Agent Run 保留模型、平台、工具活动、变更、测试、预算、检查点、失败和恢复状态。实现 Agent 不能认证自己的任务，独立 Verification Agent 负责验证。

Orca 不是默认启用的硬依赖，而是 Capability Registry 中可选的 Orchestration Backend。只有 FDE 在组织或 Engagement 允许的范围主动勾选 Orca 时，工作台才进行本机或指定远程 Execution Node 的运行时检测。检测结果明确区分未安装、版本不兼容、未连接、未授权、不健康和可用；未安装时展示官方项目说明及下载地址 `https://onorca.dev/download`，但不得自动下载、安装或切换。安装完成后必须重新检测版本、连接、Agent 能力和权限并通过连接测试，才进入“已选择且可路由”。取消勾选停止新任务路由，但不删除 Orca，也不抹除已有 Agent Run Record。

工作台把符合条件的 Task、依赖、Agent Work Contract 和作用域授权投递到 Orca；Orca Run/Task/Dispatch 标识回写 Agent Run Record。Orca 的 `worker_done` 只构成候选完成声明，不能越过 Verification 和 Acceptance Test Matrix。远程节点失联时进入 Unverifiable Run State，而不是自动失败；在没有来自执行节点的积极退出证据前不得盲目重派、清理或释放。每次 Dispatch 使用租约、检查点和幂等请求标识；确认失败或停止后，替代 Dispatch 显式引用被替代尝试并重新声明放置位置，防止重复修改、外部调用或合并。未选择、未安装或不可用时，FDE 可以继续使用本地 Agent、其他已验证编排后端或受控人工执行，不得静默启用 Orca。

最终 Test Agent 对 Development Baseline 全流程重新执行。UI 路径保存步骤截图或视频，API、迁移及非 UI 路径保存相应日志和断言。测试 Agent 不得修改产品行为；发现缺陷返回任务图。未执行就是未通过，重试与 flaky 结果必须可见。

#### A6 评审团

评审团针对锁定的 Review Snapshot 工作。默认维度覆盖功能完成度、商业价值、产品视觉、技术能力、企业复盘和目标用户易用性，并允许增加维度。每个维度声明量表、证据、权重、最低分和 veto 条件；证据不足显示 Unscored，而不是编造分数。

实现某能力的 Agent 不得评判同一能力。商业价值、企业复盘和目标用户易用性需要具名人的输入。评审者分歧展示证据和假设，不用平均值掩盖。

低于阈值或命中 veto 后，系统生成带证据、负责人、优先级和验收条件的 Improvement Item，并回退到最早责任区域：可能是证据、流程、方案、原型或开发，不固定回到 A4。受影响下游重新进入验证后才能生成新 Review Snapshot。

#### A7 历史沉淀与持续学习

Engagement History 保留证据、确认、流程、方案、原型、实现、测试、评审及关系。当前视图由历史投影生成；更新通过 supersede、affect、withdraw 或 delete 表达，不静默改写过去。

可复用资产的 Experience Weight 来自业务验收、实际使用、业务效果、缺陷、维护成本、工期、预算偏差、评审失败和事故等 Outcome Signal，并按行业、规模、地区、合规、技术、团队能力、复杂度、证据质量和时间衰减。模板被点击或导入只是弱信号，后续确认和业务结果才可提高推荐权重。

初期采用权限过滤检索、结构化指标和可解释权重，不自动训练客户项目的全局模型。

## 5. 横向能力

### 5.1 追溯与影响传播

工作台保存 Evidence/Findings/Pain/Process/Gap/Decision/Prototype/Baseline/Task/Test/Review 之间的多对多关系。所有主要对象都提供 Traceability Inspector，显示来源、状态、版本、确认、依赖和受影响结果。未确认依赖可以由具名 FDE 接受风险后继续，但风险必须跟随下游可见。

### 5.2 Capability Registry

Skill、MCP server、模型、Agent、适配器和工具统一作为 Execution Capability 管理，而不是各区域独立硬编码。每个区域显示：

- 当前可用：通过安装、策略、授权、地区、数据位置、预算、健康和验证检查；
- 本次已选择：FDE 或策略为当前工作选择的能力；
- 实际已执行：真实调用版本、输入输出、运行位置、数据目的地、费用和调用链。

能力选择优先级为组织硬策略、项目数据与预算策略、区域配置、FDE 选择、Decision API 推荐。不可用时不得静默替换，除非事先声明了合规 Capability Fallback Rule。

Capability Registry 必须把“默认推荐”“已安装”“已选择”“健康可用”和“实际执行”作为不同状态。Engineering Workflow Pack 可以有组织默认值且允许项目级自定义；Orchestration Backend 不因安装而自动获得选择权。涉及 Orca 时，选择控件同时承担检测入口：未安装提供官方地址和复检动作，安装但不可用展示具体依赖或连接原因，可用后才允许保存为当前路由选择。

自定义能力分为内置、发布者验证、组织验证和未验证。能力包声明不可变版本、输入输出、权限、数据目的地、适用区域、依赖、健康检查和升级兼容性；不完整时只能作为受限 Experimental Capability。组织验证需要清单审查、依赖检查、隔离试运行和具名批准。验证后可进入组织私有目录，默认不进入跨组织公共市场。

安全问题或权限、外部域名、数据目的地、依赖及效果发生实质变化时，原验证失效，停止新执行并把重要历史产物标记为可能受影响。执行记录展开完整 Capability Invocation Chain。

### 5.3 Demo Readiness

客户演示不是临时待办，而是证据化门禁。Demo Scenario 声明观众、业务故事、路径、环境、集成、主持人与目标；系统根据场景动态生成可版本化 Checklist。默认类别包括：

- 演示故事、脚本、PPT 与角色分工；
- 演示数据、账号、权限和有效期；
- 产品版本、设备、网络、模型额度和第三方服务；
- 隐私、录制授权与观众视图；
- 完整彩排、故障降级、现场联系人、备份与恢复。

每项包含负责人、截止时间、必选性、阻塞级别、状态和完成证据。网络、登录、额度、服务健康和版本等自动检查；内容、讲解和人员类项目由人工确认。易变证据有 Readiness Evidence Window，关键版本、数据、权限、集成或脚本变化使相关证据失效。存在阻塞项时不能标记就绪；非阻塞风险可由具名 FDE 接受。

Demo Mode 从不可变 Demo Snapshot 启动，隔离正式客户数据，支持一键重置、观众视图、离线降级和紧急停止。外部集成声明 Mock、Sandbox 或 Live；Live 高后果写操作必须进入 allowlist 并逐项确认、审计。临时账号、数据和授权设定到期后的停用、重置或删除动作。

每次彩排和客户演示形成独立 Demo Run。彩排问题成为关联产品或 Checklist 的 Remediation Item，复验后才能恢复就绪。客户反馈区分企业原话、FDE 现场记录与 FDE 推断；默认不自动录制现场。Demo Preparation Pack 可导出场景、版本、责任、证据、风险、降级路径和联系人，但不包含密码或密钥。

## 6. 信息架构与关键界面

### 6.1 应用级导航

- 组织与 Engagement 切换；
- Engagement Overview；
- Attention Queue；
- 全局权限过滤搜索；
- 能力目录、执行节点、预算、组织策略和审计；
- Demo Center；
- 企业 Portal 入口与外部访问授权。

### 6.2 Engagement Overview

页面主视觉是非线性交付地图，而不是七个互相隔离的菜单。每个区域展示当前版本、确认度、阻塞、受影响结果和下一动作。顶部明确 Entry Mode 和整体风险；右侧 Attention Queue 聚合需要当前用户处理的确认、冲突、失败、预算、测试缺口和过期证据。

工作台首页和“新建交付”必须把 Takeover 与 Requirements 作为首屏主入口：Takeover 明确接收企业资料、半成品代码和已有原型，Requirements 明确接收业务流程与需求资料。两者以同等高视觉权重直接进入对应导入动作；Discovery 持续可见但使用次级权重，为尚未整理资料的 FDE 提供会议、录音和访谈入口。进行中的项目必须展示其 Entry Mode 与对应下一动作，避免用户先进入七区域地图再判断从何处开始。

选择任意对象时，Traceability Inspector 从右侧展开，显示来源、版本、确认、依赖与下游影响。Guidance Mode 把同一状态呈现为逐步路径；Expert Mode 提高密度，但两者不产生不同数据模型。

### 6.3 区域页面

每个区域沿用统一骨架：当前工作对象、上下文与来源、主编辑/审查面、讨论与决策、覆盖或完整性、Capability 面板、运行记录和确认动作。能力面板显示推荐、已选、依赖状态、预算估计和最近执行；详细调用链进入独立运行记录，避免主界面过载。

## 7. 系统架构

### 7.1 部署形态

- **Workbench Desktop**：Windows/macOS 完整 FDE 客户端，控制本地执行、文件、浏览器和凭证。
- **Enterprise Portal**：企业确认、评论、评审、业务验收和管理的轻量 Web 入口。
- **Control Plane**：共享 Engagement 状态、版本、关系、策略、权限、审计和长任务协调。
- **Execution Node**：在桌面或服务器运行模型、Agent、浏览器、构建和测试，靠近代码与凭证。

Execution Node 可以由工作台原生节点或可选 Orca Remote Server 承载。Orca 节点只是执行位置，不拥有 Development Task Graph；代码、凭证、模型账号和 Agent CLI 仍位于相应执行主机，并受 Content Location Policy、Credential Grant、节点信任和任务类型约束。开发、连接、部署、验证与集成任务可以路由到不同节点，不因处于同一 Engagement 而共享全部数据或凭证。

控制平面不默认托管所有敏感内容。Content Location Policy 决定录音、代码、业务数据、凭证和执行证据是否只能留在本机或企业私有环境；节点只获得认证任务和临时权限，不直接访问控制平面数据库。

初始部署范围采用 connected hybrid：Architecture Spike 与 Internal Alpha 使用可连接的控制平面加本地执行节点；Pilot 验证内容留在桌面或企业私有环境、控制平面只保留允许元数据与引用的形态。完整私有控制平面或隔离网离线部署保留架构路径，但只有真实 Pilot 将其列为硬条件时才升级为 External Beta 门槛。Enterprise Portal 只接收 Content Location Policy 允许发布的确认包或脱敏投影，不反向取得受限原件。

### 7.2 模块边界

首版控制平面采用 Modular Monolith，以深模块维护事务边界，而不是按七个 UI 区域拆微服务：

- **Engagement Core**：交付图、版本、确认、影响传播、历史和对象权限；
- **Evidence & Knowledge**：录音/文档引用、转写分析版本、领域资料、索引范围和检索候选；
- **Process & Design**：流程模型、方案选择、原型版本、原型库合同和设计来源链；
- **Capability & Integration**：能力注册、信任、依赖、适配器、路由资格和凭证授权；
- **Durable Orchestration**：长任务、检查点、预算、暂停、重试、取消和节点路由；
- **Development & Verification**：开发基线、任务图、Agent run、测试矩阵和证据；
- **Review & Learning**：Review Snapshot、评分、改进项、结果信号和经验权重；
- **Demo Readiness**：场景、快照、Checklist、彩排、Live guard 和准备包；
- **Identity & Audit**：组织、外部访问、能力授权和防篡改审计。

模块名与物理拆分是设计默认；实施者可以在不破坏所有权和接口深度的前提下合并内部实现。

### 7.3 数据与持久化

- PostgreSQL：关系、当前投影、关键域事件和权限元数据；
- 对象存储或受控本地存储：录音、文档、截图、视频、导出和大文件；
- 可重建全文/向量索引：领域知识和权限过滤搜索；
- OS/企业 Secret Store：凭证；
- 独立运行日志与证据存储：高容量执行数据；
- Redis 仅用于可丢弃缓存、租约和短期协调，不作为交付事实来源。

Material change 采用选择性域事件保存；模型 token、媒体分片、进度和调试日志不会全部塞入同一事件流。

### 7.4 长任务

上传、转写、索引、Agent、构建和测试都使用 Durable Orchestration 深接口，具备幂等、真实进度、预算、暂停、重试、取消和检查点。建议评估 self-hosted Temporal 适配器与轻量本地适配器，但产品域模块不能依赖具体编排产品。

### 7.5 客户端技术候选

首选候选为 Tauri 2 + React + TypeScript，保留 Electron 回退。接受前必须在 Windows/macOS 验证签名更新、钥匙串、sidecar、可恢复大文件、离线恢复、浏览器证据、百万行仓库和系统 WebView 一致性。控制平面优先 TypeScript/Node；Rust 用于桌面壳和必要的本地高权限/高性能功能；Python 仅作为语音、文档或模型生态确有必要的隔离 worker。

这些仍是架构 Spike 的待验证技术选择，不是已完成选型。

## 8. 集成边界

首发支持声明必须通过测试矩阵：

- 录音上传与飞书会议；
- 本地 Git、GitHub 与 Gitee；
- Playwright 浏览器测试；
- OpenAI-compatible、Anthropic-compatible 与 Ollama/vLLM 本地模型路径；
- Codex 与 Claude Code 两类 Coding Agent；
- 本地 CI 与 GitHub Actions 远程 CI；
- 原型库窄合同与 Figma 官方授权/文件读取路径。

开发流程默认提供版本锁定的 `mattpocock/skills` Engineering Workflow Pack 与 GitHub/Gitee Issue Tracker Projection，并验证组织自定义 Workflow Pack 的替换合同。Orca 作为可选集成进入兼容性矩阵，不属于首发运行的强制前置条件；其适配器至少验证安装探测、官方下载引导、版本兼容、连接测试、远程节点能力、任务/Dispatch 映射、完成回报、失联恢复和取消选择后的行为。首版下载引导使用 Orca 官方地址 `https://onorca.dev/download`，地址应由受签名配置维护以便未来更新。

适配器必须声明能力、权限、数据目的地、兼容版本、失败模式和恢复。安装不等于获得环境或项目的普遍访问权。

原型库合同至少覆盖 Search、Resolve Candidate、Check Rights、Import Package 和 Report Outcome 五类语义。具体协议和传输由实施方案选择；不得共享数据库。接口不兼容时阻止新搜索/导入，但仍可查看已导入分支与缓存预览。

## 9. 安全、权限与审计

- 最小权限边界是 Delivery Engagement；角色只是管理便利，实际授权按 capability + object scope 判定。
- 企业 Portal 使用可撤销、过期、身份验证的 External Access Grant；项目成员身份不自动暴露录音、源码、商业信息和评审内容。
- 凭证只存在 OS 或企业 Secret Store；Agent 获得短期、任务范围授权，秘密不会进入普通提示、日志、截图或报告。
- 开发、连接、部署、验证和集成任务使用相互独立的最小权限；生产外部效果必须绑定已解决的 Decision Gate，凭证可用不代表动作已获批准。
- 查看敏感对象、导出、确认、Agent 执行、凭证使用、风险接受和跨企业复用进入 Tamper-Evident Audit Log。
- 同企业跨项目复用受组织策略控制；跨企业默认只复用匿名抽象、方案模式和聚合结果。原始录音、企业身份、文档、业务数据和源码不得自动跨企业。
- 组织可通过具备数据权利的具名、审计 override 放宽某项跨企业限制。
- 桌面端和执行节点必须签名发布，支持稳定通道、延迟、固定版本和分批升级。
- 遥测由组织控制、可检查，默认不包含录音、提示词、源码、企业身份和业务数据。

首发身份以统一 OIDC 边界实现。FDE 组织用户支持本地账号加 MFA，并验证一个 OIDC/飞书组织身份适配器；企业参与者通过过期邀请链接叠加邮箱验证码或飞书身份验证。SAML、更多企业 IdP 和短信验证作为后续适配器，系统保留受审计的紧急管理员账号。

中国大陆首发采用最小必要、目的明确、分类分级、境内优先和跨境默认关闭的工程基线，并在实际部署前由法律顾问确认《个人信息保护法》《数据安全法》、跨境规定、等级保护及客户行业专项义务。删除源内容时采用物理删除或密钥销毁，同时清除索引、缓存和可恢复副本；不可变历史仅保留不含原文及个人信息的审计墓碑。

Desktop 离线时可以读取和编辑本地授权内容、采集录音、运行本地识别/Agent/构建测试并形成草稿，但不能完成共享协作、企业确认或外部 API 调用。本地变化进入离线事件队列；重连后先重新验证权限，再同步允许内容并显式解决版本冲突。已撤销权限阻止同步，不能因为设备曾经离线而继续扩大访问。

## 10. 质量与验收

### 10.1 访谈识别

初始验收优先高质量会后分析，而不是实时助手。正式支持普通话、常见中文口音及中英混合；额外语言只能按独立测试集结果标示支持等级。评估必须覆盖转写、说话人、关键实体、发现提取和证据定位，而不是只报一个总准确率。

Pilot 暂定验收基线：关键实体和关键发现召回率不低于 95%，关键结论 100% 可定位到证据；60 分钟会议在 15 分钟内形成初稿，FDE 有效复核时间不超过 30 分钟。指标必须以独立、版本化的测试集和人工核验规则计算，并由 Pilot 数据校准。

### 10.2 原型与生成代码

Prototype Acceptance 检查业务覆盖、角色、正常/异常状态、交互、可用性和确认。Design QA 检查设计系统一致性、响应式、可访问性和参考模式合规。Generated Code Candidate 还必须经过构建、行为、响应式、可访问性、安全、依赖许可、代码质量和测试；授权复现模式才以视觉相似度为主要指标。

### 10.3 开发与测试

所有基线验收条件进入 Acceptance Test Matrix。P0/P1 流程必须通过且有可复现证据。Technical Acceptance 与 Business Acceptance 分开；任何跨企业泄露、未披露关键发现遗漏或伪造测试通过均为 Blocking Failure。

容量范围内，普通交互 P95 目标小于 2 秒、权限过滤搜索 P95 小于 3 秒；P0/P1 流程必须 100% 实际执行并通过，伪通过为零，测试 flaky 率低于 2%。控制平面元数据 RPO 不超过 5 分钟、RTO 不超过 4 小时；节点重新可用后，强制中断的长任务应在 5 分钟内恢复执行。跨 Engagement 数据泄漏的容忍度为零。

### 10.4 容量基线

外部首发前验证的暂定每组织容量：50 名 FDE、20 个同时活跃 Engagement、每项目 200 小时录音与 100,000 个可追溯对象、约一百万行代码仓库、20 个并发 Agent。长任务性能与普通交互分别定义目标；Pilot 证据可修订该 envelope。

## 11. 发布路径

1. **Architecture Spike**：验证桌面壳、长任务恢复、存储、执行节点、权限和关键适配器。
2. **Internal Alpha**：三种入口均可运行，七区域形成受约束的端到端闭环。首个纵向样板采用现有企业诊断 demo 所代表的 Discovery 场景：以约 60 分钟企业访谈和背景材料为输入，由 FDE、企业负责人、交付负责人完整跑通证据、发现、一条当前/目标流程、原型、一个薄功能、测试证据、评审和 Demo Snapshot。
3. **三类真实 Pilot**：Discovery、Requirements、Takeover 各至少覆盖一个有差异的真实项目。
4. **External Beta**：三项 Pilot 完成，至少两名责任 FDE 选择继续使用，识别、效率、测试、隔离、安全和恢复指标通过，且无 Blocking Failure。

每个里程碑交付可运行纵切面，而不是先分别做完七套水平模块。

Pilot 还应观察相对于现有方法至少 30% 的 Development Baseline Lead Time 改善；若未达到，不得用主观满意度替代，应定位识别、复核、流程梳理或确认环节的实际瓶颈。

后续实施计划按 10–12 人核心团队估算：产品/设计 2 人、桌面/Web 3 人、控制平面与平台 3 人、AI/数据 2 人、测试/安全/DevOps 2 人；目标约 6 个月完成 Internal Alpha，12–15 个月进入 External Beta。该人员分配允许一人兼任，但总能力与验证职责不能被省略；预算金额在实施规划前另行输入。

## 12. 设计默认与实施者可决定事项

以下没有被产品方指定，属于不改变产品边界的设计默认：

- Engagement Overview 默认以交付地图、Attention Queue 和 Traceability Inspector 组成三栏桌面布局；实施设计可根据宽度调整。
- 控制平面模块名称可调整，但 Engagement Core、Capability governance、Durable Orchestration、Identity/Audit 的所有权边界必须保留。
- 原型库合同的传输协议、分页、缓存格式与 SDK 语言由实施规划决定，只要保持窄合同和版本兼容语义。
- 首版不实现 Figma 实时双向同步，也不建立跨组织公共 Capability 市场。
- Desktop 技术栈、Temporal 和具体存储仍必须通过 Spike，不允许把“首选候选”写成既成事实。
- 首轮平台验证覆盖 Windows 11 x64、macOS 13+ Apple Silicon 与 Intel，以及 Ubuntu 22.04/24.04 x64 Server Execution Node。Windows 10 与 Windows ARM64 只做 Pilot 驱动的兼容验证，不作为首个 External Beta 的硬性承诺。

### 12.1 当前可依赖资产

- 已存在并已检查：`tools/enterprise-ai-diagnosis-mac-qwen-lan-archive-20261020-122050` 企业访谈 demo，可作为交互和业务规则参考，不作为正式架构底座。
- 尚未在本仓库出现：独立 Prototype Library、FDE Workbench 产品代码、Execution Node、统一身份系统、适配器框架和 Pilot 数据包。实施计划必须把它们视为待建设或待提供依赖，并在契约未就绪时使用受控 stub。
- Prototype Library 将在另一个项目完成；其负责人、交付时间与可用测试环境必须在进入相关纵切面前落实，但不改变本设计规定的窄合同边界。

## 13. 实施规划的硬门槛

实施计划必须：

- 从垂直切面而不是七个孤立模块开始；
- 明确哪些 ADR 为 accepted、哪些仍处于 proposed/spike；
- 给出 Engagement Core 的对象关系、版本和影响传播策略；
- 给出源证据、索引、对象存储、执行日志和 Secret Store 的数据位置方案；
- 给出 Capability Registry、任务路由、临时授权和完整调用链的最小闭环；
- 给出三种入口与一次完整回退路径的验收测试；
- 将 Demo Readiness 与至少一个 Pilot 的真实演示纳入纵切面；
- 不在设计文档获批前开始产品代码、脚手架或依赖安装。

## 14. 决策记录与术语

规范术语见仓库根目录 [`GLOSSARY.md`](../../../GLOSSARY.md)。架构和产品边界由 [`docs/adr/`](../../adr/) 中 ADR 0001–0068 记录；后续实施不得以“简化”为由绕过其中关于证据、确认、权限、测试、原型来源、Capability、工程工作流、Agent 编排与 Demo 的边界。

状态约定：ADR 0043–0045 明确为 `proposed`，必须通过 Architecture Spike；ADR 0001–0042 与 0046–0068 均为已确认的 `accepted` 决策，即使旧文件未显式写出 status frontmatter。若未来改变状态，必须用新 ADR 明确 supersede，而不是直接改写历史理由。
