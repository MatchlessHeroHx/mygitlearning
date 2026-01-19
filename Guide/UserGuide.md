Git/GitHub User Guide (核心流程速记)
=================================

目的
----
用最少步骤管理个人项目，避免在开发新功能时弄乱主分支。

核心流程（强烈推荐）
-------------------
1) 保持 main 稳定（不要直接在 main 上开发）
```bash
git switch main
git pull
```

2) 新功能开分支
```bash
git switch -c feat/your-feature
```

3) 修改与提交（小步快跑）
```bash
git status -sb
git add <files>
git commit -m "feat: your message"
```

4) 推送到 GitHub
```bash
git push -u origin feat/your-feature
```

5) 合并回 main（两种方式选一）
方式 A：走 PR（推荐）
- 在 GitHub 上创建 PR，合并后本地同步：
```bash
git switch main
git pull
```

方式 B：本地直接合并
```bash
git switch main
git pull
git merge --no-ff feat/your-feature
git push
```

6) 清理分支
```bash
git branch -d feat/your-feature
git push origin --delete feat/your-feature
```

关键指令说明
------------
- `git switch -c <branch>`：基于当前分支创建并切换到新分支。
- `git add <files>`：把改动加入暂存区，准备提交。
- `git commit -m "<msg>"`：创建一次提交（版本快照）。
- `git push`：把本地提交推送到 GitHub。
- `git pull`：从 GitHub 拉取并合并最新改动。
- `git merge --no-ff <branch>`：强制生成一次合并提交，保留分支合并痕迹。

常见问题（简答）
--------------
- 为什么不用 main 直接开发？  
  因为 main 应该随时可发布，分支能隔离风险。
- PR 有什么意义？  
  便于审查、记录讨论、触发 CI。
- 如果合并卡住？  
  先 `git status` 看冲突，解决后 `git add`，再 `git merge --continue`。

