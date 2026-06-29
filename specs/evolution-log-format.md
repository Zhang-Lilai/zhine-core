# Personal Evolution Log Format

> **Version 0.1 / Open Draft**  
> **Specification Name:** Personal Evolution Log Format  
> **Scope:** Personal Cognitive Model changes, audit, rollback, evaluation and governance

---

## 0. 规范定位

Personal Evolution Log 定义 Zhiné 中个人认知模型演进事件的记录格式。

Zhiné 的核心不是让模型自动变化，而是让每一次变化都有来源、有理由、有评估、有边界、有版本、有回滚。

Evolution Log 是个人认知模型可治理、可审计、可迁移、可持续成长的基础。

---

## 1. 设计目标

Evolution Log 的目标：

1. 记录个人记忆、技能、策略、评测集、适配层和权限的变化；
2. 支持用户查看系统为什么发生变化；
3. 支持回滚错误记忆、错误策略和错误适配；
4. 支持评测成长前后的质量变化；
5. 支持跨设备同步和冲突解决；
6. 支持导入导出和第三方实现兼容；
7. 为受控训练和模型适配提供治理证据。

---

## 2. 非目标

本规范不定义：

- 具体日志数据库；
- 分布式一致性算法；
- 加密签名算法；
- 完整备份系统；
- UI 展示方式；
- 训练流水线实现。

---

## 3. 核心概念

| 概念 | 定义 |
|---|---|
| Evolution Event | 一次个人认知资产变化事件 |
| Actor | 触发事件的主体，如用户、系统、工具、导入程序 |
| Target | 被改变的对象，如记忆、技能、策略、评测、适配层 |
| Before / After | 变更前后状态 |
| Evaluation | 变更是否通过评测或安全检查 |
| Rollback | 是否支持回滚以及如何回滚 |
| Impact Scope | 变化影响范围 |
| Integrity | 事件完整性和防篡改信息 |

---

## 4. 事件对象结构

### 4.1 Evolution Event

```json
{
  "schema_version": "0.1",
  "event_id": "evo_01JZ0000000000000000000000",
  "owner_id": "user_local",
  "event_type": "memory.update",
  "event_status": "committed",
  "timestamp": "2026-06-28T20:00:00+08:00",
  "actor": {
    "actor_type": "user",
    "actor_id": "user_local",
    "display_name": "Local User"
  },
  "trigger": {
    "trigger_type": "user_feedback",
    "source_id": "conv_20260628_001",
    "description": "用户确认 Zhiné 对外定位应统一为个人智慧伙伴。"
  },
  "target": {
    "target_type": "memory",
    "target_id": "mem_01JZ0000000000000000000001",
    "target_path": "memory/profile/project_positioning"
  },
  "operation": "update",
  "before": {
    "summary": "Zhiné 定位为个人认知伴侣。",
    "hash": "sha256:before_hash_placeholder"
  },
  "after": {
    "summary": "Zhiné 对外定位为个人智慧伙伴，技术层保留个人认知模型。",
    "hash": "sha256:after_hash_placeholder"
  },
  "reason": "品牌层与技术层术语需要分层统一。",
  "impact_scope": ["brand_positioning", "technical_docs", "readme", "community_language"],
  "evaluation": {
    "required": true,
    "status": "passed",
    "method": "manual_review",
    "score_delta": null,
    "report_id": null
  },
  "permissions": {
    "user_confirmed": true,
    "remote_model_used": false,
    "training_data_affected": false
  },
  "rollback": {
    "available": true,
    "rollback_event_id": null,
    "method": "restore_previous_value"
  },
  "integrity": {
    "previous_event_hash": null,
    "event_hash": "sha256:event_hash_placeholder",
    "signature": null
  }
}
```

---

## 5. 字段定义

### 5.1 顶层字段

