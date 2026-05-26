# Release Checklist

Use this checklist before publishing a new `prd-review` version.

## Pre-Release

- [ ] Confirm the working tree is clean or only contains intended changes.

  ```bash
  git status --short --branch
  ```

- [ ] Confirm the skill name and directory match.

  ```text
  prd-review/SKILL.md -> name: prd-review
  directory -> prd-review/
  ```

- [ ] Update `CHANGELOG.md` with both English and Chinese meaning when the change is user-visible.
- [ ] Update `README.md` if installation, usage, output, examples, or repository structure changed.
- [ ] Update `examples/` if the expected output shape changed.
- [ ] Keep maintenance docs outside `prd-review/`.
- [ ] Run the publishing dry run:

  ```bash
  gh skill publish --dry-run
  ```

- [ ] Confirm only the expected warning appears. The tag protection warning is advisory:

  ```text
  no active tag protection rulesets found
  ```

## Commit And Push

- [ ] Commit with bilingual information.

  ```text
  English summary / 中文摘要

  English details:
  - ...

  中文说明：
  - ...
  ```

- [ ] Push through SSH.

  ```bash
  git push
  ```

- [ ] Confirm local and remote are aligned.

  ```bash
  git status --short --branch
  git log --graph --oneline --decorate --all -8
  ```

## Publish

- [ ] Publish with a semantic version tag.

  ```bash
  gh skill publish --tag vX.Y.Z
  ```

- [ ] Release notes must include English and Chinese sections.

Recommended format:

```markdown
## What's Changed

- English change 1

## 中文更新

- 中文变更 1
```

## Post-Release Verification

- [ ] Verify release status:

  ```bash
  gh release view vX.Y.Z --json url,tagName,isDraft,isPrerelease,targetCommitish
  ```

- [ ] Verify remote branch and tag point to the intended commit:

  ```bash
  git ls-remote origin refs/heads/main refs/tags/vX.Y.Z
  ```

- [ ] Verify repository visibility and topic:

  ```bash
  gh repo view yihannangua/prd-review-skill --json url,isPrivate,repositoryTopics
  ```

- [ ] If this release affects marketplace discoverability, verify marketplace preparation:

  ```bash
  sed -n '1,220p' docs/marketplace-publishing.md
  ```

## 中文检查清单

发布新版本前请确认：

- [ ] 工作区干净，或只包含预期变更。
- [ ] skill 目录名和 `SKILL.md` 中的 `name` 一致。
- [ ] 用户可见变更已更新 `CHANGELOG.md`。
- [ ] 安装、用法、输出或示例变化已更新 `README.md`。
- [ ] 发布前已执行 `gh skill publish --dry-run`。
- [ ] commit 包含中文信息。
- [ ] release notes 包含英文和中文。
- [ ] 发布后已验证 release、远程 main 和 tag。
- [ ] 如果这次发布影响技能市场收录，已检查 `docs/marketplace-publishing.md`。
