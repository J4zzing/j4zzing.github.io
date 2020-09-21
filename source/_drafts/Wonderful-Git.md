---
title: Wonderful-Git
tags:
---

## Branch

**根据特定commit创建新的分支**

https://stackoverflow.com/questions/2816715/branch-from-a-previous-commit-using-git

```sh
git branch branchname <sha1-of-commit>

git branch branchname HEAD~3

git checkout -b branchname <sha1-of-commit or HEAD~3>
```



**Apply a specific commit to current branch**

```sh
git cherry-pick d42c389
```

https://stackoverflow.com/questions/881092/how-to-merge-a-specific-commit-in-git

[`git cherry-pick`](https://git-scm.com/docs/git-cherry-pick)



## Merge

合并冲突时选择某个文件版本

https://stackoverflow.com/questions/914939/simple-tool-to-accept-theirs-or-accept-mine-on-a-whole-file-using-git



## Rebase

https://git-scm.com/book/en/v2/Git-Branching-Rebasing

