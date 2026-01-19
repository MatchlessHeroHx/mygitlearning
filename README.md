# Git Learning Workspace | Git 学习工作坊

一个用于练习 Git 与 GitHub 的轻量工作区，包含最小但实用的流程文档与操作指南。

## 目录导航

- [核心工作流速记](GIT_WORKFLOW.md)
- [分支开发流程](BRANCH_WORKFLOW.md)
- [User Guide（中文速查）](Guide/UserGuide.md)

## 适用场景

- 个人项目需要稳定的 `main` 分支
- 每个功能用分支隔离，避免改乱主线
- 希望有一份简洁可复用的 Git/GitHub 参考

## 快速上手（最短路径）

1) 从 `main` 拉最新
```bash
git switch main
git pull
```

2) 新功能开分支
```bash
git switch -c feat/your-feature
```

3) 提交并推送
```bash
git add <files>
git commit -m "feat: your message"
git push -u origin feat/your-feature
```

4) 合并回 `main`
```bash
git switch main
git pull
git merge --no-ff feat/your-feature
git push
```

## 约定（建议）

- 不直接在 `main` 上做开发
- 每次改动尽量小步提交
- 合并冲突时先 `git status` 再处理
