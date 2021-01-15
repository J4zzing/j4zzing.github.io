---
title: Wonderful-Git
tags:
---

## Commit

**把当前Commit回退到Stage状态**

```sh
git reset --soft HEAD^
```

https://stackoverflow.com/questions/7214039/how-do-you-move-a-commit-to-the-staging-area-in-git

https://git-scm.com/docs/git-reset



## Branch

**根据特定commit创建新的分支**

```sh
git branch branchname <sha1-of-commit>

git branch branchname HEAD~3

git checkout -b branchname <sha1-of-commit or HEAD~3>
```

https://stackoverflow.com/questions/2816715/branch-from-a-previous-commit-using-git



**Apply a specific commit to current branch**

```sh
git cherry-pick <commit>
```

https://stackoverflow.com/questions/881092/how-to-merge-a-specific-commit-in-git

[`git cherry-pick`](https://git-scm.com/docs/git-cherry-pick)



## Merge

合并冲突时选择某个文件版本

```sh
git checkout 

```

https://stackoverflow.com/questions/914939/simple-tool-to-accept-theirs-or-accept-mine-on-a-whole-file-using-git



## Rebase

https://git-scm.com/book/en/v2/Git-Branching-Rebasing



## Stash

找回误删的stash，只能找到带WIP的

```sh
git fsck --unreachable | grep commit | cut -d" " -f3 | xargs git log --merges --no-walk --grep=WIP
```

https://stackoverflow.com/questions/89332/how-to-recover-a-dropped-stash-in-git



## 迁移仓库

```
cd existing_repo
git remote rename origin old-origin
git remote add origin git@gitlab.codemao.cn:caijingzheng/codemao-audio.git
git push -u origin --all
git push -u origin --tags
```

https://intellipaat.com/community/3649/git-fetch-all-branches-how-to-fetch-all-git-branches

https://stackoverflow.com/questions/67699/how-to-clone-all-remote-branches-in-git/4754797#4754797

