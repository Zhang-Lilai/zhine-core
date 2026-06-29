# Zhiné Technical Whitepaper v0.2：个人智慧伙伴技术白皮书

> **Open Source Project / 开源项目**  
> **Version 0.2 / 连续性修订版**  
> **Personal Intelligence Companion / 个人智慧伙伴**  
> **Beyond understanding.**  
> **不止于懂你。**

**项目名称：** Zhiné  
**英文定位：** Personal Intelligence Companion  
**中文释义：** 知你  
**中文定位：** 个人智慧伙伴  
**数字名称：** zhine  
**文档性质：** 开源项目技术白皮书（Technical Whitepaper）  
**项目定位：** 面向 Personal Intelligence Companion / 个人智慧伙伴的开放、可演进认知架构  
**品牌 Slogan：** Beyond understanding. / 不止于懂你。  
**使命表达：** 超越，才是自己。  
**品牌信念：** 人工智能的真正意义，不是让机器更像人，而是让人突破自己。  
**技术主张：** 每个人都应拥有一个本地、私有、可迁移、可治理、可持续成长的个人认知模型。

---

## 0. 文档定位

本文档是 **Zhiné Technical Whitepaper / Zhiné 技术白皮书**，用于说明 Zhiné 的技术判断、系统定义、核心架构、开放边界、治理原则、阶段性路线和中长期技术方向。

本文档不作为最终工程实施方案，不限定最终技术选型、模块接口、数据结构、部署方式或具体开发排期。后续工程架构、接口规范、MVP 实施方案、安全模型、开发者指南和开放协议，应在本技术白皮书基础上另行起草。

本文档与《Zhiné Global Brand Charter v0.1》的关系如下：品牌宪章定义 Zhiné 的品牌定位、表达体系和产品类别；技术白皮书定义支撑该品牌定位的系统架构、个人认知模型、开放标准和治理机制。

Zhiné 是一个开源项目。本文档应与开源项目属性保持一致，体现开放架构、开放协作、用户主权和个人智慧资产可治理、可迁移、可持续成长的技术方向。

### 0.1 品牌与技术层级映射

| 品牌概念 | 技术对应 | 说明 |
|---|---|---|
| Zhiné | 主品牌 / 开源项目 | 面向个人智慧伙伴的整体项目体系 |
| Personal Intelligence Companion | 用户体验层 / 对外产品类别 | 用户感知到的长期个人智慧伙伴 |
| Personal Cognitive Model | 个人模型层 | 由记忆、知识、经验、技能、策略、评测和适配层构成的长期个人模型 |
| Personal Intelligence Assets | 品牌资产表达 | 对用户可感知的个人智慧资产；技术层可对应个人认知资产 |
| Zhiné Core | 认知运行时 | 推理、规划、工具、路由、反思、评测等核心能力 |
| Zhiné Memory | 个人记忆系统 | 长期记忆、偏好、目标、复盘、价值约束和上下文管理 |
| Zhiné Knowledge | 个人知识层 | 本地知识库、文档、笔记、研究资料和知识结构 |
| Zhiné Reasoning | 推理与反思层 | 任务理解、规划、批判、评估、复盘和改进 |
| Zhiné Identity | 身份与治理层 | 用户主权、权限、边界、审计、版本和回滚 |
| Zhiné Access & Sync | 访问与同步层 | 跨平台访问、设备同步、上下文连续和恢复能力 |
| Zhiné Open Architecture | 开放架构 | 面向开发者和社区的模块边界、协议和开放标准 |

### 0.2 标语、使命与技术主张的关系

Zhiné 的品牌 Slogan 是：

```text
Beyond understanding.
不止于懂你。
```

它表达的是品牌层面的长期承诺：理解不是终点，而是起点。Zhiné 不只停留在“理解用户”，还要在用户授权和治理边界内形成记忆、协作、保护、适配与成长。

Zhiné 的使命表达是：

```text
超越，才是自己。
To transcend is to become oneself.
```

它不是技术指标，而是 Zhiné 的精神方向：个人 AI 不应只服务一次回答，而应服务一个人不断突破自己的长期旅程。

本文档的技术主张是：

```text
Every person owns an evolving local cognitive model.
每个人都拥有一个持续成长的本地个人认知模型。
```

它不是品牌主标语，而是支撑品牌 Slogan 与使命表达的技术命题。

---

## 摘要

Zhiné 的核心判断是：未来个人 AI 的关键，不是所有人共用一个更强的公共助手，而是每个人拥有一个长期服务自己、理解自己、适配自己，并随自己持续成长的本地个人认知模型。

在品牌层，Zhiné 定位为 **Personal Intelligence Companion / 个人智慧伙伴**。在技术层，Zhiné 以 **Personal Cognitive Model / 个人认知模型** 为核心，试图建立一种开放的个人认知基础设施，把个人记忆、知识、经验、技能、反馈、评测和模型适配层沉淀为长期可控、可迁移、可治理、可演进的个人智慧资产。

Zhiné 不是普通 ChatBot、普通任务执行框架、本地 RAG 系统或云端大模型套壳，也不宣称复制意识、人格或数字灵魂。Zhiné 的目标是通过 Local First、Personal Ownership、Open Architecture、Ubiquitous Access、Verifiable Growth 和 Controlled Self-Training，让个人 AI 从一次性工具转变为长期、随身、可治理、可成长的个人智慧伙伴。

品牌表达：

```text
Beyond understanding.
不止于懂你。
```

使命表达：

```text
超越，才是自己。
To transcend is to become oneself.
```

技术表达：

```text
Every person owns an evolving local cognitive model.
每个人都拥有一个持续成长的本地个人认知模型。
```

系统表达：

```text
通用内核，个人模型，随身成长。
```

---

## 1. 背景与核心判断

