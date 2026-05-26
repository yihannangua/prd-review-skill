# Release Process

All commits and GitHub releases for this repository should include Chinese information.

## Commit Messages

Every commit should include at least a Chinese summary or Chinese detail. Bilingual commit messages are preferred.

Recommended format:

```text
English summary / 中文摘要

English details:
- ...

中文说明：
- ...
```

Example:

```text
Add requirement quality checklist / 增加需求质量检查清单

English details:
- Adds explicit checks for terminology, priority, ambiguity, and contradictions.

中文说明：
- 增加术语一致性、优先级一致性、歧义和矛盾需求检查。
```

## GitHub Releases

Every GitHub release must include both English and Chinese release notes.

Recommended format:

```markdown
## What's Changed

- English change 1
- English change 2

## 中文更新

- 中文变更 1
- 中文变更 2
```

## Local Commit Template

This repository includes `.gitmessage`. Configure it with:

```bash
git config commit.template .gitmessage
```

This is a local developer convenience. The release requirement still applies even when commits are created by another tool.

## Related Maintenance Docs

- `CONTRIBUTING.md`: contribution and repository layering rules.
- `docs/release-checklist.md`: release checklist.
- `docs/troubleshooting.md`: GitHub, SSH, and publishing troubleshooting.

## 中文补充

- `CONTRIBUTING.md`：贡献方式和仓库分层规则。
- `docs/release-checklist.md`：版本发布检查清单。
- `docs/troubleshooting.md`：GitHub、SSH 和发布问题排查。
