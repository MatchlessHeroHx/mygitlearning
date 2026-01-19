Branch Workflow (Feature Branch -> Merge -> Cleanup) | 分支工作流（功能开发 -> 合并 -> 清理）
================================================================================

Title | 标题
-----
Feature Branch Development and Merge Back to Main | 功能分支开发及其向主分支的合并

When to use | 适用场景
-----------
- You want to add a feature without risking the stability of `main`. | 在不影响 `main` 分支稳定性的前提下开发新功能。
- You need a clean, reviewable history for a specific change. | 为特定的变更留存清晰、可评审的历史记录。
- You want the option to discard a feature without affecting the main branch. | 可选地舍弃某项功能而不对主分支产生任何影响。

Key commands and meanings | 核心命令与解析
-------------------------
1) Start clean from main | 从最新的主分支开始
```bash
git switch main
git pull
```
- `git switch main`: move to the main branch. | 切换至 `main` 主分支。
- `git pull`: fetch and merge the latest changes from GitHub. | 从 GitHub 拉取并同步最新代码。

2) Create a feature branch | 创建功能分支
```bash
git switch -c feat/workflow-doc
```
- `git switch -c`: create and switch to a new branch in one step. | 创建并同步切换到新分支（一步到位）。

3) Stage and commit changes | 暂存并提交代码
```bash
git add <files>
git commit -m "docs: add git workflow guide"
```
- `git add`: stage files for commit. | 将文件加入暂存区。
- `git commit`: create a snapshot (version) with a message. | 为当前变更创建快照（提交记录）。

4) Push the branch to GitHub | 推送分支至远程仓库
```bash
git push -u origin feat/workflow-doc
```
- `git push`: send local commits to GitHub. | 将本地提交推送至 GitHub。
- `-u`: set upstream tracking so future `git push` is simpler. | 建立上游追踪，简化后续推送流程。

5) Merge the feature branch back to main | 将功能合并回主分支
```bash
git switch main
git pull
git merge --no-ff feat/workflow-doc
git push
```
- `git merge --no-ff`: force a merge commit even if a fast-forward is possible, so the feature's history is explicit. | 强制创建合并提交（即使可快进），以保证功能演进历史的完整性。

6) Clean up the feature branch | 清理功能分支
```bash
git branch -d feat/workflow-doc
git push origin --delete feat/workflow-doc
```
- `git branch -d`: delete the local feature branch. | 删除本地功能分支。
- `git push origin --delete`: delete the remote feature branch. | 删除远程仓库的分支记录。

Notes | 贴士
-----
- Keep `main` stable; do all development in branches. | 始终保持 `main` 稳定；所有开发均应在独立分支中完成。
- If you are collaborating, create a PR instead of merging directly on `main`. | 团队协作时，应通过 Pull Request (PR) 流程进行合并，而非直接操作 `main`。