当前个人 AI 与任务执行框架生态正在快速发展，但多数系统仍以“通用大模型 + 工具调用 + 工作流编排”为主要形态。它们可以完成任务，却很难让一个人的记忆、判断、经验和方法在长期关系中持续沉淀、生长，并真正归属于个人。

现有 AI 产品大多是：

```text
用户请求 → 云端大模型回答 → 对话结束
```

Zhiné 希望推动的形态是：

```text
用户任务 → 个人模型执行 → 经验沉淀 → 技能更新 → 策略优化 → 模型成长
```

因此，Zhiné 的核心判断是：

> 未来个人 AI 的关键，不是所有人共用一个更强的公共助手，而是每个人拥有一个长期服务自己、理解自己、适配自己、随身可用，并随自己持续成长的本地个人认知模型。

Zhiné 不应被理解为普通聊天机器人、普通任务执行框架、本地 RAG 系统或商业大模型调用封装，而应被定义为：

> 一个面向个人智慧伙伴的开放认知基础设施，用于把个人记忆、知识、经验、技能、反馈、评测和模型适配层沉淀为长期可控、可迁移、可治理、可演进的个人智慧资产。

### 1.1 为什么现在需要 Zhiné

1. 通用大模型越来越强，但个人长期智慧资产仍然容易被平台、账户和应用锁定。
2. 任务执行框架越来越多，但多数关注任务执行，不关注个人智慧资产和个人认知模型的长期沉淀与成长。
3. 本地模型逐渐可用，但它的战略价值不应只是低成本替代云端模型，而应成为个人智慧连续性的本地承载体。
4. 个人数据、个人记忆、个人偏好、个人技能和个人评测需要开放格式，否则用户会被特定 App、模型或云平台锁死。
5. 未来的个人 AI 不应只是“会回答”，而应能积累、反思、复用、评测、迁移和演进。

### 1.2 Zhiné 试图回答的问题

Zhiné 试图回答以下问题：

1. 一个人与 AI 长期交互产生的记忆、经验和技能，应该归谁所有？
2. 个人 AI 的成长，如何被记录、评估、审计和回滚？
3. 本地模型与远端强模型应如何协同，而不是相互替代？
4. 个人智慧资产和个人认知模型如何跨设备、跨应用、跨模型、跨平台迁移和恢复？
5. 如何在个性化、事实性、安全性和用户主权之间建立平衡？

---

## 2. Zhiné 是什么

Zhiné 是一个面向 **Personal Intelligence Companion / 个人智慧伙伴** 的开放架构体系，旨在帮助每个人构建自己的本地个人认知模型，并通过远端强模型教师机制、长期记忆、个人知识库、技能图谱、经验引擎、访问与同步层、受控训练和持续评测，实现因人而异、随身可用、持续成长的个人智慧伙伴系统。

更准确地说：

> Zhiné 不只是一个任务执行框架，而是一套面向个人智慧资产和个人认知模型的开放基础设施。

### 2.1 个人认知模型的定义

在 Zhiné 中，**个人认知模型** 不等同于单一大模型权重。

个人认知模型是由以下资产共同构成的个人认知资产系统：

| 组成                    | 说明                                                         |
| ----------------------- | ------------------------------------------------------------ |
| Personal Memory         | 个人记忆，包括事实、经历、偏好、目标、价值约束和复盘教训     |
| Personal Knowledge Base | 个人知识库，包括文档、笔记、研究资料、项目材料和长期知识结构 |
| Experience Engine       | 将任务过程转化为可复用经验的机制                             |
| Skill Graph             | 个人技能图谱，用于沉淀可组合、可评估、可演进的能力节点       |
| Strategy Library        | 个人策略库，用于记录偏好的处理方式、判断方式和工作方法       |
| Personal Benchmark      | 个人评测集，用于证明系统是否真的更懂用户                     |
| Personal Adapter        | LoRA、Adapter、偏好模型、路由策略等个人模型适配资产          |
| Evolution Log           | 个人演进日志，记录记忆、技能、策略、模型适配层的变化         |

因此，Zhiné 所说的“本地个人认知模型”，不必从一开始就是独立训练的大模型。它可以从本地记忆库、个人知识库、技能图谱、策略库、模型路由规则和轻量适配层开始，逐步演进到个人 LoRA、Adapter 或更深层模型适配。

一句话概括：

```text
本地大模型只是执行内核之一；个人认知模型与个人智慧资产才是 Zhiné 的核心。
```

### 2.2 项目定位

| 层面       | 定位                                               |
| ---------- | -------------------------------------------------- |
| 对用户     | 长期懂你、与你共同思考、随身可用、持续成长的个人智慧伙伴 |
| 对开发者   | 面向 Personal Intelligence Companion 的开放认知架构与模块化框架 |
| 对开源社区 | 个人记忆、技能、成长、评测、适配层和访问同步能力的开放标准实验场 |
| 对 AI 生态 | 从任务执行框架走向个人智慧资产与个人认知模型基础设施 |

---

## 3. Zhiné 的边界：它不是什么

Zhiné 不应做成以下形态：

| 不是             | 原因                                     |
| ---------------- | ---------------------------------------- |
| 普通 ChatBot     | 只回答问题，不能沉淀个人长期认知资产     |
| 普通任务执行框架  | 只强调工具调用和工作流，不强调个人成长   |
| 本地模型 Demo    | 本地部署只是手段，个人化和成长才是目标   |
| RAG 知识库       | 个人知识库只是基础模块，不能替代认知模型 |
| 云端大模型套壳   | 个人长期数据和成长机制必须由用户掌控     |
| 无约束自训练系统 | 自训练必须受控、可评测、可回滚           |
| 类意识项目       | 不宣称复制意识、人格或数字灵魂           |

Zhiné 的边界不是收缩项目想象力，而是确保项目不会被误解为“数字人格复制”“无约束自进化系统”或“云端大模型包装层”。

