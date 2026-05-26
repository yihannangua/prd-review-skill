# Troubleshooting

This document records publishing and GitHub maintenance issues encountered while preparing `prd-review`.

## `gh skill publish --dry-run` Says Name Does Not Match Directory

Symptom:

```text
name "prd-review" does not match directory name "."
```

Cause:

The repository root was itself the skill directory. `gh skill publish` treated the directory name as `.`.

Fix:

Use a repository layout where the skill lives in a child directory:

```text
repo-root/
  prd-review/
    SKILL.md
    agents/openai.yaml
    references/
```

## GitHub HTTPS Push Times Out

Symptom:

```text
Failed to connect to github.com port 443 after 75001 ms
Couldn't connect to server
```

Cause:

Git over HTTPS could not reach GitHub from the local network, even though `gh api` might still work.

Preferred fix:

Use SSH for git remotes.

```bash
ssh-keygen -t ed25519 -C "54133432+yihannangua@users.noreply.github.com" -f ~/.ssh/id_ed25519_github -N ""
```

Add the public key to GitHub:

```bash
cat ~/.ssh/id_ed25519_github.pub
```

Configure SSH:

```text
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_github
  IdentitiesOnly yes
```

Switch remote:

```bash
git remote set-url origin git@github.com:yihannangua/prd-review-skill.git
```

Verify:

```bash
ssh -T git@github.com
git fetch origin
git push
```

## SSH Permission Denied

Symptom:

```text
git@github.com: Permission denied (publickey).
```

Fix:

- Confirm the public key is added to GitHub.
- Confirm `~/.ssh/config` points `github.com` to the correct private key.
- Confirm private key permissions:

  ```bash
  chmod 600 ~/.ssh/config ~/.ssh/id_ed25519_github
  ```

## GitHub API Fallback Can Create Incomplete Trees

Symptom:

Remote `main` contains only changed files or misses files that already existed locally.

Cause:

The Git Data API tree update was created incorrectly and did not preserve the full base tree.

Guidance:

- Prefer normal `git push` over API fallback.
- If API fallback is unavoidable, ensure the new tree is based on the full remote base tree.
- After API fallback, always run:

  ```bash
  git fetch origin --tags
  git log --graph --oneline --decorate --all -8
  git diff --stat origin/main..HEAD
  git diff --stat HEAD..origin/main
  ```

If the remote API commit is incomplete and the local commit is correct, fix by pushing the local commit through SSH:

```bash
git push --force-with-lease origin main
git tag -f vX.Y.Z HEAD
git push --force origin vX.Y.Z
```

Only force-update a published tag when correcting an erroneous release target.

## File Mode Changes After Publishing

Symptom:

```text
old mode 100644
new mode 100755
```

Cause:

Some local file systems or publishing commands may flip executable bits on Markdown/YAML files.

Fix:

If the file content is unchanged and only mode differs, ignore file mode in this repository:

```bash
git config core.filemode false
```

## 中文故障排查摘要

- 如果 `gh skill publish --dry-run` 提示目录名不匹配，把 skill 放到 `prd-review/` 子目录。
- 如果 HTTPS `git push` 超时，改用 SSH remote。
- 如果 SSH 提示 `Permission denied (publickey)`，检查 GitHub 是否已添加公钥，以及 `~/.ssh/config` 是否指向正确私钥。
- 尽量不要用 GitHub API fallback；如果用了，必须检查远程 tree 是否完整。
- 如果只出现文件权限位变化，可以设置 `git config core.filemode false`。

