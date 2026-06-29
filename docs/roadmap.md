# Zhiné Roadmap

> **Version 0.1 / Open Draft**  
> **Document Type:** Project Roadmap and Milestone Plan  
> **Scope:** Open-source architecture, reference implementation, specs and community ecosystem

---

## 0. 路线图定位

本文档定义 Zhiné 从项目宣言、架构规范、最小原型到开放生态的阶段性路线。

Zhiné 的长期目标是成为 **Personal Intelligence Companion / 个人智慧伙伴** 的开放基础设施。短期目标不是做“大而全”的 AI 产品，而是先验证个人认知模型的最小成长闭环。

---

## 1. 路线图总览

| 阶段 | 名称 | 核心目标 | 主要交付 |
|---|---|---|---|
| Phase 0 | 项目宣言与架构规范 | 把思想、边界、原则和标准方向讲清楚 | README、Whitepaper、Architecture、Principles、Specs v0.1 |
| Phase 1 | 最小可运行原型 | 跑通单用户个人模型成长闭环 | 本地模型、远端增强、记忆、知识库、经验引擎、演进日志 |
| Phase 2 | 开放协议、评测与跨设备连续性 | 建立技术壁垒、评测体系和基础同步能力 | Memory Governance、Benchmark、Model Router、Access & Sync |
| Phase 3 | 个人模型适配层 | 形成用户可控的个人适配资产 | Training Candidate Pool、LoRA Manager、Evaluation Gate |
| Phase 4 | 生态化 | 让社区构建插件、模型、技能、评测集和终端入口 | 插件生态、模型后端、技能市场、评测生态 |

---

## 2. Phase 0：项目宣言与架构规范

### 2.1 目标

把 Zhiné 的品牌定位、技术判断、架构边界、开放原则和第一批规范定义清楚。

本阶段的重点不是写代码，而是避免项目在早期被误解为普通 ChatBot、Agent 框架、本地 RAG 或云端大模型套壳。

### 2.2 交付物

| 交付物 | 说明 | 状态建议 |
|---|---|---|
| `README.md` | 项目总览、定位、核心原则和第一阶段目标 | P0 |
| `docs/whitepaper.md` | 技术白皮书 | P0 |
| `docs/architecture.md` | 总体架构和模块边界 | P0 |
| `docs/principles.md` | 核心原则与不可违反的红线 | P0 |
| `docs/roadmap.md` | 阶段路线与里程碑 | P0 |
| `specs/personal-memory-format.md` | 个人记忆格式草案 | P0 |
| `specs/evolution-log-format.md` | 演进日志格式草案 | P0 |
| `specs/personal-benchmark-protocol.md` | 个人评测协议草案 | P0 |
| `LICENSE` | 建议 Apache License 2.0 | P0 |
| `CONTRIBUTING.md` | 社区贡献规则 | P1 |
| `SECURITY.md` | 安全披露规则 | P1 |

### 2.3 验收标准

Phase 0 完成时，应满足：

1. 对外定位统一为 Personal Intelligence Companion / 个人智慧伙伴；
2. 技术核心统一为 Personal Cognitive Model / 个人认知模型；
3. 明确 Zhiné 是开源项目，不使用机密草案口径；
4. 明确 Local First、Personal Ownership、Open Architecture、Verifiable Growth 等原则；
5. 明确个人数据不默认开源；
6. 明确第一阶段不做完整自动自训练；
7. 核心文档能支撑开发者理解项目边界。

---

## 3. Phase 1：最小可运行原型

### 3.1 目标

跑通单用户个人模型成长闭环。

最小闭环：

```text
个人记忆
+ 个人知识库
+ 本地模型
+ 远端增强
+ 经验抽取
+ 技能沉淀
+ 下次复用
```

建议第一场景：

```text
Personal Research Intelligence Companion for One User
```

### 3.2 P0 功能

