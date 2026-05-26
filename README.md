# PRD Review Skill

Language: [English](#english) | [中文](#中文)

## English

`prd-review` is an Agent Skill for deep PRD and requirements review. It helps an agent understand the business model, modules, data relationships, workflows, permissions, states, and rules in a product requirements document, then identify omissions, contradictions, ambiguity, implementation risk, and testability gaps.

This is not a template-compliance checker. It is intended to behave more like a senior product manager, business analyst, QA lead, and solution architect reviewing the same PRD together.

## What It Reviews

- Business goals and system boundaries
- Users, roles, permissions, and sensitive operations
- Business objects, identifiers, lifecycle, and ownership
- Module responsibilities and cross-module dependencies
- Core workflows, state transitions, side effects, and external integrations
- Data consistency, conflict handling, overwrite rules, retries, rollback, and auditability
- Exception paths, boundary cases, and acceptance-test readiness

## Install

Install the latest published version:

```bash
gh skill install yihannangua/prd-review-skill
```

Pin to the first release:

```bash
gh skill install yihannangua/prd-review-skill prd-review --pin v1.0.0
```

After installing, restart Codex or reload your editor window so the skill is discovered.

## Marketplace

Canonical source:

- GitHub: https://github.com/yihannangua/prd-review-skill

Marketplace listings will be added after they are available:

- Smithery: pending
- SkillsMP: pending

See `docs/marketplace-publishing.md` for publishing and verification steps.

## Usage

Example prompt:

```text
Use prd-review to deeply review the current requirement document.
First understand the business model, modules, data relationships, and cross-module rules.
Then identify errors, omissions, contradictions, ambiguity, and untestable requirements.
Give detailed modification advice and suggested PRD wording.
```

Chinese prompt:

```text
使用 prd-review 深度评审当前需求文档。
请先理解业务模式、模块功能、数据关系和模块间规则，
再指出错误、遗漏、冲突、歧义和不可测试问题，
并给出详细修改建议和建议补充文案。
```

## Output

The skill guides the agent to produce a report with:

- Overall readiness conclusion
- Business understanding and inferred domain model
- Business objects and data relationships
- Module map and module-level findings
- Cross-module consistency issues
- Detailed issue table with severity and rationale
- Suggested PRD additions or replacement wording
- Questions for product/business owners
- Suggested test scenarios

See `examples/sample-review-report.md` for a compact example.

## Repository Structure

```text
README.md
CHANGELOG.md
RELEASE_PROCESS.md
CONTRIBUTING.md
docs/
  marketplace-publishing.md
  release-checklist.md
  troubleshooting.md
prd-review/
  SKILL.md
  agents/openai.yaml
  references/
    review-framework.md
    issue-taxonomy.md
    module-review-template.md
    cross-module-checklist.md
    business-rule-checklist.md
    requirement-quality-checklist.md
    report-template.md
examples/
  sample-prd.md
  sample-review-report.md
```

## Privacy

Do not commit real customer documents, confidential PRDs, credentials, personal data, or proprietary business information to this public repository. Use sanitized or fictional examples only.

## Release Process

Commits and GitHub release notes should include Chinese information. See `RELEASE_PROCESS.md`.

For development and maintenance:

- `CONTRIBUTING.md`
- `docs/release-checklist.md`
- `docs/troubleshooting.md`

## License

MIT

## 中文

`prd-review` 是一个用于深度评审 PRD 和需求文档的 Agent Skill。它会引导智能体先理解文档中的业务模式、模块功能、数据关系、业务流程、权限、状态和规则，再识别错误、遗漏、冲突、歧义、实现风险和不可测试点。

它不是模板合规检查器。它更像是让一位资深产品经理、业务分析师、测试负责人和解决方案架构师一起审阅同一份 PRD。

## 评审内容

- 业务目标和系统边界
- 用户、角色、权限和敏感操作
- 业务对象、标识符、生命周期和数据归属
- 模块职责和跨模块依赖
- 核心流程、状态流转、副作用和外部系统集成
- 数据一致性、冲突处理、覆盖规则、重试、回滚和审计
- 异常路径、边界条件和验收测试可行性

## 安装

安装最新发布版本：

```bash
gh skill install yihannangua/prd-review-skill
```

固定安装第一个发布版本：

```bash
gh skill install yihannangua/prd-review-skill prd-review --pin v1.0.0
```

安装后，请重启 Codex 或重新加载编辑器窗口，让 Codex 发现新 skill。

## 技能市场

官方源码：

- GitHub: https://github.com/yihannangua/prd-review-skill

技能市场链接将在收录后补充：

- Smithery：待收录
- SkillsMP：待收录

发布和验证步骤见 `docs/marketplace-publishing.md`。

## 使用方式

示例 prompt：

```text
使用 prd-review 深度评审当前需求文档。
请先理解业务模式、模块功能、数据关系和模块间规则，
再指出错误、遗漏、冲突、歧义和不可测试问题，
并给出详细修改建议和建议补充文案。
```

英文 prompt：

```text
Use prd-review to deeply review the current requirement document.
First understand the business model, modules, data relationships, and cross-module rules.
Then identify errors, omissions, contradictions, ambiguity, and untestable requirements.
Give detailed modification advice and suggested PRD wording.
```

## 输出内容

这个 skill 会引导智能体输出一份结构化评审报告，通常包含：

- 总体结论和是否建议进入设计/开发/测试
- 对业务的理解和推断出的领域模型
- 业务对象和数据关系
- 模块地图和模块级问题
- 跨模块一致性问题
- 带严重程度和原因说明的详细问题清单
- 建议补充或替换到 PRD 的文案
- 需要产品或业务确认的问题
- 建议测试场景

可以查看 `examples/sample-review-report.md` 了解简化示例。

## 仓库结构

```text
README.md
CHANGELOG.md
RELEASE_PROCESS.md
CONTRIBUTING.md
docs/
  marketplace-publishing.md
  release-checklist.md
  troubleshooting.md
prd-review/
  SKILL.md
  agents/openai.yaml
  references/
    review-framework.md
    issue-taxonomy.md
    module-review-template.md
    cross-module-checklist.md
    business-rule-checklist.md
    requirement-quality-checklist.md
    report-template.md
examples/
  sample-prd.md
  sample-review-report.md
```

## 隐私提醒

不要把真实客户文档、保密 PRD、账号凭据、个人数据或商业敏感信息提交到这个公开仓库。示例请使用脱敏或虚构内容。

## 发布规范

每次提交和 GitHub 版本发布都应该包含中文信息。详见 `RELEASE_PROCESS.md`。

开发和维护文档：

- `CONTRIBUTING.md`
- `docs/release-checklist.md`
- `docs/troubleshooting.md`

## 许可证

MIT
