# Personal Memory Format

> **Version 0.1 / Open Draft**  
> **Specification Name:** Personal Memory Format  
> **Scope:** Zhiné Memory, Personal Cognitive Model, import/export, governance and evaluation

---

## 0. 规范定位

Personal Memory Format 定义 Zhiné 中个人记忆的基础数据结构、字段语义、生命周期、权限规则、冲突处理和导入导出要求。

个人记忆不是聊天记录。聊天记录只是记忆候选来源之一。

在 Zhiné 中，个人记忆是个人认知模型的重要组成部分，属于用户的个人智慧资产。它必须可治理、可迁移、可审计、可删除、可回滚。

---

## 1. 设计目标

Personal Memory Format 的目标：

1. 让个人记忆脱离单一 App、平台或模型；
2. 支持跨设备、跨模型、跨应用迁移；
3. 支持来源追踪、置信度、敏感级别和权限控制；
4. 支持记忆更新、合并、冲突处理和回滚；
5. 支持后续进入评测、技能沉淀和训练候选池；
6. 支持本地优先和远端授权协同。

---

## 2. 非目标

本规范不解决：

- 具体数据库选型；
- 向量索引实现；
- 加密算法细节；
- 完整同步协议；
- 模型训练细节；
- UI 展示方式；
- 多用户组织权限。

这些内容应由后续工程文档或其他协议定义。

---

## 3. 核心概念

| 概念 | 定义 |
|---|---|
| Memory Record | 单条个人记忆记录 |
| Memory Candidate | 尚未正式写入长期记忆的候选记忆 |
| Memory Source | 记忆来源，如对话、文档、反馈、工具、人工输入 |
| Memory Type | 记忆类型，如事实、经历、偏好、目标、价值约束 |
| Confidence | 记忆可信度 |
| Importance | 记忆重要性 |
| Sensitivity | 记忆敏感级别 |
| Permission | 记忆使用权限 |
| Provenance | 记忆来源链和演进路径 |
| Verification Status | 记忆验证状态 |
| Evolution Event | 记忆变化对应的演进日志事件 |

---

## 4. 记忆类型

### 4.1 类型枚举

| 类型 | 英文值 | 说明 | 示例 |
|---|---|---|---|
| 个人画像 | `profile` | 长期稳定的个人基本信息和背景 | 用户长期从事 OSS 产品研发 |
| 经历记忆 | `episodic` | 特定时间、任务、事件或交互经历 | 用户在某次会议中确认产品定位 |
| 语义记忆 | `semantic` | 长期知识、概念、判断和事实 | Zhiné 定位为个人智慧伙伴 |
| 程序记忆 | `procedural` | 用户偏好的做事方法和流程 | 文件修订应先删重复，再重构逻辑 |
| 反思记忆 | `reflective` | 复盘、教训和改进原则 | 不应过度解释哲学表达 |
| 偏好记忆 | `preference` | 表达、风格、判断或交互偏好 | 输出应简洁、重点突出 |
| 目标记忆 | `goal` | 长期目标、阶段目标和项目方向 | 建立开源个人智慧伙伴项目 |
| 价值记忆 | `value` | 价值边界、原则和不可违反事项 | 用户主权优先，不做封闭平台 |

### 4.2 类型选择规则

同一内容可能有多个维度。写入时应选择主类型，并在 `tags` 中补充辅助分类。

示例：

```json
{
  "type": "preference",
  "tags": ["writing", "document", "style"]
}
```

---

## 5. 基础对象结构

### 5.1 Memory Record

