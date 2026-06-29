# Zhiné

> **Open Source Project / 开源项目**  
> **Personal Intelligence Companion / 个人智慧伙伴**  
> **Beyond understanding. / 不止于懂你。**

Zhiné 是一个建立在开放、可演进认知架构之上的个人智慧伙伴项目。

它的目标不是再做一个聊天机器人、任务执行框架或云端大模型套壳，而是帮助个人拥有一个本地、私有、可迁移、可治理、可持续成长的 **Personal Cognitive Model / 个人认知模型**，并将长期交互中产生的记忆、知识、经验、技能、反馈和评测沉淀为个人智慧资产。

---

## 1. 项目定位

| 层级 | 表达 | 说明 |
|---|---|---|
| 主品牌 | Zhiné | 面向个人智慧伙伴的开源项目 |
| 对外产品类别 | Personal Intelligence Companion / 个人智慧伙伴 | 用户感知到的长期 AI 伙伴 |
| 技术核心 | Personal Cognitive Model / 个人认知模型 | 由记忆、知识、经验、技能、策略、评测和适配层构成的个人模型资产 |
| 架构主张 | Open Cognitive Architecture / 开放认知架构 | 面向开发者和社区的开放模块、协议和治理框架 |
| 核心承诺 | Beyond understanding. / 不止于懂你。 | 理解之后，还要记忆、协作、保护、适应和成长 |

一句话说明：

> Zhiné turns personal AI from a one-time tool into a long-term, portable, governable and evolving personal intelligence companion.

---

## 2. Zhiné 为什么存在

今天，大多数 AI 产品仍然以以下形态存在：

```text
用户请求 → 云端模型回答 → 对话结束
```

这种模式可以解决很多即时任务，但难以解决个人 AI 的长期问题：

- 用户长期交互产生的记忆、经验和方法归谁所有；
- 个人偏好、知识和技能如何沉淀为可迁移资产；
- 本地模型如何成为个人长期智慧连续性的承载体；
- 远端强模型如何增强个人模型，而不是取代个人模型；
- 模型成长如何被记录、验证、审计和回滚；
- 用户如何避免被单一平台、模型、账户或应用锁定。

Zhiné 希望推动的形态是：

```text
用户任务 → 个人模型执行 → 经验沉淀 → 技能更新 → 策略优化 → 模型成长
```

---

## 3. Zhiné 是什么

Zhiné 是一套面向个人智慧伙伴的开放认知基础设施，核心由以下部分构成：

| 组成 | 作用 |
|---|---|
| Zhiné Core | 认知运行时，负责理解、推理、规划、工具调用、评估和反思 |
| Zhiné Memory | 个人记忆系统，管理长期记忆、偏好、目标、复盘和价值约束 |
| Zhiné Knowledge | 个人知识层，管理文档、笔记、项目资料、研究资料和知识结构 |
| Zhiné Reasoning | 推理与反思层，负责任务理解、计划生成、批判、评估和复盘 |
| Zhiné Identity | 身份与治理层，处理用户主权、权限、边界、审计、版本和回滚 |
| Zhiné Access & Sync | 访问与同步层，支持跨设备访问、上下文连续和安全恢复 |
| Zhiné Open Architecture | 开放架构，定义模块边界、开放协议和社区协作方式 |

Zhiné 的核心不是单一模型权重，而是一个围绕个人长期成长形成的认知资产系统。

---

## 4. Zhiné 不是什么

Zhiné 不应被实现或传播为：

| 不是 | 原因 |
|---|---|
| 普通 ChatBot | 只回答问题，不能沉淀长期个人智慧资产 |
| 普通 Agent 框架 | 只强调工具调用和流程编排，不强调个人模型主权与成长 |
| 本地 RAG Demo | 检索只是基础能力，不等同于个人认知模型 |
| 云端大模型套壳 | 个人长期资产必须由用户掌控 |
| 无约束自训练系统 | 自学习必须经过授权、治理、评测和回滚机制 |
| 数字灵魂或人格复制项目 | Zhiné 不宣称复制意识、人格或灵魂 |

---

## 5. 核心原则

Zhiné 的技术与产品实现必须遵循以下原则：