| 字段 | 类型 | 必填 | 说明 |
|---|---:|---:|---|
| `schema_version` | string | 是 | 规范版本 |
| `event_id` | string | 是 | 事件唯一 ID |
| `owner_id` | string | 是 | 个人资产所有者 |
| `event_type` | string | 是 | 事件类型 |
| `event_status` | enum | 是 | 事件状态 |
| `timestamp` | datetime | 是 | 事件发生时间 |
| `actor` | object | 是 | 触发主体 |
| `trigger` | object | 是 | 触发原因 |
| `target` | object | 是 | 被变更对象 |
| `operation` | enum | 是 | 操作类型 |
| `before` | object/null | 否 | 变更前状态摘要和哈希 |
| `after` | object/null | 否 | 变更后状态摘要和哈希 |
| `reason` | string | 是 | 变更理由 |
| `impact_scope` | array | 否 | 影响范围 |
| `evaluation` | object | 否 | 评测结果 |
| `permissions` | object | 否 | 授权信息 |
| `rollback` | object | 是 | 回滚信息 |
| `integrity` | object | 否 | 完整性信息 |

### 5.2 事件状态

`event_status` 可取值：

| 值 | 说明 |
|---|---|
| `proposed` | 已提出但未提交 |
| `pending_review` | 等待用户或系统评审 |
| `committed` | 已提交生效 |
| `rejected` | 已拒绝 |
| `rolled_back` | 已被回滚 |
| `superseded` | 已被后续事件替代 |
| `failed` | 执行失败 |

### 5.3 操作类型

`operation` 可取值：

| 值 | 说明 |
|---|---|
| `create` | 新建对象 |
| `update` | 更新对象 |
| `delete` | 删除对象 |
| `archive` | 归档对象 |
| `restore` | 恢复对象 |
| `merge` | 合并对象 |
| `split` | 拆分对象 |
| `permission_change` | 权限变更 |
| `sensitivity_change` | 敏感级别变更 |
| `evaluate` | 评测 |
| `train` | 训练或适配 |
| `deploy` | 启用新版本 |
| `rollback` | 回滚 |

---

## 6. 事件类型

### 6.1 事件命名规则

事件类型采用：

```text
<domain>.<action>
```

示例：

```text
memory.create
memory.update
skill.create
strategy.update
benchmark.evaluate
adapter.train
permission.change
sync.resolve_conflict
```

### 6.2 核心事件类型

| 事件类型 | 说明 |
|---|---|
| `memory.create` | 新增个人记忆 |
| `memory.update` | 更新个人记忆 |
| `memory.delete` | 删除个人记忆 |
| `memory.merge` | 合并重复记忆 |
| `memory.resolve_conflict` | 解决记忆冲突 |
| `knowledge.import` | 导入个人知识 |
| `knowledge.index` | 建立或更新知识索引 |
| `skill.create` | 新建技能卡 |
| `skill.update` | 更新技能卡 |
| `strategy.create` | 新建策略规则 |
| `strategy.update` | 更新策略规则 |
| `benchmark.create` | 新建评测样例 |
| `benchmark.run` | 运行评测 |
| `benchmark.update` | 更新评测集 |
| `candidate.add` | 加入训练候选池 |
| `candidate.remove` | 移出训练候选池 |
| `adapter.train` | 训练个人适配层 |
| `adapter.deploy` | 启用个人适配层 |
| `adapter.rollback` | 回滚个人适配层 |
| `permission.change` | 权限变更 |
| `sensitivity.change` | 敏感级别变更 |
| `sync.device_authorized` | 授权设备 |
| `sync.device_revoked` | 撤销设备 |
| `sync.resolve_conflict` | 同步冲突解决 |

---

## 7. Actor 对象

### 7.1 Actor Object

```json
{
  "actor_type": "system",
  "actor_id": "zhine_core_local",
  "display_name": "Zhiné Core"
}
```

### 7.2 Actor 类型

| 值 | 说明 |
|---|---|
| `user` | 用户本人 |
| `system` | Zhiné 系统 |
| `model` | 模型 |
| `tool` | 工具 |
| `plugin` | 插件 |
| `importer` | 导入程序 |
| `remote_teacher` | 远端教师模型 |

### 7.3 规则

- 模型触发的高影响变更不得自动提交；
- 远端教师模型不得直接写入长期资产，只能产生候选；
- 插件触发的事件必须包含插件 ID 和权限记录；
- 用户确认事件应清晰标记。

---

## 8. Target 对象

### 8.1 Target Object

```json
{
  "target_type": "skill",
  "target_id": "skill_research_analysis",
  "target_path": "skills/research/analysis"
}
```

### 8.2 Target 类型

