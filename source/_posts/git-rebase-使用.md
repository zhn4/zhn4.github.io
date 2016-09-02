---
title: git rebase 使用
date: 2016-07-26 15:55:39
tags:
---
### git rebase 使用
使用rebase合并，比merge合并好处在于减少多余的合并记录

参考：https://backlogtool.com/git-guide/tw/stepup/stepup2_8.html

```bash
#master主分支，dev次分支
#master分支保持最新版本
git pull origin master

#切换到到dev分支
git checkout dev

#基于master分支rebase
git rebase master

#添加修改文件
git add '文件名'

#切换到master分支，并合并dev分支
git checkout master
git merge dev
```