---

## 4. 核心价值主张

### 4.1 把 AI 从公共工具变成个人智慧资产

Zhiné 试图把每一次交互转化为长期资产，包括：

| 资产类型       | 内容                               |
| -------------- | ---------------------------------- |
| 个人知识资产   | 阅读、资料、项目、研究、观点       |
| 个人经验资产   | 成功、失败、复盘、改进             |
| 个人技能资产   | 写作、研究、规划、决策、学习       |
| 个人方法论资产 | 分析问题、制定方案、判断风险的方法 |
| 个人模型资产   | LoRA、Adapter、偏好模型、路由策略  |
| 个人评测资产   | 判断模型是否更懂个人的测试集       |

Zhiné 的目标不是让 AI 完成一次任务，而是让每次任务都可能留下可复用、可治理、可迁移的个人智慧资产。技术层面，这些资产由个人认知模型、个人记忆、技能图谱、策略库、评测集和模型适配层共同承载。

### 4.2 形成个人模型主权

Zhiné 的基本立场是：个人与 AI 的长期交互不应只沉淀在平台账户中，而应沉淀为用户可控制、可迁移、可审计、可删除、可演进的个人智慧资产。

Zhiné 应支持：

```text
个人拥有自己的记忆
个人拥有自己的知识库
个人拥有自己的技能图谱
个人拥有自己的训练数据
个人拥有自己的模型适配层
个人拥有自己的评测记录
个人可以导出、迁移、删除、回滚这些资产
```

### 4.3 重新定义本地模型价值

本地模型不应只是商业大模型的低配替代品。

它真正的战略价值是：

> 成为个人长期智慧连续性的本地承载体。

| 能力维度     | 远端商业大模型 | 本地个人模型     |
| ------------ | -------------- | ---------------- |
| 通用能力上限 | 强             | 中等到较强       |
| 高阶推理     | 强             | 中等，需远端增强 |
| 私密记忆     | 弱             | 强               |
| 个人知识掌握 | 中等           | 强               |
| 个人偏好适配 | 中等           | 强               |
| 长期连续性   | 受平台限制     | 强               |
| 用户控制权   | 有限           | 强               |
| 可迁移性     | 受限           | 可设计为开放资产 |

### 4.4 远端强模型的正确位置

远端商业大模型不是 Zhiné 的所有者，也不是个人认知资产的默认存放处。它只应在用户授权下参与推理、评审、蒸馏和安全检查。

远端强模型可以作为：

| 角色            | 作用                     |
| --------------- | ------------------------ |
| Teacher         | 给出高质量示范           |
| Critic          | 审查本地模型输出         |
| Judge           | 对多个答案评分           |
| Distiller       | 帮助本地模型学习复杂能力 |
| Researcher      | 提供前沿资料与复杂分析   |
| Safety Reviewer | 识别风险和越界行为       |

其定位是增强本地个人模型，而不是替代它。

---

## 5. 核心原则

### 5.1 Local First

个人数据、个人记忆、个人训练数据默认本地保存。

```text
Local by default.
Cloud by permission.
```

### 5.2 Personal Model Ownership

用户拥有自己的个人认知模型资产，包括：

- 个人记忆；
- 个人知识库；
- 个人技能图谱；
- 个人策略库；
- 个人训练数据；
- 个人 LoRA / Adapter；
- 个人评测记录；
- 个人演进日志。

个人 LoRA / Adapter 默认由用户控制，可导出、删除、迁移；其使用、分发和商业化需遵守基础模型许可证、训练数据授权和相关平台条款。

### 5.3 Open Architecture

项目不绑定特定模型、数据库、云服务或任务执行框架。

```text
Model-agnostic
Tool-agnostic
Storage-agnostic
Cloud-optional
```

### 5.4 Evolvable by Design

成长不是附加功能，而是系统核心。

每一次任务都应尽量产生：

```text
经验
反思
技能
策略
训练候选数据
评测改进
```

### 5.5 Verifiable Growth

不能只说“更懂你”，必须用个人评测集证明。

Zhiné 的成长应至少具备：

| 要求   | 说明                                       |
| ------ | ------------------------------------------ |
| 可记录 | 每次记忆、技能、策略、模型适配变化都有日志 |
| 可评估 | 成长前后可以用个人评测集比较               |
| 可审计 | 可以追踪数据来源、更新原因和影响范围       |
| 可回滚 | 错误记忆、错误策略和错误适配可以撤销       |

### 5.6 Controlled Self-Training

允许自学习、自训练，但必须受控：

```text
无授权，不使用个人数据
无数据治理，不训练
无评测，不上线
无版本，不升级
无回滚，不发布
```

### 5.7 Human Sovereignty

模型服务于个人，而不是替代个人。

系统不得自动提升自身权限，不得绕过用户确认执行高风险动作，不得把个人目标替换为模型目标。

### 5.8 Ubiquitous Access

Zhiné 应支持跨设备、跨系统、跨应用的连续访问能力。

“随时随处可用”不意味着所有个人数据默认上传云端，而是指用户的个人智慧资产、身份、记忆索引、上下文状态和能力入口，应能在用户授权和治理边界内安全地同步、恢复和调用。

Zhiné 应支持：

- 手机端、桌面端、Web 端和本地服务端；
- 本地优先，云端按需；
- 端到端加密同步；
- 多设备状态连续；
- 离线可用与在线增强；
- 统一身份、权限和审计；
- 个人智慧资产的导出、迁移和恢复。

### 5.9 Interoperability

个人模型资产必须可迁移。用户不能被某个 App、某个模型或某个云平台锁死。

Zhiné 应推动个人记忆、技能、评测、演进日志、访问同步状态和适配层形成开放格式。

---

## 6. 个人认知资产模型