| 值 | 说明 |
|---|---|
| `memory` | 个人记忆 |
| `knowledge` | 个人知识库对象 |
| `skill` | 技能卡或技能图谱节点 |
| `strategy` | 策略规则 |
| `benchmark` | 评测样例或评测集 |
| `adapter` | LoRA、Adapter 或路由策略 |
| `permission` | 权限配置 |
| `sync_state` | 设备或同步状态 |
| `training_candidate` | 训练候选数据 |

---

## 9. Before / After

### 9.1 设计目的

`before` 和 `after` 不一定保存完整对象，可以保存摘要、差异或哈希。

对于敏感对象，不应在日志中重复保存完整明文内容。

### 9.2 推荐结构

```json
{
  "summary": "变更摘要",
  "diff": {
    "field": "content",
    "old": "旧值摘要",
    "new": "新值摘要"
  },
  "hash": "sha256:...",
  "snapshot_ref": "snapshot_001"
}
```

### 9.3 规则

- 对 public / private 数据可保存摘要；
- 对 sensitive / secret 数据应优先保存哈希和快照引用；
- 回滚需要完整快照时，快照应加密存储；
- 日志不得成为隐私数据泄露的新通道。

---

## 10. Evaluation 对象

### 10.1 Evaluation Object

```json
{
  "required": true,
  "status": "passed",
  "method": "personal_benchmark",
  "benchmark_ids": ["bench_001", "bench_002"],
  "score_before": 0.72,
  "score_after": 0.81,
  "score_delta": 0.09,
  "report_id": "eval_report_001"
}
```

### 10.2 评测状态

| 值 | 说明 |
|---|---|
| `not_required` | 不需要评测 |
| `pending` | 等待评测 |
| `passed` | 通过评测 |
| `failed` | 未通过评测 |
| `manual_review_required` | 需要人工评审 |

### 10.3 评测规则

以下事件必须要求评测或人工确认：

- 更新高重要度记忆；
- 更新价值约束；
- 更新长期目标；
- 修改核心策略；
- 启用个人适配层；
- 使用个人数据训练；
- 大范围迁移或合并资产。

---

## 11. Rollback 对象

### 11.1 Rollback Object

```json
{
  "available": true,
  "rollback_event_id": null,
  "method": "restore_snapshot",
  "snapshot_ref": "snapshot_001",
  "expires_at": null
}
```

### 11.2 回滚方式

| 值 | 说明 |
|---|---|
| `restore_previous_value` | 恢复旧值 |
| `restore_snapshot` | 从快照恢复 |
| `reverse_patch` | 应用反向补丁 |
| `disable_version` | 禁用新版本 |
| `manual_repair` | 人工修复 |
| `not_available` | 不可回滚 |

### 11.3 回滚规则

- 高风险事件必须可回滚；
- 删除事件至少应支持短期恢复或墓碑记录；
- 训练和适配发布必须保留旧版本；
- 回滚本身也必须生成新的 Evolution Event；
- 回滚不得删除原审计记录。

---

## 12. 完整性字段

### 12.1 Integrity Object

```json
{
  "previous_event_hash": "sha256:previous_hash",
  "event_hash": "sha256:current_hash",
  "signature": "signature_placeholder"
}
```

### 12.2 设计目的

完整性字段用于：

- 发现日志篡改；
- 支持事件链校验；
- 支持跨设备同步一致性；
- 支持未来签名和备份验证。

v0.1 不强制实现签名，但建议保留字段。

---

## 13. 典型事件示例

### 13.1 新增记忆

```json
{
  "schema_version": "0.1",
  "event_id": "evo_memory_create_001",
  "owner_id": "user_local",
  "event_type": "memory.create",
  "event_status": "committed",
  "timestamp": "2026-06-28T20:10:00+08:00",
  "actor": {"actor_type": "user", "actor_id": "user_local"},
  "trigger": {"trigger_type": "manual", "description": "用户明确要求记住一项偏好。"},
  "target": {"target_type": "memory", "target_id": "mem_001"},
  "operation": "create",
  "before": null,
  "after": {"summary": "用户偏好正式、专业、简洁的文档风格。"},
  "reason": "用户显式表达长期偏好。",
  "impact_scope": ["memory", "personalization"],
  "evaluation": {"required": false, "status": "not_required"},
  "permissions": {"user_confirmed": true, "remote_model_used": false},
  "rollback": {"available": true, "method": "delete_created_record"}
}
```