1. **Local First**：个人数据、个人记忆、个人训练候选数据默认本地保存。
2. **Personal Model Ownership**：用户拥有自己的记忆、知识、技能、训练数据、适配层、评测记录和演进日志。
3. **Open Architecture**：不绑定特定模型、数据库、云服务或任务执行框架。
4. **Evolvable by Design**：成长不是附加功能，而是系统核心。
5. **Verifiable Growth**：不能只说“更懂你”，必须通过个人评测集证明。
6. **Controlled Self-Training**：允许自学习，但必须受控、可评测、可回滚。
7. **Human Sovereignty**：模型服务个人，不替代个人，不自动提升权限。
8. **Ubiquitous Access**：支持跨设备、跨系统、跨应用的连续访问能力。
9. **Interoperability**：个人智慧资产必须可导出、可迁移、可恢复。

---

## 6. 第一阶段目标

第一阶段不追求完整自训练，也不追求一次性实现全部架构。

第一阶段只验证最小闭环：

```text
个人记忆
+ 个人知识库
+ 本地模型
+ 远端增强
+ 经验抽取
+ 技能沉淀
+ 下次复用
```

建议优先场景：

```text
Personal Research Intelligence Companion for One User
```

即：先面向单个用户，构建一个可长期使用、可调用个人知识库、能沉淀研究经验和复用分析技能的个人研究智慧伙伴。

---

## 7. 当前文档结构

```text
zhine/
  README.md

  docs/
    architecture.md
    principles.md
    roadmap.md

  specs/
    personal-memory-format.md
    evolution-log-format.md
    personal-benchmark-protocol.md
```

### 7.1 文档说明

| 文件 | 作用 |
|---|---|
| `README.md` | 项目总览、定位、原则和第一阶段目标 |
| `docs/architecture.md` | 总体架构、模块边界、数据流、模型路由和安全控制 |
| `docs/principles.md` | 核心原则、工程约束、产品行为准则和不可违反的红线 |
| `docs/roadmap.md` | 阶段路线、交付物、验收标准和社区推进节奏 |
| `specs/personal-memory-format.md` | 个人记忆格式、字段定义、生命周期和治理规则 |
| `specs/evolution-log-format.md` | 演进日志格式、事件类型、审计、回滚和完整性要求 |
| `specs/personal-benchmark-protocol.md` | 个人评测协议、测试样例、指标体系和发布门禁 |

---

## 8. 建议仓库结构

```text
zhine/
  README.md
  LICENSE
  CONTRIBUTING.md
  SECURITY.md

  docs/
    whitepaper.md
    architecture.md
    principles.md
    roadmap.md
    engineering-plan.md
    mvp-plan.md
    security-model.md
    developer-quickstart.md
    governance.md

  specs/
    personal-memory-format.md
    skill-graph-format.md
    evolution-log-format.md
    personal-benchmark-protocol.md
    model-router-protocol.md
    personal-adapter-format.md
    access-sync-protocol.md

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

## 9. 开源与数据边界

Zhiné 是开源项目，但开源边界必须清晰：

| 可开源 | 不应默认开源 |
|---|---|
| 架构思想 | 个人记忆 |
| 核心框架 | 个人文档 |
| 协议规范 | 个人训练数据 |
| 参考实现 | 个人 LoRA / Adapter |
| 评测模板 | 个人行为日志 |
| 治理机制 | 用户私密上下文 |

建议许可：

| 类型 | 建议 |
|---|---|
| 核心代码 | Apache License 2.0 |
| 文档与规范 | CC BY 4.0 |
| 示例数据 | CC BY 或 CC BY-SA |
| 个人数据 | 默认不公开，除非用户明确授权 |

---

## 10. 项目宣言

```text
Zhiné is a Personal Intelligence Companion built on an open and evolvable cognitive architecture.

We believe every person should own a local, private, portable, governable, and continuously evolving cognitive model.

Zhiné is not just a task-execution framework or chatbot. It is a personal cognitive infrastructure that turns memory, experience, skills, feedback, and learning into long-term personal intelligence assets.

Beyond understanding.
To transcend is to become oneself.
```

中文：

```text
Zhiné 是一个建立在开放、可演进认知架构之上的个人智慧伙伴。

我们认为，每个人都应拥有一个本地、私有、可迁移、可治理、可持续成长的个人认知模型。

Zhiné 不只是一个任务执行框架，而是一个个人认知基础设施，用于把记忆、经验、技能、反馈和学习转化为长期个人智慧资产。

不止于懂你。
超越，才是自己。
```
