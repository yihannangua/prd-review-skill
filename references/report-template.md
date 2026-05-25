# Report Template

Use this structure for the final review report. Adapt headings when the user's requested format differs.

```markdown
# 需求业务深度评审报告

## 1. 总体结论

- 评审对象：
- 评审范围：
- 是否建议进入设计/开发/测试：
- 最大风险：
- 优先修复项：

## 2. 业务理解

### 2.1 业务目标

| 类型 | 内容 |
|------|------|
| Stated |  |
| Inferred |  |
| Missing |  |
| Question |  |

### 2.2 业务对象与数据关系

| 对象 | 含义 | 关键标识 | 来源/归属模块 | 依赖关系 | 生命周期/状态 |
|------|------|----------|----------------|----------|---------------|

### 2.3 模块地图

| 模块 | 职责 | 上游依赖 | 下游影响 | 关键风险 |
|------|------|----------|----------|----------|

### 2.4 核心流程

- 流程 1：
- 流程 2：

## 3. 核心风险摘要

| 风险 | 影响 | 优先级 | 建议 |
|------|------|--------|------|

## 4. 模块级评审

### 4.x 模块名称

**理解：**

**关键规则：**

**发现的问题：**

**建议修改：**

**建议测试场景：**

## 5. 跨模块问题

| ID | 严重程度 | 涉及模块 | 问题 | 影响 | 建议 |
|----|----------|----------|------|------|------|

## 6. 详细问题清单

| ID | 严重程度 | 类型 | 模块 | 位置 | 问题 | 为什么重要 | 修改建议 |
|----|----------|------|------|------|------|------------|----------|

## 7. 建议补充/修改文案

### 7.x 文案标题

建议插入位置：

```text
建议文案
```

## 8. 待产品确认问题

| ID | 问题 | 背景 | 可选决策 | 影响 |
|----|------|------|----------|------|

## 9. 建议测试场景

| 模块 | 场景 | 前置条件 | 操作 | 期望结果 |
|------|------|----------|------|----------|
```

## Writing Guidance

- Put the most important risks near the top.
- Do not bury blockers in a long table only.
- Use specific module names from the source document.
- When proposing wording, make it concrete enough to paste into a PRD.
- If the document is very large, summarize low-risk modules and go deep on high-risk modules.

