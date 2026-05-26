# Marketplace Publishing

This document records how to prepare and submit `prd-review` to public skill marketplaces.

## Publishing Goals

- Keep the GitHub repository as the source of truth.
- Publish installable releases through GitHub tags and releases.
- Make the repository discoverable by marketplace crawlers through clear metadata, topics, README content, examples, and release notes.
- Keep every public-facing update bilingual when possible, especially release notes and important maintenance docs.

## GitHub Agent Skill

GitHub should remain the canonical distribution channel.

1. Confirm the repository is public:

   ```bash
   gh repo view yihannangua/prd-review-skill --json url,isPrivate,repositoryTopics
   ```

2. Confirm required metadata:

   - Repository topic includes `agent-skills`.
   - `prd-review/SKILL.md` has `name`, `description`, and `license`.
   - `README.md` includes installation, usage, output shape, privacy notice, and examples.
   - `LICENSE`, `CHANGELOG.md`, and examples are present.

3. Validate before release:

   ```bash
   gh skill publish --dry-run
   ```

4. Publish a release:

   ```bash
   gh skill publish --tag vX.Y.Z
   ```

5. Verify the release:

   ```bash
   gh release view vX.Y.Z --json url,tagName,isDraft,isPrerelease,targetCommitish
   git ls-remote origin refs/heads/main refs/tags/vX.Y.Z
   ```

## Smithery

Smithery supports discovering and installing skills from GitHub-backed listings. Treat the GitHub repository and release as the source artifact, then register or import the GitHub repository through the Smithery website or API when available for the account.

Recommended preparation:

- Keep the GitHub repository public.
- Add marketplace-friendly topics:
  - `agent-skills`
  - `agent-skill`
  - `prd`
  - `requirements`
  - `requirement-review`
  - `product-management`
  - `codex`
  - `claude`
- Ensure README contains a short English summary and a Chinese summary.
- Ensure the skill can be installed from GitHub before submitting:

  ```bash
  gh skill install yihannangua/prd-review-skill
  ```

After Smithery lists the skill, verify search and install from Smithery CLI:

```bash
npx @smithery/cli@latest skill search "prd review"
npx @smithery/cli@latest skill add <listed-skill-id>
```

If Smithery requires an account or API key, complete that step in the browser/account settings first. Do not put API keys in the repository.

## SkillsMP

SkillsMP is oriented around public Agent Skill listings. The safest publishing path is to make the GitHub repository easy to crawl and install, then submit or wait for marketplace indexing.

Recommended preparation:

- Keep the repository public.
- Ensure the `agent-skills` topic exists.
- Add additional discovery topics for the domain.
- Keep the skill directory name and `SKILL.md` name aligned: `prd-review`.
- Keep release tags and GitHub release notes current.
- Use sanitized examples only.

After listing or indexing:

- Search SkillsMP for `prd-review` and `prd review`.
- Confirm the install command points to `yihannangua/prd-review-skill`.
- Confirm the description matches the current README and `SKILL.md`.
- Add the marketplace link back to README after the listing URL is known.

## Metadata Checklist

- [ ] Repository is public.
- [ ] Repository topics are complete.
- [ ] `prd-review/SKILL.md` frontmatter is valid.
- [ ] README has English and Chinese sections.
- [ ] Installation command is tested.
- [ ] `gh skill publish --dry-run` passes.
- [ ] Latest GitHub release has bilingual notes.
- [ ] Marketplace listing links are added to README after they exist.

## 中文说明

这个文档用于记录 `prd-review` 发布到技能市场前后的操作。

建议原则：

- GitHub 仓库作为唯一源码和发布源。
- 通过 GitHub tag 和 release 发布可安装版本。
- 通过清晰的 README、topic、示例和发布说明提高 Smithery、SkillsMP 等平台的可发现性。
- 不要把任何平台 token、API key 或真实业务文档提交到仓库。

发布到 Smithery 或 SkillsMP 前，应先保证：

- 仓库为 public。
- 已包含 `agent-skills` topic。
- 已补充 PRD、requirements、product-management 等领域 topic。
- `gh skill publish --dry-run` 校验通过。
- GitHub release 已发布并包含中文说明。
- README 中的安装和使用方式准确。

平台收录后，再把 Smithery / SkillsMP 的实际链接补回 README。
