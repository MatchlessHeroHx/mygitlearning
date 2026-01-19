Git and GitHub workflow (simple, safe)
=====================================

Goal
----
- Keep main stable.
- Develop each feature in its own branch.
- Merge only when feature is ready.

Daily flow (safe)
-----------------
1) Start from main and sync
```bash
git switch main
git pull
```

2) Create a feature branch
```bash
git switch -c feat/login
```

3) Work and commit in small steps
```bash
git status -sb
git add <files>
git commit -m "feat: add login form"
```

4) Push branch to GitHub
```bash
git push -u origin feat/login
```

5) Merge back to main (after review)
```bash
git switch main
git pull
git merge --no-ff feat/login
git push
```

6) Clean up the branch
```bash
git branch -d feat/login
git push origin --delete feat/login
```

Key commands (common)
---------------------
- Check status: `git status -sb`
- See history: `git log --oneline --decorate --graph -n 20`
- Stage files: `git add <file>` or `git add .`
- Commit: `git commit -m "message"`
- Push: `git push`
- Pull: `git pull`

Undo (safe on shared history)
-----------------------------
- Revert a commit (creates a new commit that undoes it):
```bash
git revert <commit>
```
- If a revert triggers conflicts:
```bash
git add <file>
git revert --continue
```
- Abort the revert:
```bash
git revert --abort
```

Undo (rewrite history, use only if NOT pushed)
----------------------------------------------
- Move branch pointer and discard commits:
```bash
git reset --hard <commit>
```
- Or edit history interactively:
```bash
git rebase -i <base_commit>
```

Conflict resolution (quick)
---------------------------
1) Open conflicted files, keep the final content you want.
2) Remove conflict markers `<<<<<<<`, `=======`, `>>>>>>>`.
3) Stage and continue:
```bash
git add <file>
git merge --continue
```

Remote setup (first time)
-------------------------
```bash
git remote add origin https://github.com/<user>/<repo>.git
git push -u origin main
```

Tip
---
- If you are worried about breaking the project, never develop directly on main.
