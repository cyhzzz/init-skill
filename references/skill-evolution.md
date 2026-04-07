---
name: evolution
description: |
  进化引擎。扫描 corrections.jsonl 和 observations.jsonl，
  自动将重复出现的模式晋升为 learned-rules.md。
---

# Evolution Engine

## 触发条件

- 用户显式调用 `/evolve`
- 每周末自动审计

## 工作流程

### Step 1: 扫描纠正记录

读取 `.claude/memory/corrections.jsonl`：

```json
{"timestamp": "2024-01-15", "correction": "不要在循环里调用 API", "count": 3}
{"timestamp": "2024-01-16", "correction": "使用 zod 验证输入", "count": 2}
```

### Step 2: 识别模式

- 同一纠正出现 2 次以上 → 候选规则
- 同一观察被验证 3 次以上 → 候选模式

### Step 3: 晋升规则

将候选规则写入 `learned-rules.md`：

```markdown
## 2024-01-15 新增

- **禁止循环内调用 API** - 改用批量接口
- **输入必须验证** - 使用 zod
```

### Step 4: 清理

- 已晋升的纠正从 corrections.jsonl 移除
- 归档到 evolution-log.md

## 输出

```markdown
## 进化报告 - 2024-01-20

### 新增规则 (2)
1. 禁止循环内调用 API
2. 输入必须验证

### 已验证模式 (3)
1. 错误统一格式
2. 分页参数标准化
3. 日志分级记录

### 待观察 (1)
1. 缓存策略优化
```
