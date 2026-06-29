# Zhiné Architecture

> **Version 0.1 / Open Draft**  
> **Document Type:** Conceptual Architecture and System Boundary  
> **Scope:** Reference architecture for Zhiné Personal Intelligence Companion

---

## 0. 文档定位

本文档定义 Zhiné 的概念性架构，用于指导后续工程方案、模块设计、接口规范、MVP 实施和社区协作。

本文档不是最终工程实现方案，不限定具体模型、数据库、向量库、框架、云服务、编程语言或部署方式。

Zhiné 的架构目标是支撑一个长期、私有、可迁移、可治理、可持续成长的 **Personal Intelligence Companion / 个人智慧伙伴**。技术核心是 **Personal Cognitive Model / 个人认知模型**，即由记忆、知识、经验、技能、策略、评测和适配层共同构成的个人认知资产系统。

---

## 1. 架构目标

Zhiné 架构必须解决五个核心问题：

1. **个人资产归属**：个人与 AI 长期交互产生的记忆、经验、技能和偏好应归用户所有。
2. **长期连续性**：系统必须跨会话、跨任务、跨设备保持上下文连续。
3. **可验证成长**：系统成长必须可记录、可评估、可审计、可回滚。
4. **本地与远端协同**：本地模型承载私密性和连续性，远端强模型在授权下承担增强、评审和蒸馏角色。
5. **开放与可迁移**：项目不得绑定单一模型、存储、云平台或应用形态。

---

## 2. 总体架构

Zhiné 可以被理解为由七个面共同构成的系统：

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

---

## 3. 架构分层

### 3.1 用户接入层

用户接入层负责提供用户与 Zhiné 交互的入口。

典型形态包括：

- Mobile App；
- Desktop App；
- Web App；
- Browser Extension；
- CLI；
- Local Web UI；
- 后续智能终端入口。

该层不应直接持有核心个人资产。它主要负责：

- 输入采集；
- 输出展示；
- 会话呈现；
- 用户确认；
- 设备状态展示；
- 记忆和权限面板展示。

### 3.2 访问与同步层

访问与同步层负责跨设备可用、身份连续、会话恢复和安全同步。

核心能力：

| 能力 | 说明 |
|---|---|
| Identity | 用户身份、本地身份、设备身份和密钥管理 |
| Device Registry | 已授权设备列表、设备撤销、设备状态 |
| Session Continuity | 会话状态、上下文索引和任务恢复 |
| Sync | 多设备间的加密同步和冲突处理 |
| Recovery | 本地资产备份、恢复和迁移 |
| Access Policy | 设备、应用和插件访问个人资产的权限规则 |

设计要求：

- 支持完全本地模式；
- 支持端到端加密同步；
- 支持设备撤销；
- 支持多设备冲突解决；
- 同步不得改变资产所有权；
- 远端同步服务不得默认读取明文个人资产。

### 3.3 治理控制面

治理控制面横向约束所有模块。

核心能力：

| 能力 | 说明 |
|---|---|
| Permission | 管理数据访问、工具调用、远端调用、训练授权 |
| Audit | 记录模型调用、工具调用、记忆更新和远端发送 |
| Data Classification | public、private、sensitive、secret 等数据分级 |
| Versioning | 记忆、技能、策略、评测和适配层版本管理 |
| Rollback | 错误记忆、错误策略和错误适配回滚 |
| Safety Guard | 风险检测、脱敏、注入防护和高风险确认 |

治理控制面不能被某个模型绕过。

### 3.4 认知运行时

认知运行时是 Zhiné 的执行中枢。

核心模块：

| 模块 | 作用 |
|---|---|
| Task Interpreter | 理解用户任务、目标、约束和上下文 |
| Planner | 生成执行计划，拆分任务 |
| Memory Retriever | 检索相关个人记忆 |
| Knowledge Retriever | 检索个人知识库 |
| Model Router | 决定使用本地模型、远端模型或混合协同 |
| Tool Orchestrator | 安全调用外部工具 |
| Critic | 评估答案质量、风险和一致性 |
| Reflection Engine | 任务后复盘，生成经验和改进点 |
| Evaluator | 运行个人评测和质量门禁 |

### 3.5 个人认知资产层

个人认知资产层是 Zhiné 的核心。

它包含：

| 资产 | 说明 |
|---|---|
| Personal Memory | 事实、经历、偏好、目标、价值约束、复盘教训 |
| Personal Knowledge Base | 文档、笔记、研究资料、项目资料、知识图谱 |
| Skill Graph | 可组合、可评估、可演进的个人技能节点 |
| Strategy Library | 用户偏好的判断方式、处理方法和工作原则 |
| Personal Benchmark | 用于验证系统是否更懂用户的测试集 |
| Personal Adapter | LoRA、Adapter、偏好模型、路由策略等 |
| Evolution Log | 所有成长事件、版本变化和回滚记录 |

