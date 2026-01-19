Branch Workflow (Feature Branch -> Merge -> Cleanup) | 分支工作流（功能分支 -> 合并 -> 清理）
================================================================================

Title | 标题
-----
Feature Branch Development and Merge Back to Main | 功能分支开发并合并回主分支

When to use | 何时使用
-----------
- You want to add a feature without risking the stability of `main`. | 你想添加新功能而不影响 `main` 分支的稳定性。
- You need a clean, reviewable history for a specific change. | 你需要为特定更改保留清晰、可评审的历史记录。
- You want the option to discard a feature without affecting the main branch. | 你希望可以选择放弃某个功能而不影响主分支。

Key commands and meanings | 关键命令及其含义
-------------------------
1) Start clean from main | 从 main 分支开始，保持代码最新
```bash
git switch main
git pull
```
- `git switch main`: move to the main branch. | 切换到主分支。
- `git pull`: fetch and merge the latest changes from GitHub. | 从 GitHub 获取并合并最新更改。

2) Create a feature branch | 创建功能分支
```bash
git switch -c feat/workflow-doc
```
- `git switch -c`: create and switch to a new branch in one step. | 创建并一步切换到新分支。

3) Stage and commit changes | 暂存并提交代码
```bash
git add <files>
git commit -m "docs: add git workflow guide"
```
- `git add`: stage files for commit. | 将文件添加到暂存区。
- `git commit`: create a snapshot (version) with a message. | 创建一个带有消息的快照（版本）。

4) Push the branch to GitHub | 将分支推送至 GitHub
```bash
git push -u origin feat/workflow-doc
```
- `git push`: send local commits to GitHub. | 将本地提交发送到 GitHub。
- `-u`: set upstream tracking so future `git push` is simpler. | 设置上游追踪，以便后续的 `git push` 执行更简单。

5) Merge the feature branch back to main | 将功能分支合并回主分支
```bash
git switch main
git pull
git merge --no-ff feat/workflow-doc
git push
```
- `git merge --no-ff`: force a merge commit even if a fast-forward is possible, so the feature's history is explicit. | 即使可以进行快进合并，也强制创建一个合并提交，以使功能的历史记录清晰可见。

6) Clean up the feature branch | 清理功能分支
```bash
git branch -d feat/workflow-doc
git push origin --delete feat/workflow-doc
```
- `git branch -d`: delete the local feature branch. | 删除本地功能分支。
- `git push origin --delete`: delete the remote feature branch. | 删除远程功能分支。

Notes | 注意事项
-----
- Keep `main` stable; do all development in branches. | 保持 `main` 分支稳定；所有开发均在分支中进行。
- If you are collaborating, create a PR instead of merging directly on `main`. | 如果你是与他人协作，请创建 PR（拉取请求）而不是直接合并到 `main`。

