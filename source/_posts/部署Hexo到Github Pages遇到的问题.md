---
title: 部署Hexo到Github Pages遇到的问题
date: 2020-05-05 10:41:44
tags:
---

[将 Hexo 部署到 GitHub Pages](https://hexo.io/zh-cn/docs/github-pages)

## 分支

由于Github目前只支持将页面部署到master分支，我们需要把原来的master分支改名，然后利用TravisCI把pages部署到master分支上。

首先，修改本地分支名称

`git branch -m master source`

编写或修改.travis.yml

```yaml
sudo: false
language: node_js
node_js:
  - 10 # use nodejs v10 LTS
cache: npm
branches:
  only:
    - source # build source branch only
script:
  - hexo generate # generate static files
deploy:
  provider: pages
  skip-cleanup: true
  github-token: $GH_TOKEN
  keep-history: true
  on:
    branch: source
  local-dir: public
  target_branch: master
```

[GitHub Pages Deployment](https://docs.travis-ci.com/user/deployment/pages/)

然后推送到远程仓库

`git push -u origin source`

如果你已经配置好了TravisCI，接下来它就会帮你完成部署了。



如果你之前错误的部署过，删除远程的gh-pages分支

`git push --delete origin gh-pages`

## The tag fancybox on line 77 in themes/landscape/README.md is not a recognized Liquid tag

似乎是因为Github把source分支当成了页面内容？？在TravisCI上Restart build可以解决问题。