| 模块 | 功能边界 | 验收标准 |
|---|---|---|
| Local Model Runtime | 接入至少一种本地模型运行环境 | 能完成基础问答和本地推理 |
| Remote Model Adapter | 接入至少一种远端强模型 | 支持授权调用、结果评审和增强 |
| Personal Memory Store | 记忆写入、检索、编辑、删除 | 能调用历史偏好和事实 |
| Personal Knowledge Base | 文档导入、索引、检索 | 能基于个人资料完成研究任务 |
| Model Router | 本地/远端/混合路由 | 能根据敏感度和复杂度路由 |
| Experience Engine | 任务后经验抽取 | 能生成经验事件和候选技能 |
| Evolution Log | 记录关键资产变化 | 每次记忆、技能、策略更新有日志 |
| Basic UI / CLI | 基础交互入口 | 用户能完成导入、提问、确认、查看记录 |

### 3.3 P1 功能

| 模块 | 功能边界 | 验收标准 |
|---|---|---|
| Reflection Engine | 任务后复盘 | 能指出成功经验、失败原因和改进点 |
| Skill Store | 初版技能卡 | 能保存并复用至少一种任务技能 |
| Strategy Library | 初版策略规则 | 能保存用户偏好的处理方式 |
| Personal Benchmark | 初版评测样例 | 能比较成长前后的表现 |
| Access Layer v0.1 | 身份、设备、本地目录规范 | 能支持基础本地资产管理 |

### 3.4 暂不纳入

Phase 1 不纳入：

- 自动自训练；
- 完整 LoRA 微调平台；
- 大规模插件市场；
- 多用户协作；
- 商业化云同步；
- 拟人化人格复制。

### 3.5 验收标准

Phase 1 完成时，应可演示：

1. 用户上传个人研究资料；
2. 系统建立本地知识库；
3. 用户提出研究问题；
4. 本地模型优先回答；
5. 复杂任务在授权下调用远端教师模型；
6. 系统生成任务结果；
7. 用户反馈后系统提炼经验；
8. 系统形成 Skill Card 或 Strategy Rule；
9. 下一次类似任务能复用已有经验；
10. 评测样例显示输出质量有改进；
11. 错误记忆或策略可以回滚。

---

## 4. Phase 2：开放协议、评测与跨设备连续性

### 4.1 目标

建立 Zhiné 的技术壁垒和生态接口。

Phase 2 的重点不只是功能增加，而是让 Zhiné 的个人智慧资产具备可治理、可迁移、可评测、可同步的基础能力。

### 4.2 交付模块

| 模块 | 说明 |
|---|---|
| Memory Governance | 记忆来源、版本、置信度、冲突处理、回滚 |
| Skill Graph | 技能关系、依赖、复用、评分和版本化 |
| Personal Benchmark | 个人评测集、评测指标、发布门禁 |
| Model Router Protocol | 本地/远端/混合模型协同协议 |
| Safety Guard | 数据分级、脱敏、工具权限和安全审计 |
| Tool Bridge | 外部工具生态接入接口 |
| Access & Sync | 端到端加密同步、多设备会话、设备权限管理 |

### 4.3 开放标准推进

Phase 2 应形成以下规范的 v0.2 或 v0.3：

- Personal Memory Format；
- Personal Evolution Log；
- Personal Benchmark Protocol；
- Personal Skill Graph Format；
- Model Router Protocol；
- Personal Access & Sync Protocol。

### 4.4 验收标准

1. 个人记忆可导出、导入、迁移；
2. 技能卡可复用、评估、版本化；
3. 评测协议能阻止低质量更新上线；
4. 路由协议能清晰表达本地与远端协同逻辑；
5. 多设备访问不破坏 Local First 和用户主权；
6. 工具调用和远端调用有完整审计。

---

## 5. Phase 3：个人模型适配层

### 5.1 目标

让每个用户可以在授权和治理边界内形成自己的模型适配资产。

适配层不必从一开始就是完整模型权重，可以从偏好模型、路由策略、LoRA、Adapter 或任务专用小模型开始。

### 5.2 交付模块

| 模块 | 说明 |
|---|---|
| Training Candidate Pool | 管理可进入训练的候选样本 |
| Data Curator | 数据清洗、去重、脱敏、质量评分 |
| Personal LoRA Manager | 个人 LoRA 创建、版本、评测和回滚 |
| Distillation Pipeline | 远端教师模型蒸馏本地能力 |
| Evaluation Gate | 训练后评测门禁 |
| Model Registry | 个人模型版本管理 |

### 5.3 关键约束

- 无授权，不进入训练；
- 无治理，不启动训练；
- 无评测，不上线；
- 无版本，不发布；
- 无回滚，不启用；
- 敏感数据不默认参与训练。