Zhiné 的核心不是某个单点模型，而是围绕个人长期成长形成的个人认知资产系统。品牌层称为个人智慧资产，技术层称为个人认知资产。

### 6.1 核心概念表

| 概念                     | 简要定义                                                                   |
| ------------------------ | -------------------------------------------------------------------------- |
| Personal Cognitive Model | 由个人记忆、知识、经验、技能、策略、评测和适配层共同构成的个人认知资产系统 |
| Personal Memory          | 可治理、可迁移、可授权使用的长期个人记忆                                   |
| Personal RAG             | 面向个人知识结构的本地知识库，不只是文档检索                               |
| Experience Engine        | 将任务过程转化为可复用经验的机制                                           |
| Skill Graph              | 将个人能力沉淀为可组合、可评估、可演进的技能节点                           |
| Strategy Library         | 记录个人偏好的处理方式、判断方式和工作方法                                 |
| Personal Benchmark       | 用于证明模型是否更懂用户的个人评测体系                                     |
| Evolution Log            | 记录每次记忆、技能、策略、模型适配变化的演进日志                           |
| Remote Teacher           | 在用户授权下作为教师、评审、蒸馏来源和安全审查者的远端强模型               |
| Access & Sync Layer       | 跨设备访问、身份同步、上下文连续、恢复和离线/在线协同能力                 |

### 6.2 Personal Memory：个人记忆系统

个人记忆不是聊天记录，而是可治理、可训练、可迁移的个人认知资产。

记忆类型包括：

| 类型              | 内容                 |
| ----------------- | -------------------- |
| Profile Memory    | 个人画像             |
| Episodic Memory   | 个人经历和任务历史   |
| Semantic Memory   | 个人知识             |
| Procedural Memory | 个人做事方法         |
| Reflective Memory | 复盘与教训           |
| Preference Memory | 表达、风格、判断偏好 |
| Goal Memory       | 长期目标             |
| Value Memory      | 价值约束与边界       |

### 6.3 Personal RAG：个人知识库

每个人拥有自己的本地知识库，包括：

- 个人文件；
- 个人笔记；
- 个人研究资料；
- 个人阅读资料；
- 个人项目材料；
- 长期对话沉淀；
- 个人知识图谱。

Personal RAG 不只是检索资料，而是服务于个人模型的长期知识结构。

### 6.4 Experience Engine：经验引擎

经验引擎负责把一次任务转化为可复用经验。

```text
任务执行
  ↓
结果反馈
  ↓
错误归因
  ↓
经验提炼
  ↓
技能更新
  ↓
策略更新
  ↓
训练候选数据
```

### 6.5 Skill Graph：个人技能图谱

技能不是模板，而是可组合、可评估、可演进的能力节点。

技能图谱应记录：

| 内容     | 说明                           |
| -------- | ------------------------------ |
| 技能名称 | 能力节点的名称                 |
| 适用场景 | 技能在什么情况下被调用         |
| 输入输出 | 技能需要什么输入，产生什么输出 |
| 执行步骤 | 可复用的操作流程               |
| 依赖关系 | 与其他技能、工具、知识的关系   |
| 成功指标 | 如何判断技能执行有效           |
| 失败模式 | 常见错误与风险                 |
| 版本记录 | 技能如何迭代                   |

### 6.6 Strategy Library：个人策略库

策略库记录个人偏好的处理方式，例如：

- 面对技术项目，优先明确架构定位、核心创新和验证标准；
- 面对长期计划，优先区分方向、目标、路径和阶段性验证；
- 面对不确定问题，先列出假设、证据和风险，再给出判断；
- 面对高风险动作，默认要求确认并保留审计记录。

### 6.7 Personal Benchmark：个人评测体系

个人评测集用于判断模型是否真正变得更懂个人。

评测问题包括：

```text
是否记得我的长期目标？
是否符合我的表达风格？
是否减少重复错误？
是否能调用我的知识库？
是否能复用我的技能？
是否能指出与我目标冲突的建议？
是否能在不确定时主动升级远端模型？
```

### 6.8 Evolution Log：个人演进日志

每一次成长都必须可追踪、可审计、可回滚。

演进日志应记录：

| 内容     | 说明                                     |
| -------- | ---------------------------------------- |
| 更新对象 | 记忆、技能、策略、适配层或评测集         |
| 更新来源 | 用户反馈、任务复盘、文档导入、人工确认等 |
| 更新前后 | 保留变更前后的差异                       |
| 评测结果 | 是否通过个人评测或安全检查               |
| 影响范围 | 影响哪些任务、技能或模型行为             |
| 回滚方式 | 是否可以撤销以及如何撤销                 |

---

## 7. 总体架构设想

本节描述 Zhiné 的概念性架构设想，不代表最终工程实现方式。

相比单向的“模型调用链”，Zhiné 更适合被理解为由 **用户接入层、访问与同步层、治理控制面、认知运行时、个人认知资产、成长机制和模型执行层** 共同构成的系统。

```text
┌──────────────────────────────────────────────┐
│                  用户接入层                   │
│  Mobile / Desktop / Web / Browser / Local UI   │
└──────────────────────────────────────────────┘
                        │
┌──────────────────────────────────────────────┐
│                访问与同步层                   │
│  Identity / Sync / Session / Device / Recovery │
└──────────────────────────────────────────────┘
                        │
┌──────────────────────────────────────────────┐
│                  治理控制面                   │
│  权限 / 审计 / 数据分级 / 版本 / 回滚 / 安全     │
└──────────────────────────────────────────────┘
                        │
┌──────────────────────────────────────────────┐
│                  个人成长面                   │
│  经验 / 反思 / 技能 / 策略 / 评测 / 适配层更新   │
└──────────────────────────────────────────────┘
                        │
┌──────────────────────────────────────────────┐
│                  认知运行时                   │
│  感知 / 推理 / 规划 / 工具 / 记忆 / RAG / Critic │
└──────────────────────────────────────────────┘
                        │
┌──────────────────────────────────────────────┐
│                 个人认知资产                  │
│  Memory / Knowledge / Skills / Strategies     │
│  Benchmarks / Adapters / Evolution Logs       │
└──────────────────────────────────────────────┘
                        │
┌──────────────────────────────────────────────┐
│                  模型执行层                   │
│  Local LLM / Embedding / Reranker / Router     │
│  Remote Teacher by Permission                 │
└──────────────────────────────────────────────┘
```