### 13.2 更新策略

```json
{
  "schema_version": "0.1",
  "event_id": "evo_strategy_update_001",
  "owner_id": "user_local",
  "event_type": "strategy.update",
  "event_status": "committed",
  "timestamp": "2026-06-28T20:20:00+08:00",
  "actor": {"actor_type": "system", "actor_id": "zhine_core_local"},
  "trigger": {"trigger_type": "user_feedback", "description": "用户要求报告避免啰嗦和重复。"},
  "target": {"target_type": "strategy", "target_id": "strategy_document_concise"},
  "operation": "update",
  "before": {"summary": "普通文档修订策略。"},
  "after": {"summary": "制度、报告和技术文件应短、硬、清楚、能执行。"},
  "reason": "长期文档风格偏好需要固化为策略规则。",
  "impact_scope": ["writing", "document_generation"],
  "evaluation": {"required": true, "status": "manual_review_required"},
  "permissions": {"user_confirmed": true},
  "rollback": {"available": true, "method": "restore_previous_value"}
}
```

### 13.3 回滚事件

```json
{
  "schema_version": "0.1",
  "event_id": "evo_rollback_001",
  "owner_id": "user_local",
  "event_type": "memory.rollback",
  "event_status": "committed",
  "timestamp": "2026-06-28T20:30:00+08:00",
  "actor": {"actor_type": "user", "actor_id": "user_local"},
  "trigger": {"trigger_type": "user_request", "description": "用户指出该记忆错误。"},
  "target": {"target_type": "memory", "target_id": "mem_002"},
  "operation": "rollback",
  "before": {"summary": "错误记忆处于 active。"},
  "after": {"summary": "错误记忆已恢复到上一版本。"},
  "reason": "用户确认此前更新不准确。",
  "impact_scope": ["memory", "retrieval"],
  "evaluation": {"required": false, "status": "not_required"},
  "rollback": {"available": true, "rollback_event_id": "evo_memory_update_003", "method": "restore_previous_value"}
}
```

---

## 14. 日志存储与导出

### 14.1 推荐格式

- JSONL：推荐作为标准导入导出格式；
- SQLite：推荐作为本地运行存储；
- Parquet：可用于大规模分析；
- Markdown 报告：用于用户可读审计摘要。

### 14.2 JSONL 示例

```jsonl
{"schema_version":"0.1","event_id":"evo_001","event_type":"memory.create","event_status":"committed"}
{"schema_version":"0.1","event_id":"evo_002","event_type":"strategy.update","event_status":"committed"}
```

### 14.3 导出包

```text
evolution-log.jsonl
event-index.json
snapshots/
  snapshot_001.enc
  snapshot_002.enc
integrity.json
README.md
```

---

## 15. 与其他规范的关系

| 规范 | 关系 |
|---|---|
| Personal Memory Format | 记忆新增、更新、删除必须写入 Evolution Log |
| Personal Benchmark Protocol | 评测结果应写入 Evolution Log |
| Skill Graph Format | 技能节点变化应写入 Evolution Log |
| Model Router Protocol | 路由策略变化应写入 Evolution Log |
| Personal Adapter Format | 适配层训练、发布、回滚应写入 Evolution Log |
| Access & Sync Protocol | 设备授权、撤销、同步冲突应写入 Evolution Log |

---

## 16. 最小合规要求

声称支持 Evolution Log v0.1 的实现，至少必须支持：

1. 事件唯一 ID；
2. 事件类型；
3. 时间戳；
4. 触发主体；
5. 目标对象；
6. 操作类型；
7. 变更前后摘要；
8. 变更理由；
9. 回滚可用性；
10. JSONL 导出；
11. 记忆更新事件记录；
12. 权限变更事件记录；
13. 评测事件记录。

---

## 17. 后续版本方向

v0.2 应补充：

- JSON Schema；
- Patch 格式；
- 加密快照规范；
- 事件链签名；
- 多设备日志合并策略；
- 冲突解决算法；
- 与 Git-like 版本模型的关系；
- 用户可读审计报告格式。
