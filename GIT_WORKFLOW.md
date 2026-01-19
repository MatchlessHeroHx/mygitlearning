Git and GitHub workflow (Simple & Safe) | Git 与 GitHub 工作流（简易且安全）
================================================================================

Goal | 目标
----
- Keep main stable. | 保持 `main` 分支稳定。
- Develop each feature in its own branch. | 每个功能都在独立分支中开发。
- Merge only when feature is ready. | 仅在功能就绪时进行合并。

Daily flow (Safe) | 日常工作流（安全模式）
-------------------------
1) Start from main and sync | 同步主分支
```bash
git switch main
git pull
```

2) Create a feature branch | 创建功能分支
```bash
git switch -c feat/login
```

3) Work and commit in small steps | 小步提交
```bash
git status -sb
git add <files>
git commit -m "feat: add login form"
```

4) Push branch to GitHub | 推送至 GitHub
```bash
git push -u origin feat/login
```

5) Merge back to main (after review) | 合并回主分支（评审后）
```bash
git switch main
git pull
git merge --no-ff feat/login
git push
```

6) Clean up the branch | 地理分支
```bash
git branch -d feat/login
git push origin --delete feat/login
```

Key commands (Common) | 常用必备命令
---------------------
- Check status | 查看状态: `git status -sb`
- See history | 查看历史: `git log --oneline --decorate --graph -n 20`
- Stage files | 暂存文件: `git add <file>` or `git add .`
- Commit | 提交变更: `git commit -m "message"`
- Push | 推送代码: `git push`
- Pull | 拉取最新: `git pull`

Undo (Safe on shared history) | 撤销（适用于共享仓库的安全方式）
-----------------------------
- Revert a commit (creates a new commit that undoes it) | 还原提交（生成一个相反的新提交）:
```bash
git revert <commit>
```
- If a revert triggers conflicts | 处理还原冲突:
```bash
git add <file>
git revert --continue
```
- Abort the revert | 放弃还原:
```bash
git revert --abort
```

Undo (Rewrite history, use only if NOT pushed) | 撤销（重写历史，仅限未推送时使用）
----------------------------------------------
- Move branch pointer and discard commits | 强制重置并丢弃提交:
```bash
git reset --hard <commit>
```
- Or edit history interactively | 交互式变基（编辑历史）:
```bash
git rebase -i <base_commit>
```

Conflict resolution (Quick) | 冲突解决（快速指南）
---------------------------
1) Open conflicted files, keep the final content you want. | 打开冲突文件，保留最终目标内容。
2) Remove conflict markers `<<<<<<<`, `=======`, `>>>>>>>`. | 移除所有冲突标记。
3) Stage and continue | 暂存并继续:
```bash
git add <file>
git merge --continue
```

Remote setup (First time) | 远程仓库初始化
-------------------------
```bash
git remote add origin https://github.com/<user>/<repo>.git
git push -u origin main
```

Tip | 建议
---
- To avoid breaking the project, never develop directly on main. | 严禁在 `main` 直接开发，以免破坏项目稳定性。