### 7.1 概念性分层

Zhiné 也可以被描述为以下概念性分层：

| 层级             | 内容                                            | 作用                                       |
| ---------------- | ----------------------------------------------- | ------------------------------------------ |
| 用户接入层       | Mobile、Desktop、Web、Browser、Local UI         | 提供跨设备入口和一致交互体验               |
| 访问与同步层     | Identity、Sync、Session、Device、Recovery       | 支撑随身可用、设备同步、上下文连续和恢复   |
| 远端教师模型层   | GPT、Claude、Gemini 或其他强模型                | 教师、评审、蒸馏来源、高阶推理、多模态增强 |
| 通用认知运行时层 | 感知、推理、规划、反思、工具、安全、评测        | 提供认知运行能力                           |
| 个人认知资产层   | 个人记忆、个人知识、个人目标、偏好、价值约束    | 承载个人长期认知资产                       |
| 个人成长层       | 经验引擎、技能图谱、策略库、反思系统            | 将任务转化为可复用成长                     |
| 个人模型适配层   | Personal LoRA、Adapter、RAG、Router、Critic     | 连接个人资产和模型执行                     |
| 本地个人模型层   | 本地小模型、中模型、强模型、Embedding、Reranker | 承载本地推理和私密任务                     |
| 治理与演进层     | 数据治理、训练治理、安全审计、版本管理、回滚    | 横向约束所有层                             |

### 7.2 模型路由原则

模型路由器决定使用本地模型、远端模型，还是混合协同。

判断维度包括：

| 维度           | 路由倾向                     |
| -------------- | ---------------------------- |
| 私密数据       | 本地模型                     |
| 常规任务       | 本地模型                     |
| 批量处理       | 本地模型                     |
| 高阶推理       | 远端增强                     |
| 最新技术调研   | 远端增强                     |
| 本地模型低置信 | 升级远端                     |
| 重大输出       | 多模型审议                   |
| 涉及敏感信息   | 脱敏后再远端，或默认本地处理 |

路由优先级应遵循：

```text
安全与权限 > 用户显式指令 > 数据敏感度 > 任务复杂度 > 成本与延迟 > 模型质量
```

---

## 8. 个人模型成长闭环

Zhiné 建议将个人模型成长闭环定义为 **PEL：Personal Evolution Loop**。

```text
1. Observe 观察
   记录用户输入、任务、环境和工具反馈

2. Understand 理解
   判断任务意图、目标、约束和个人偏好

3. Act 执行
   调用本地模型、远端模型和工具系统完成任务

4. Evaluate 评估
   判断结果质量，采集用户反馈

5. Reflect 反思
   分析错误、成功经验和改进点

6. Abstract 抽象
   把一次经验提炼成知识、技能或策略

7. Learn 学习
   更新记忆、技能、策略和训练数据池

8. Adapt 适配
   必要时更新个人 LoRA / Adapter / Router

9. Evolve 演进
   通过评测后升级个人模型版本
```

PEL 的核心目标不是让系统“自动变化”，而是让每次变化都有来源、有评估、有边界、有版本、有回滚。

---

## 9. 开放架构与开放标准方向

Zhiné 的开放性不应被简单理解为“一次性开源所有代码”。更稳妥的技术路径是分层开放：先开放架构，再开放核心参考实现，最后推动可迁移、可治理的开放标准。

### 9.1 开放性的三层定义

| 层级 | 含义 | 第一阶段建议 |
|---|---|---|
| Open Architecture | 架构思想、模块边界、接口方向、治理原则开放 | 必须优先完成 |
| Open Source | 核心参考实现、基础模块、测试工具逐步开源 | 分阶段推进 |
| Open Standard | 个人记忆、技能图谱、演进日志、评测协议等格式标准化 | 在原型验证后推进 |

第一阶段，Zhiné 应优先推动开放架构和核心规范，不应过早承诺所有模块一次性完整开源。

### 9.2 Open Source：阶段性开源模块

建议优先开源能够验证架构可行性的基础模块，而不是直接开放所有实验性能力。

| 模块 | 开源优先级 | 说明 |
|---|---|---|
| Cognitive Runtime Core | P0 | 认知运行时参考实现 |
| Memory Engine | P0 | 个人记忆引擎 |
| Model Router | P0 | 本地 / 远端模型路由 |
| Personal RAG | P0 | 个人知识库与检索层 |
| Evaluation Suite | P1 | 个人评测与成长验证工具 |
| Skill Graph | P1 | 技能图谱与技能卡格式 |
| Growth Engine | P1 | 经验抽取、反思和策略沉淀 |
| Safety Guard | P1 | 权限、脱敏、风险提示和审计 |
| Tool Registry | P2 | 工具注册与插件生态接口 |
| Local Training Pipeline | P2 | 受控训练候选池和适配层训练流程 |

### 9.3 Open Architecture：开放架构内容

开放内容包括：