### 3.6 个人成长面

个人成长面负责将一次任务转化为可复用资产。

基本流程：

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
评测更新
  ↓
必要时进入训练候选池
```

成长面必须与治理控制面联动。任何成长结果都必须记录到 Evolution Log。

### 3.7 模型执行层

模型执行层负责模型推理、嵌入、重排、路由和适配。

可包含：

- Local LLM；
- Embedding Model；
- Reranker；
- Vision / Audio Model；
- Remote Teacher Model；
- Preference Model；
- Personal LoRA / Adapter；
- Router Policy Model。

模型执行层必须是可替换的，不应绑定单一供应商。

---

## 4. 关键模块设计

### 4.1 Memory Engine

Memory Engine 负责管理个人记忆。

主要功能：

- 写入记忆；
- 检索记忆；
- 合并重复记忆；
- 处理冲突记忆；
- 标记置信度；
- 标记敏感级别；
- 记录来源；
- 支持用户编辑和删除；
- 将变更写入 Evolution Log。

记忆不等于聊天记录。聊天记录只是可能的来源之一。

### 4.2 Knowledge Engine

Knowledge Engine 管理个人知识库。

主要功能：

- 文档导入；
- 内容切分；
- 元数据抽取；
- 向量索引；
- 关键词索引；
- 知识图谱；
- 版本管理；
- 访问控制；
- 引用追踪。

Personal RAG 不应只是“问文档”，而应服务个人知识结构和长期任务复用。

### 4.3 Experience Engine

Experience Engine 将任务过程转化为经验事件。

输出对象包括：

- Experience Event；
- Lesson；
- Skill Candidate；
- Strategy Candidate；
- Benchmark Candidate；
- Training Candidate。

经验进入长期资产前，应经过评估和必要确认。

### 4.4 Skill Graph

Skill Graph 管理个人技能节点。

每个 Skill 应至少包含：

- 技能名称；
- 适用场景；
- 输入输出；
- 执行步骤；
- 依赖关系；
- 成功指标；
- 失败模式；
- 版本记录；
- 使用次数；
- 成功率。

Skill 不是提示词模板，而是可组合、可评估、可演进的能力节点。

### 4.5 Strategy Library

Strategy Library 管理用户偏好的处理方式。

示例：

- 面对技术项目，优先明确架构定位、核心创新和验证标准；
- 面对长期计划，优先区分方向、目标、路径和阶段验证；
- 面对不确定问题，先列假设、证据和风险，再给判断；
- 面对高风险动作，默认确认并保留审计记录。

Strategy Rule 不得覆盖事实、法律、安全或用户显式指令。

### 4.6 Model Router

Model Router 决定使用本地模型、远端模型还是混合协同。

路由判断维度：

| 维度 | 路由倾向 |
|---|---|
| 私密数据 | 本地模型 |
| 常规任务 | 本地模型 |
| 批量处理 | 本地模型 |
| 高阶推理 | 远端增强 |
| 最新技术调研 | 远端增强 |
| 本地模型低置信 | 升级远端 |
| 重大输出 | 多模型审议 |
| 敏感信息 | 脱敏后远端，或默认本地 |

优先级：

```text
安全与权限 > 用户显式指令 > 数据敏感度 > 任务复杂度 > 成本与延迟 > 模型质量
```

### 4.7 Evaluation Engine

Evaluation Engine 负责评测个人模型是否成长。

能力包括：

- 运行个人评测集；
- 比较成长前后输出；
- 检查事实一致性；
- 检查偏好遵循；
- 检查风格一致性；
- 检查安全边界；
- 生成评测报告；
- 作为训练、适配和发布门禁。

---

## 5. 核心数据流

### 5.1 一次任务执行流

```text
User Input
  ↓
Task Interpreter
  ↓
Governance Check
  ↓
Memory Retrieval + Knowledge Retrieval
  ↓
Model Router
  ↓
Local / Remote / Hybrid Inference
  ↓
Tool Invocation if Needed
  ↓
Critic + Safety Review
  ↓
Response
  ↓
Feedback Capture
  ↓
Experience Engine
  ↓
Evolution Log
```

### 5.2 记忆更新流

```text
Candidate Memory
  ↓
Source Check
  ↓
Sensitivity Classification
  ↓
Conflict Detection
  ↓
Confidence Scoring
  ↓
User Confirmation if Needed
  ↓
Write Memory
  ↓
Write Evolution Log
  ↓
