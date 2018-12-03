---
layout: post
title:  "git命令使用"
categories: git
tags:  Java git
author: jida
---

* content
{:toc}


## 前言

之前公司一直用的svn，但计划明年从svn迁移到git，顺便自己在学习Java从零到企业级项目实战开发，正好通过git方式将代码上传到码云，那么我也就将其中的流程给记录下来。
## idea上传到码云步骤
1. 分别创建 README.md 和 .ignore文件

    在命令行输入

    type nul> README.md

    type nul> .ignore
2. 在.ignore中配置需要忽略的文件

    *.class

    #package file

    *.war *.ear

    #maven ignore

    target/

    #idea

    .idea/  /idea/  *.ipr  *.iml  *.iws

    #temp file

    *.log *.cache *.diff *.patch *.tmp

    #system ignore

    .DS_Store Thumbs.db
3. 创建本地仓库 git init
4. 查看git哪些文件发生变化 git status
5. 添加所有发生变更的文件 git add .
6. 提交到本地

    git commit -am "first commit init project"

    (-am 后面添加注释)

    这块还遇到过不能提交的问题

    [解决方法](https://blog.csdn.net/senior_lee/article/details/54667679)
7. 连接到码云

    git remote add origin git@gitee.com:ncut_LJD/mmall_learning.git
8. 查看分支 git branch
9. 将本地代码提交到码云

    git push -u origin master

    遇到问题 需要配置ssh

    [解决办法](https://blog.csdn.net/MAMAIMAI/article/details/79820704)
10. 从码云同步代码 git pull
11. 强制提交代码 git push -u -f origin master(-f 强制)
12. 查看远程分支 git branch -r
13. 创建分支

    git checkout -b v1.0 origin/master (在origin/master基础上生成v1.0分支)
14. 分支上传 git push origin HEAD -u(推送到当前分支)
  ---
码云地址：https://gitee.com/ncut_LJD

## git的基本命令
- 获取分支上的代码

  git clone -b 分支名称 git地址