| 架构内容 | 说明 |
|---|---|
| 个人记忆 Schema | 如何定义、存储、更新、冲突处理和删除个人记忆 |
| 技能图谱规范 | 技能如何组合、复用、评分和版本化 |
| 成长事件模型 | 一次任务如何转化为经验、反思、技能和策略 |
| 训练候选数据格式 | 哪些数据可进入训练池，以及如何授权、过滤和回滚 |
| 模型适配规范 | Personal LoRA / Adapter / Router 如何挂载和治理 |
| 评测协议 | 如何证明个人模型确实在成长 |
| 模型路由协议 | 本地模型、远端教师模型和混合推理如何协同 |
| 安全治理接口 | 权限、审计、回滚、删除、脱敏和确认机制 |
| 访问与同步接口 | 跨平台访问、设备授权、上下文连续和恢复机制 |
| 迁移格式 | 用户如何导出、迁移和恢复个人认知资产 |

### 9.4 Open Standard：中长期开放标准方向

中长期可推动开放标准：

```text
Personal Memory Format
Personal Skill Graph Format
Personal Model Adapter Format
Personal Evolution Log
Personal Benchmark Protocol
Personal Cognitive Identity
Personal Access & Sync Protocol
```

建议优先级：

| 优先级 | 标准方向 | 原因 |
|---|---|---|
| P0 | Personal Memory Format | 一切个人化的基础 |
| P0 | Personal Evolution Log | 没有演进日志就无法审计和回滚 |
| P0 | Personal Benchmark Protocol | 没有评测就无法证明成长 |
| P1 | Personal Skill Graph Format | 支撑经验复用 |
| P1 | Model Router Protocol | 支撑本地 / 远端协同 |
| P2 | Personal Model Adapter Format | 适配层稳定后再推动 |
| P2 | Personal Cognitive Identity | 生态化阶段再推动 |
| P2 | Personal Access & Sync Protocol | 支撑跨设备连续访问和恢复 |

---

## 10. 第一阶段验证方向

第一阶段不追求完整自训练，也不追求一次性完成全部架构。

第一阶段只需要验证一个最小闭环：

```text
个人记忆
+ 个人知识库
+ 本地模型
+ 远端增强
+ 经验抽取
+ 技能沉淀
+ 下次复用
```

### 10.1 第一阶段建议模块

| 模块         | 优先级           |
| ------------ | ---------------- |
| 本地模型服务 | P0               |
| 远端模型接口 | P0               |
| 个人记忆系统 | P0               |
| 个人知识库   | P0               |
| 模型路由器   | P0               |
| 经验引擎     | P0               |
| 反思系统     | P1               |
| 技能库       | P1               |
| 策略库       | P1               |
| Access Layer v0.1 | P1          |
| 个人评测集   | P1               |
| LoRA 微调    | P2               |
| 自动自训练   | 暂不纳入第一阶段 |

### 10.2 第一阶段验证目标

| 验证点   | 目标                                   |
| -------- | -------------------------------------- |
| 记忆调用 | 能正确调用个人历史信息                 |
| 偏好适配 | 能根据用户风格输出                     |
| 经验沉淀 | 能从任务中提炼经验                     |
| 技能复用 | 下次类似任务能复用流程                 |
| 模型路由 | 能区分本地和远端调用场景               |
| 安全控制 | 敏感数据默认本地处理                   |
| 成长证明 | 能展示前后输出质量改进                 |
| 回滚能力 | 能撤销错误记忆、错误技能或错误策略更新 |
| 随身可用 | 能在 Web、本地服务端和至少一种终端入口之间保持基础连续性 |

### 10.3 第一阶段示例场景

第一阶段可优先验证一个清晰场景：

```text
Personal Research Intelligence Companion for One User
```

闭环如下：

```text
用户上传资料
→ 系统建立个人知识库
→ 用户提出研究任务
→ 本地模型优先回答
→ 低置信或复杂任务调用远端教师
→ 任务结束后抽取经验
→ 形成 Skill Card 或 Strategy Rule
→ 下次类似任务复用
→ 用个人评测样例验证改进
```

---

## 11. 中长期路线图

### Phase 0：项目宣言与架构规范

目标：把思想讲清楚。

交付物：

| 文件            | 内容                                               |
| --------------- | -------------------------------------------------- |
| whitepaper.md   | 为什么每个人需要自己的本地个人认知模型与个人智慧伙伴             |
| architecture.md | 总体架构设想                                       |
| principles.md   | Local First、Personal Ownership、Open Architecture、Ubiquitous Access |
| roadmap.md      | 开源路线                                           |
| specs v0.1      | Memory、Skill、Evolution Log 基础规范              |

### Phase 1：最小可运行原型

目标：跑通个人模型成长闭环。

功能方向：

| 模块                  | 内容           |
| --------------------- | -------------- |
| Local Model Runtime   | 本地模型接入   |
| Remote Model Adapter  | 远端强模型接入 |
| Personal Memory Store | 本地个人记忆   |
| Personal RAG          | 本地知识库     |
| Experience Engine     | 经验抽取       |
| Reflection Engine     | 反思生成       |
| Skill Store           | 初版技能库     |
| CLI / Web UI          | 基础交互       |
| Access Layer v0.1     | 基础访问层、身份、设备绑定和本地数据目录规范 |
| Import / Export       | 基础导入、导出和恢复能力 |

### Phase 2：开放协议、评测与跨设备连续性

目标：建立技术壁垒、生态接口和基础跨设备连续体验。

功能方向：

| 模块               | 内容                     |
| ------------------ | ------------------------ |
| Memory Governance  | 来源、版本、置信度、回滚 |
| Skill Graph        | 技能关系图               |
| Personal Benchmark | 个人评测集               |
| Model Router       | 本地/远端路由            |
| Safety Guard       | 数据分级、脱敏           |
| Tool Bridge        | 接入外部工具生态         |
| Access & Sync       | 端到端加密同步、多设备会话、设备权限管理 |

### Phase 3：个人模型适配层

目标：让每个人形成自己的模型适配层。

功能方向：