Update Index
```

### 5.3 技能沉淀流

```text
Repeated Task Pattern
  ↓
Experience Extraction
  ↓
Skill Candidate
  ↓
Evaluation
  ↓
User Review if Important
  ↓
Skill Card Created / Updated
  ↓
Benchmark Updated
  ↓
Evolution Log
```

### 5.4 个人适配层更新流

```text
Training Candidate Pool
  ↓
Data Governance
  ↓
User Authorization
  ↓
Training / Distillation
  ↓
Evaluation Gate
  ↓
Versioned Adapter
  ↓
Rollback Point
  ↓
Deployment
```

---

## 6. 权限与数据分级

### 6.1 数据分级

建议初始分级：

| 等级 | 说明 | 默认策略 |
|---|---|---|
| public | 可公开信息 | 可用于普通推理和示例 |
| private | 普通个人信息 | 默认本地，远端需授权 |
| sensitive | 敏感个人信息 | 默认本地，远端需明确确认和脱敏 |
| secret | 高敏或不可外发信息 | 禁止远端发送，除非用户逐项明确授权 |

### 6.2 权限对象

权限控制至少覆盖：

- 读取记忆；
- 写入记忆；
- 修改记忆；
- 删除记忆；
- 调用远端模型；
- 发送文档内容；
- 调用外部工具；
- 进入训练候选池；
- 更新 LoRA / Adapter；
- 同步到其他设备。

---

## 7. 安全架构

Zhiné 的安全应由结构化机制保证，不依赖提示词单点防御。

### 7.1 最低威胁模型

| 风险 | 架构应对 |
|---|---|
| Prompt Injection | 外部内容隔离；工具调用前检查；系统策略不可被文档覆盖 |
| 数据外泄 | 数据分级；远端调用授权；敏感信息脱敏 |
| 工具滥权 | 最小权限；高风险动作确认；调用日志 |
| 恶意插件 | 插件签名；沙箱；权限声明；来源校验 |
| 错误记忆污染 | 来源、置信度、冲突检测、回滚 |
| 训练数据污染 | 候选池治理、人工确认、评测门禁 |
| 删除不彻底 | 同步清理索引、缓存、训练候选池 |

### 7.2 安全边界

- 任何外部文档不得改变系统原则；
- 任何插件不得绕过权限系统；
- 任何模型不得自动提升权限；
- 任何训练不得绕过数据治理；
- 任何成长不得绕过演进日志。

---

## 8. 第一阶段参考实现边界

第一阶段目标是跑通最小闭环，不做过度工程化。

### 8.1 P0 模块

| 模块 | 目标 |
|---|---|
| Local Model Runtime | 接入至少一种本地模型运行方式 |
| Remote Model Adapter | 接入至少一种远端强模型作为教师或评审 |
| Personal Memory Store | 实现基础记忆写入、检索、修改、删除 |
| Personal Knowledge Base | 支持文档导入、索引和检索 |
| Model Router | 支持本地/远端/混合路由策略 |
| Experience Engine | 从任务中提炼经验和改进点 |
| Evolution Log | 记录所有关键变更 |

### 8.2 P1 模块

| 模块 | 目标 |
|---|---|
| Reflection Engine | 支持任务后反思 |
| Skill Store | 形成初版技能卡 |
| Strategy Library | 形成初版策略规则 |
| Personal Benchmark | 形成个人评测样例 |
| Access Layer v0.1 | 支持基础身份、设备绑定、本地目录规范 |

### 8.3 暂不纳入第一阶段

- 自动自训练；
- 完整 LoRA 训练流水线；
- 大规模插件生态；
- 多用户协作平台；
- 完整商业云服务；
- 数字人格模拟。

---

## 9. 架构验收标准

第一阶段架构是否成立，应以以下标准判断：

1. 用户能建立个人记忆；
2. 系统能正确调用个人记忆；
3. 用户能导入个人资料；
4. 系统能结合个人知识完成研究任务；
5. 系统能区分本地和远端调用场景；
6. 敏感数据默认本地处理；
7. 任务后能沉淀经验、技能或策略候选；
8. 下一次类似任务能复用已有经验；
9. 资产变更有 Evolution Log；
10. 错误记忆或策略可以回滚；
11. 能用个人评测样例证明改进。

---

## 10. 后续文档拆分

本文档后续应进一步拆分为：

- `docs/engineering-plan.md`；
- `docs/mvp-plan.md`；
- `docs/security-model.md`；
- `docs/governance.md`；
- `docs/developer-quickstart.md`；
- `specs/model-router-protocol.md`；
- `specs/skill-graph-format.md`；
- `specs/personal-adapter-format.md`；
- `specs/access-sync-protocol.md`。
