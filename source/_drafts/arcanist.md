---
title: arcanist cheatsheet
tags:
---

- create tasks T{NNNN} asign them
- create a branch with name like "T{NNNN}-boo-hoo"
- `git checkout -b T1234-boo-foo`
- commit changes on that branch until it gets ready to be reviewed
- `git commit -am 'first'`
- `git commit -am 'now it works'`
- check if it's lint free (NOTE: it runs lint against only modified files)
- `arc lint`
- push a review request to the server. This will create a diff with id D{NNNN}
- `arc diff []`
- As a reviewer, you can apply the changeset on your local by using `arc patch D{NNNN}`
- `arc patch D5678`
- if reviewers post a comment and you need to update the changeset, commit more changes on that branch
- and push updated changeset to the server
- `arc diff --update 1234`
- To check status of review requests which you have posted, run `arc list` which will give you a list of Status, Diff ID and title
- `arc list`
- Once review request got accepted, merge changes to master. "arc land" command will take care of merging/rebasing branch and deleting your working branch... And pushing changes to origin/master.
- `arc land [--onto <branch name>]`
- viola!

https://secure.phabricator.com/book/phabricator/article/arcanist_diff/