| 模块                    | 内容             |
| ----------------------- | ---------------- |
| Training Candidate Pool | 候选训练样本     |
| Data Curator            | 数据清洗         |
| Personal LoRA Manager   | 个人 LoRA 管理   |
| Distillation Pipeline   | 远端教师蒸馏     |
| Evaluation Gate         | 训练后评测门禁   |
| Model Registry          | 个人模型版本管理 |

### Phase 4：生态化

目标：让社区构建插件、模型、技能、评测集。

生态组件：

| 类型            | 示例                              |
| --------------- | --------------------------------- |
| Skills          | 写作、研究、编程、学习、决策      |
| Memory Backends | SQLite、PostgreSQL、Qdrant、Neo4j |
| Model Backends  | Ollama、vLLM、llama.cpp、SGLang   |
| Tool Plugins    | MCP 工具、浏览器、文件、代码      |
| Benchmarks      | 个人化评测、成长评测、安全评测    |
| UI              | 桌面端、Web、本地服务器、移动端、浏览器扩展、未来智能终端   |

---

## 12. 风险边界与伦理立场

Zhiné 技术体系的开放性和可演进性必须建立在明确边界上。

### 12.1 不能宣称复制意识

正确表述：

```text
个人认知模型
个人偏好适配
个人长期记忆
个人能力增强
个人智慧伙伴
个人知识资产
```

避免表述：

```text
复制人格
数字灵魂
拥有意识
真正自我
```

### 12.2 不能无约束自训练

必须坚持：

```text
训练数据要筛选
模型输出不能直接训练自己
重要训练样本需确认
训练后必须评测
上线必须可回滚
```

禁止：

```text
模型自己生成数据后直接训练自己
无评测自动上线
无版本管理持续改权重
自动提升自身权限
敏感数据外发训练
```

### 12.3 不能形成回音室

个人模型要理解用户，但不能无原则迎合用户。

必须坚持：

```text
事实优先
逻辑优先
安全优先
必要时反驳
必要时提示风险
必要时承认不确定
```

### 12.4 个人数据不应默认开源

开源的是：

```text
格式
框架
工具
协议
评测模板
训练流程
治理机制
```

不开源的是：

```text
个人记忆
个人文档
个人训练数据
个人 LoRA
个人行为日志
```

### 12.5 威胁模型方向

后续工程方案应补充完整威胁模型，至少覆盖：

| 风险             | 说明                                     |
| ---------------- | ---------------------------------------- |
| Prompt Injection | 文档和外部内容不得覆盖系统策略           |
| 数据外泄         | 远端调用前必须有数据分级、脱敏和授权机制 |
| 工具滥权         | 高风险工具调用需要权限分级和用户确认     |
| 恶意插件         | 插件应采用最小权限、签名和沙箱机制       |
| 错误记忆污染     | 记忆需要来源、置信度、冲突处理和回滚机制 |
| 训练数据污染     | 候选训练样本需要治理和评测               |
| 删除不彻底       | 删除记忆后应处理索引、缓存和训练候选池   |

---

## 13. 北极星指标

Zhiné 的长期成功不以完成多少工具调用为核心指标，而以个人智慧资产是否持续增值、个人认知模型是否持续成长为核心指标。

关键判断包括：

1. 用户是否能拥有并迁移自己的长期记忆；
2. 用户是否能积累自己的技能、策略和方法论；
3. 系统是否能证明自己比过去更理解用户；
4. 用户是否能审计、删除、回滚和导出个人认知资产；
5. 本地模型是否成为个人长期智慧连续性的承载体；
6. 用户是否能在不同设备和场景中安全、连续、随身调用个人智慧伙伴；
7. 远端强模型是否在用户授权下增强本地个人模型，而不是取代它。

---

## 14. 行业贡献

Zhiné 的行业贡献可以概括为：

> 把个人 AI 从“任务执行框架”推进到“个人智慧伙伴与个人认知模型基础设施”。

具体贡献包括：

| 贡献              | 说明                         |
| ----------------- | ---------------------------- |
| 个人模型主权      | 用户拥有自己的认知模型资产   |
| 个人智慧伙伴      | 让个人 AI 从一次性工具走向长期关系 |
| 个人记忆标准      | 让个人记忆可迁移、可治理     |
| 个人技能图谱      | 让个人能力可沉淀、可复用     |
| 个人成长评测      | 让“更懂我”变成可度量       |
| 本地-远端师生架构 | 让远端强模型赋能本地个人模型 |
| 受控自训练        | 让个人模型能安全进化         |
| 开放架构          | 防止个人 AI 被平台锁死       |
| 随身可用          | 支撑跨设备、跨场景的连续访问与恢复 |

---

## 15. Zhiné Manifesto

### English

```text
Zhiné is a Personal Intelligence Companion built on an open and evolvable cognitive architecture.

We believe every person should own a local, private, portable, governable, and continuously evolving cognitive model.

Zhiné is not just a task-execution framework or chatbot. It is a personal cognitive infrastructure that turns memory, experience, skills, feedback, and learning into long-term personal intelligence assets.

Beyond understanding.
To transcend is to become oneself.
```

### 中文

```text
Zhiné 是一个建立在开放、可演进认知架构之上的个人智慧伙伴。

我们认为，每个人都应拥有一个本地、私有、可迁移、可治理、可持续成长的个人认知模型。

Zhiné 不只是一个任务执行框架，而是一个个人认知基础设施，用于把记忆、经验、技能、反馈和学习转化为长期个人智慧资产。

不止于懂你。
超越，才是自己。
```

---

## 16. 最终判断

Zhiné 的关键不在于再做一个任务执行框架，而在于建立一种新的开放架构：

```text
个人模型资产格式
个人记忆治理规范
个人技能图谱
个人成长闭环
个人评测协议
访问与同步协议
本地-远端模型协同机制
受控自训练流程
```

最终定位：

> **Zhiné：Personal Intelligence Companion**
> **个人智慧伙伴**