```json
{
  "schema_version": "0.1",
  "memory_id": "mem_01JZ0000000000000000000000",
  "owner_id": "user_local",
  "type": "preference",
  "status": "active",
  "content": "用户偏好文档输出简洁、直接、重点突出，避免重复和啰嗦。",
  "summary": "偏好简洁、直接、重点突出的文档风格。",
  "language": "zh-CN",
  "tags": ["writing", "document", "style"],
  "source": {
    "source_type": "conversation",
    "source_id": "conv_20260625_001",
    "source_uri": null,
    "timestamp": "2026-06-25T00:00:00+08:00",
    "actor": "user"
  },
  "confidence": 0.95,
  "importance": 0.86,
  "sensitivity": "private",
  "permissions": {
    "can_retrieve": true,
    "can_use_for_reasoning": true,
    "can_use_for_personalization": true,
    "can_use_for_training": false,
    "can_share": false,
    "can_remote_infer": false,
    "local_only": true
  },
  "validity": {
    "valid_from": "2026-06-25T00:00:00+08:00",
    "valid_until": null,
    "decay_policy": "stable"
  },
  "verification": {
    "status": "verified",
    "verified_by": "user",
    "verified_at": "2026-06-25T00:00:00+08:00"
  },
  "provenance": [],
  "relations": [],
  "created_at": "2026-06-25T00:00:00+08:00",
  "updated_at": "2026-06-25T00:00:00+08:00"
}
```

---

## 6. 字段定义

### 6.1 顶层字段

| 字段 | 类型 | 必填 | 说明 |
|---|---:|---:|---|
| `schema_version` | string | 是 | 规范版本，当前为 `0.1` |
| `memory_id` | string | 是 | 全局唯一记忆 ID |
| `owner_id` | string | 是 | 资产所有者 ID，默认可为本地用户标识 |
| `type` | enum | 是 | 记忆类型 |
| `status` | enum | 是 | 记忆状态 |
| `content` | string | 是 | 记忆正文 |
| `summary` | string | 否 | 记忆摘要，用于展示和快速检索 |
| `language` | string | 否 | BCP 47 语言标签，如 `zh-CN`、`en` |
| `tags` | array | 否 | 标签 |
| `source` | object | 是 | 记忆来源 |
| `confidence` | number | 是 | 可信度，0 到 1 |
| `importance` | number | 是 | 重要性，0 到 1 |
| `sensitivity` | enum | 是 | 敏感级别 |
| `permissions` | object | 是 | 权限设置 |
| `validity` | object | 否 | 有效期和衰减策略 |
| `verification` | object | 是 | 验证状态 |
| `provenance` | array | 否 | 来源和演进链 |
| `relations` | array | 否 | 与其他记忆、技能、文档的关系 |
| `created_at` | datetime | 是 | 创建时间 |
| `updated_at` | datetime | 是 | 更新时间 |

### 6.2 状态字段

`status` 可取值：

| 值 | 说明 |
|---|---|
| `candidate` | 候选记忆，尚未写入长期记忆 |
| `active` | 当前有效记忆 |
| `superseded` | 已被新记忆替代 |
| `archived` | 已归档，不主动检索 |
| `deleted` | 已删除，保留墓碑记录用于同步和审计 |
| `disputed` | 存在冲突或待确认 |

### 6.3 敏感级别

`sensitivity` 可取值：

| 值 | 说明 | 默认策略 |
|---|---|---|
| `public` | 可公开信息 | 可参与普通推理和示例 |
| `private` | 普通个人信息 | 默认本地；远端需授权 |
| `sensitive` | 敏感个人信息 | 默认本地；远端需明确确认和脱敏 |
| `secret` | 高敏信息 | 默认禁止远端发送和训练 |

### 6.4 权限字段

| 字段 | 类型 | 说明 |
|---|---:|---|
| `can_retrieve` | boolean | 是否可被检索 |
| `can_use_for_reasoning` | boolean | 是否可用于推理上下文 |
| `can_use_for_personalization` | boolean | 是否可用于个性化响应 |
| `can_use_for_training` | boolean | 是否可进入训练候选或训练过程 |
| `can_share` | boolean | 是否可分享给外部系统或用户 |
| `can_remote_infer` | boolean | 是否可发送给远端模型推理 |
| `local_only` | boolean | 是否仅限本地使用 |

权限必须遵守以下约束：