### 5.4 验收标准

1. 用户可查看训练候选数据；
2. 用户可批准或拒绝数据进入训练；
3. 系统能生成个人适配层；
4. 适配前后有评测对比；
5. 适配层可禁用和回滚；
6. 适配层元数据可导出。

---

## 6. Phase 4：生态化

### 6.1 目标

形成围绕 Zhiné 开放架构的社区生态。

生态不应围绕单一 App，而应围绕个人智慧资产、开放格式、运行时接口和可迁移能力展开。

### 6.2 生态组件

| 类型 | 示例 |
|---|---|
| Skills | 写作、研究、编程、学习、决策、健康管理、项目管理 |
| Memory Backends | SQLite、PostgreSQL、Qdrant、Neo4j、LanceDB |
| Model Backends | Ollama、vLLM、llama.cpp、SGLang、MLX |
| Tool Plugins | MCP 工具、浏览器、文件系统、代码执行、日历、邮件 |
| Benchmarks | 个人化评测、成长评测、安全评测、领域评测 |
| UI | 桌面端、Web、本地服务器、移动端、浏览器扩展、未来智能终端 |
| Governance Tools | 审计、权限、数据分级、插件签名、同步加密 |

### 6.3 社区治理重点

- 开放协议优先；
- 参考实现次之；
- 应用形态多样化；
- 插件最小权限；
- 个人数据不进入公共仓库；
- 社区评测集不包含真实个人隐私；
- 贡献者必须遵守安全和数据边界。

---

## 7. 版本节奏建议

| 版本 | 重点 | 输出 |
|---|---|---|
| v0.1 | 文档与架构草案 | README、Architecture、Principles、Core Specs |
| v0.2 | 最小原型 | 本地模型、记忆、知识库、路由、演进日志 |
| v0.3 | 成长闭环 | 经验引擎、技能卡、策略库、个人评测 |
| v0.4 | 治理与安全 | 权限、审计、数据分级、回滚、安全模型 |
| v0.5 | 访问与同步 | Access Layer、本地备份、基础同步、恢复 |
| v0.6 | 开放协议增强 | Router、Skill Graph、Benchmark、Sync Protocol |
| v0.7 | 适配层实验 | 候选训练池、LoRA/Adapter、评测门禁 |
| v1.0 | 稳定参考实现 | 稳定 API、文档、示例、社区治理机制 |

---

## 8. 优先级判断

### 8.1 最高优先级

- 项目定位统一；
- 个人记忆格式；
- 演进日志；
- 个人评测协议；
- 本地/远端路由；
- 安全治理；
- 最小可运行闭环。

### 8.2 暂缓优先级

- 多用户 SaaS；
- 市场化插件商店；
- 自动自训练；
- 完整移动端产品；
- 大规模云同步；
- 拟人化角色系统。

### 8.3 不应推进的方向

- 复制人格或数字灵魂叙事；
- 默认云端化；
- 以平台账户锁定个人资产；
- 未经授权的数据训练；
- 无评测的自动成长；
- 过早商业化导致架构封闭。

---

## 9. 北极星指标

Zhiné 的长期成功不以工具调用次数或聊天轮数衡量，而应以个人智慧资产是否持续增值衡量。

关键指标包括：

1. 用户是否拥有并能迁移自己的长期记忆；
2. 用户是否能积累技能、策略和方法论；
3. 系统是否能证明自己比过去更理解用户；
4. 用户是否能审计、删除、回滚和导出个人资产；
5. 本地模型是否成为个人长期智慧连续性的承载体；
6. 用户是否能跨设备安全、连续、随身调用个人智慧伙伴；
7. 远端强模型是否增强本地个人模型，而不是取代它。

---

## 10. 下一批建议文件

在当前 7 个文件之后，建议继续生成：

1. `docs/security-model.md`；
2. `docs/governance.md`；
3. `docs/mvp-plan.md`；
4. `docs/developer-quickstart.md`；
5. `specs/skill-graph-format.md`；
6. `specs/model-router-protocol.md`；
7. `specs/personal-adapter-format.md`；
8. `specs/access-sync-protocol.md`；
9. `CONTRIBUTING.md`；
10. `SECURITY.md`。