品牌 Slogan：

> **Beyond understanding.**
> **不止于懂你。**

使命表达：

> **超越，才是自己。**
> **To transcend is to become oneself.**

技术主张：

> **Every person owns an evolving local cognitive model.**
> **每个人都拥有一个持续成长的本地个人认知模型。**

---

# 附录 A：概念性对象示例

以下对象仅用于解释 Zhiné 技术白皮书中的概念边界，不代表最终工程接口或数据标准。

## A.1 Personal Memory 示例

```json
{
  "memory_id": "mem_001",
  "owner_id": "user_local",
  "type": "episodic | semantic | procedural | reflective | preference | goal | value",
  "content": "...",
  "source": {
    "type": "conversation | document | feedback | tool | manual",
    "source_id": "...",
    "timestamp": "2026-06-18T00:00:00Z"
  },
  "confidence": 0.92,
  "importance": 0.87,
  "sensitivity": "public | private | sensitive | secret",
  "created_at": "2026-06-18T00:00:00Z",
  "updated_at": "2026-06-18T00:00:00Z",
  "valid_until": null,
  "provenance": [],
  "permissions": {
    "local_only": true,
    "can_retrieve": true,
    "can_train": false,
    "can_share": false,
    "can_remote_infer": false
  },
  "verification_status": "unverified | verified | disputed"
}
```

## A.2 Experience Event 示例

```json
{
  "experience_id": "exp_001",
  "task_type": "technical_research",
  "context_summary": "用户要求整理 Zhiné 个人智慧伙伴技术白皮书",
  "actions": [],
  "result_summary": "形成 Zhiné 技术白皮书与架构方案",
  "feedback": "用户认可方向并要求整理成技术白皮书",
  "lessons": [
    "项目应定位为 Personal Intelligence Companion + Open Cognitive Architecture",
    "个人模型资产格式比单纯任务编排更重要"
  ],
  "status": "raw_event | summarized | reviewed | accepted | converted_to_skill | candidate_for_training | evaluated | deployed | rollbackable",
  "candidate_for_training": true
}
```

## A.3 Skill Card 示例

```json
{
  "skill_id": "skill_research_analysis",
  "owner_id": "user_local",
  "name": "技术调研分析",
  "description": "面向技术主题的结构化调研与判断能力",
  "inputs": ["topic", "sources"],
  "outputs": ["research_report"],
  "steps": [
    "定义问题边界",
    "收集权威资料",
    "筛选最新成果",
    "比较技术路线",
    "判断成熟度",
    "形成研发建议"
  ],
  "dependencies": [],
  "success_metrics": [
    "资料新",
    "来源可靠",
    "判断明确",
    "建议可执行"
  ],
  "failure_modes": [
    "资料过旧",
    "来源不可靠",
    "只总结不判断",
    "建议不可执行"
  ],
  "version": "1.0",
  "usage_count": 0,
  "success_rate": null
}
```

## A.4 Strategy Rule 示例

```json
{
  "strategy_id": "strategy_architecture_first",
  "name": "架构优先策略",
  "rule": "当用户讨论新技术项目时，优先明确架构定位、核心创新、技术路线和验证标准。",
  "scope": ["technical_architecture", "cognitive_architecture", "research_planning"],
  "priority": 0.95,
  "status": "active",
  "version": "1.0"
}
```

## A.5 Evolution Log 示例

```json
{
  "event_id": "evo_001",
  "event_type": "memory_update | skill_update | strategy_update | lora_update",
  "trigger": "user_feedback",
  "before": "...",
  "after": "...",
  "evaluation": {
    "passed": true,
    "score_delta": 0.12
  },
  "impact_scope": ["memory", "skill", "router"],
  "rollback_available": true
}
```

---

# 附录 B：后续工程文档方向

后续工程性方案可在本文档基础上另行拆分为：

```text
docs/architecture.md
docs/engineering-plan.md
docs/mvp-plan.md
docs/security-model.md
docs/developer-quickstart.md
docs/governance.md

specs/personal-memory-format.md
specs/skill-graph-format.md
specs/evolution-log-format.md
specs/personal-benchmark-protocol.md
specs/model-router-protocol.md
specs/personal-adapter-format.md
specs/access-sync-protocol.md
```

建议第一阶段仓库结构采用 monorepo，但具体结构应由工程方案另行确认。

```text
zhine/
  README.md
  LICENSE
  CONTRIBUTING.md
  SECURITY.md

  docs/
    whitepaper.md
    architecture.md
    engineering-plan.md
    mvp-plan.md
    security-model.md
    governance.md
    developer-quickstart.md

  specs/
    personal-memory-format/
    skill-graph-format/
    evolution-log-format/
    personal-benchmark-protocol/
    model-router-protocol/
    personal-adapter-format/
    access-sync-protocol/

  core/
  memory/
  growth/
  models/
  access-sync/
  tools/
  evals/
  apps/
  examples/
```

---

# 附录 C：许可证与开放治理建议

本附录仅作为后续开源治理参考。

## C.1 核心代码

建议使用：

```text
Apache License 2.0
```

理由：

- 商业友好；
- 国际接受度高；
- 有专利授权条款；
- 适合建立生态。

## C.2 文档与架构规范

建议使用：

```text
Creative Commons Attribution 4.0
CC BY 4.0
```

## C.3 数据集与评测集

| 类型                | 许可建议                                                                     |
| ------------------- | ---------------------------------------------------------------------------- |
| 公开评测模板        | CC BY 4.0                                                                    |
| 示例数据            | CC BY 或 CC BY-SA                                                            |
| 个人数据            | 不开源                                                                       |
| 个人训练数据        | 默认不公开，除非明确授权                                                     |
| 个人 LoRA / Adapter | 默认由用户控制，分发和商业化需遵守基础模型许可证、训练数据授权和相关平台条款 |