```text
如果 local_only = true，则 can_remote_infer 必须为 false。
如果 sensitivity = secret，则默认 can_share=false、can_remote_infer=false、can_use_for_training=false。
如果 can_use_for_training=true，必须存在明确授权记录。
```

---

## 7. 来源对象

### 7.1 Source Object

```json
{
  "source_type": "conversation",
  "source_id": "conv_20260625_001",
  "source_uri": null,
  "timestamp": "2026-06-25T00:00:00+08:00",
  "actor": "user"
}
```

### 7.2 来源类型

| 值 | 说明 |
|---|---|
| `conversation` | 对话 |
| `document` | 文档 |
| `feedback` | 用户反馈 |
| `tool` | 工具返回结果 |
| `manual` | 用户手动输入 |
| `system` | 系统生成，但必须标记为未验证 |
| `import` | 外部导入 |
| `evaluation` | 评测结果产生 |

### 7.3 来源规则

- 用户明确提供的信息可信度可较高；
- 模型推断的信息必须低置信，并标记为 `unverified`；
- 外部文档产生的记忆必须保留文档 ID 或引用位置；
- 工具结果产生的记忆必须保留工具名称、调用 ID 和时间；
- 来源不明的记忆不得进入训练候选池。

---

## 8. 验证状态

### 8.1 Verification Object

```json
{
  "status": "verified",
  "verified_by": "user",
  "verified_at": "2026-06-25T00:00:00+08:00"
}
```

### 8.2 状态枚举

| 值 | 说明 |
|---|---|
| `unverified` | 未验证 |
| `verified` | 已验证 |
| `disputed` | 有争议 |
| `inferred` | 系统推断，未被用户确认 |
| `obsolete` | 已过时 |

### 8.3 验证规则

- `inferred` 不得被展示为确定事实；
- `disputed` 不应作为强上下文使用；
- `obsolete` 默认不主动检索；
- 高重要度的 `profile`、`goal`、`value` 记忆应尽量由用户确认；
- 写入训练候选池前应至少达到 `verified` 或经过显式授权。

---

## 9. 关系对象

### 9.1 Relation Object

```json
{
  "relation_type": "supports",
  "target_type": "memory",
  "target_id": "mem_01JZ0000000000000000000001",
  "description": "该记忆支持用户的文档风格偏好。"
}
```

### 9.2 关系类型

| 值 | 说明 |
|---|---|
| `supports` | 支持另一条记忆或判断 |
| `contradicts` | 与另一条记忆冲突 |
| `supersedes` | 替代旧记忆 |
| `derived_from` | 从另一对象推导而来 |
| `related_to` | 一般关联 |
| `used_by_skill` | 被某个技能使用 |
| `evaluated_by` | 被某个评测样例验证 |

---

## 10. 生命周期

### 10.1 状态流转

```text
candidate
  ↓ accept
active
  ↓ update
active + evolution event
  ↓ supersede
superseded
  ↓ archive
archived
  ↓ delete
deleted
```

冲突情况：

```text
active
  ↓ conflict detected
disputed
  ↓ user resolves
active / superseded / deleted
```

### 10.2 写入规则

写入长期记忆前，应完成：

1. 来源检查；
2. 类型判断；
3. 敏感级别判断；
4. 置信度评分；
5. 重要性评分；
6. 冲突检测；
7. 权限设置；
8. 必要时用户确认；
9. 生成 Evolution Log。

### 10.3 更新规则

更新记忆时不得直接覆盖旧内容，应：

- 保留更新前内容；
- 记录更新原因；
- 记录触发来源；
- 生成演进日志；
- 对重要记忆保留回滚点。

### 10.4 删除规则

删除应包括：

- 主记录状态改为 `deleted`；
- 从检索索引中移除；
- 从向量索引中移除或置为不可检索；
- 从训练候选池中移除；
- 清理缓存；
- 写入 Evolution Log；
- 多设备同步删除状态。

可以保留最小墓碑记录用于同步和审计，但墓碑记录不得包含原始敏感内容。

