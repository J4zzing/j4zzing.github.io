---
title: Phabricator workflow
date: 2020-08-05 15:35:28
tags:
- Phabricator
- arcanist
---

Altered from this gist: https://gist.github.com/sekimura/6367366

- create tasks `T{NNNN}` assign them

- create and switch to a branch `git checkout -b <branch name>`

- make some changes and commit until it gets ready to be reviewed

  `git commit -am 'comment here'`

- check if it's lint free (NOTE: it runs lint against only modified files)

  `arc lint`

- push a review request to the server. This will create a diff with id `D{NNNN}`

  `arc diff [remote branch name] [--draft]`

- As a reviewer, you can apply the change set on your local by using `arc patch D{NNNN}`

  `arc patch D5678`

- if reviewers post a comment and you need to update the change set, commit more changes on that branch

  `git commit -am 'update'`

- and push updated change set to the server

  `arc diff --update D5678`

- To check status of review requests which you have posted, run `arc list` which will give you a list of Status, Diff ID and title

  `arc list`

- Once review request got accepted, merge changes to a remote branch. `arc land` command will take care of merging/rebasing branch and deleting your working branch... And pushing changes to origin/master.

  `arc land [--onto <remote branch name>] --strategy squash`

- viola!

### More

https://secure.phabricator.com/book/phabricator/article/arcanist_diff/

https://secure.phabricator.com/T13547