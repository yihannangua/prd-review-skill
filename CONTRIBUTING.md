# Contributing

Thank you for improving `prd-review`. This repository is maintained as a public Agent Skill, so changes should keep the skill useful, installable, and easy to review.

## Working Principles

- Manage every skill change with git.
- Discuss or outline design changes before implementation when the change affects skill behavior, review methodology, public naming, release process, or repository structure.
- Keep `prd-review/SKILL.md` focused on agent workflow and trigger guidance.
- Put detailed review methods, checklists, and templates in `prd-review/references/`.
- Keep repository maintenance process outside the skill runtime files.
- Use bilingual commit messages or include Chinese information in every commit.
- Use bilingual GitHub release notes for every published version.

## What Belongs In The Skill

Add content to `prd-review/SKILL.md` or `prd-review/references/` when it improves PRD or requirement review behavior, for example:

- Business rule clarity checks
- Terminology consistency checks
- Feature-description consistency checks
- Data definition and lifecycle checks
- Priority consistency checks
- Contradiction and ambiguity detection
- Module, workflow, permission, data consistency, integration, and testability review guidance

## What Belongs Outside The Skill

Keep maintenance and publishing guidance outside `prd-review/`, for example:

- Git workflow
- Commit message requirements
- GitHub release process
- SSH and GitHub troubleshooting
- Publishing checklists
- Repository examples and README content

Use:

```text
README.md
RELEASE_PROCESS.md
CONTRIBUTING.md
docs/release-checklist.md
docs/troubleshooting.md
.gitmessage
```

## Development Workflow

1. Check repository status:

   ```bash
   git status --short --branch
   ```

2. Make the smallest coherent change.

3. If the change affects skill discovery or publishing, run:

   ```bash
   gh skill publish --dry-run
   ```

4. Commit with bilingual information:

   ```text
   English summary / 中文摘要

   English details:
   - ...

   中文说明：
   - ...
   ```

5. Push through SSH:

   ```bash
   git push
   ```

6. For releases, follow `docs/release-checklist.md`.

## 中文说明

欢迎改进 `prd-review`。这个仓库作为公开 Agent Skill 维护，因此每次变更都应保持 skill 可安装、可发布、可审阅。

### 工作原则

- 所有 skill 变更都使用 git 管理。
- 涉及 skill 行为、评审方法、公开命名、发布流程或仓库结构的变更，先梳理方案再实现。
- `prd-review/SKILL.md` 只放 agent 触发和工作流。
- 详细评审方法、检查清单和报告模板放在 `prd-review/references/`。
- 仓库维护和发布流程不要写进 skill 运行文件。
- 每次 commit 都要包含中文信息，推荐中英双语。
- 每次 GitHub release 都要包含英文和中文发布说明。

### 应写进 skill 的内容

和 PRD/需求文档评审能力直接相关的内容应写入 `prd-review/SKILL.md` 或 `prd-review/references/`，例如业务规则清晰性、术语一致性、数据定义统一、优先级一致性、矛盾需求和歧义检查。

### 不应写进 skill 的内容

git 工作流、提交规范、GitHub 发布流程、SSH 配置、故障排查、发布检查清单等属于仓库维护文档，应放在根目录或 `docs/` 中。