---

## 11. 冲突处理

### 11.1 冲突类型

| 类型 | 说明 |
|---|---|
| factual_conflict | 事实冲突 |
| preference_conflict | 偏好变化或冲突 |
| goal_conflict | 目标变化 |
| permission_conflict | 权限冲突 |
| sensitivity_conflict | 敏感级别冲突 |
| stale_memory | 旧记忆可能过时 |

### 11.2 冲突记录示例

```json
{
  "memory_id": "mem_new",
  "relations": [
    {
      "relation_type": "contradicts",
      "target_type": "memory",
      "target_id": "mem_old",
      "description": "用户对输出风格的偏好发生变化。"
    }
  ],
  "status": "disputed"
}
```

### 11.3 解决策略

- 用户明确更新优先于旧记忆；
- 新近行为不必然覆盖长期偏好；
- 推断记忆不得覆盖用户确认记忆；
- 高置信记忆和高重要记忆冲突时应要求确认；
- 解决冲突后应生成演进日志。

---

## 12. 检索要求

Memory Retriever 应综合以下因素排序：

- 语义相关性；
- 记忆类型；
- 重要性；
- 置信度；
- 新近性；
- 有效期；
- 权限；
- 敏感级别；
- 用户当前任务目标。

检索时必须先经过权限过滤，再进入模型上下文。

```text
Memory Store
  ↓
Permission Filter
  ↓
Sensitivity Filter
  ↓
Relevance Ranking
  ↓
Context Packing
  ↓
Model Router
```

---

## 13. 导入导出格式

### 13.1 文件格式

建议支持：

- JSONL：适合增量导入导出；
- JSON：适合完整备份；
- SQLite：适合本地运行；
- Markdown + Metadata：适合用户可读备份。

### 13.2 JSONL 示例

```jsonl
{"schema_version":"0.1","memory_id":"mem_001","type":"preference","content":"用户偏好简洁、直接、重点突出的文档风格。"}
{"schema_version":"0.1","memory_id":"mem_002","type":"goal","content":"用户希望将 Zhiné 建设为开源个人智慧伙伴项目。"}
```

### 13.3 导出要求

导出包应包含：

```text
memory.jsonl
memory-index-metadata.json
permissions.json
relations.jsonl
evolution-log.jsonl
README.md
```

敏感内容导出前应提醒用户。

---

## 14. 与 Evolution Log 的关系

任何以下行为都必须生成 Evolution Log：

- 新增记忆；
- 更新记忆；
- 删除记忆；
- 合并记忆；
- 冲突解决；
- 权限变更；
- 敏感级别变更；
- 进入训练候选池；
- 从训练候选池移除。

Memory Record 只描述当前状态。Evolution Log 描述变化过程。

---

## 15. 与 Personal Benchmark 的关系

个人评测集可以引用记忆，用于验证系统是否真正理解用户。

示例评测问题：

```json
{
  "test_id": "bench_memory_001",
  "required_memory_ids": ["mem_001", "mem_002"],
  "prompt": "请按照我偏好的风格，说明 Zhiné 当前定位。",
  "expected_traits": ["简洁", "重点突出", "使用 Personal Intelligence Companion 口径"]
}
```

---

## 16. 最小合规要求

一个实现若声称支持 Personal Memory Format v0.1，至少必须支持：

1. `memory_id`；
2. `type`；
3. `content`；
4. `source`；
5. `confidence`；
6. `importance`；
7. `sensitivity`；
8. `permissions`；
9. `verification`；
10. `created_at`；
11. `updated_at`；
12. 导出 JSONL；
13. 删除和回滚记录；
14. 与 Evolution Log 关联。

---

## 17. 后续版本方向

v0.2 应补充：

- JSON Schema；
- 加密字段规范；
- 多设备同步冲突策略；
- 向量索引元数据规范；
- 记忆压缩和摘要策略；
- 记忆衰减模型；
- 训练候选池字段；
- 与 Skill Graph 的关系规范。
