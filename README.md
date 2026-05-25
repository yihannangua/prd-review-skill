# PRD Review Skill

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
prd-review/
  SKILL.md
  agents/openai.yaml
  references/
    review-framework.md
    issue-taxonomy.md
    module-review-template.md
    cross-module-checklist.md
    business-rule-checklist.md
    report-template.md
examples/
  sample-prd.md
  sample-review-report.md
```

## Privacy

Do not commit real customer documents, confidential PRDs, credentials, personal data, or proprietary business information to this public repository. Use sanitized or fictional examples only.

## License

MIT

