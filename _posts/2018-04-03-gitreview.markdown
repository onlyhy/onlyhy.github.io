---
layout: post
title:  "Git基础知识复习"
date:   2018-04-03 10:00:00 +00:00
categories: Git
author: onlyhy
---

*复习廖雪峰老师的[Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)所记的笔记*

#### Git是分布式版本控制系统

1. `git init` 将当前目录变成Git可以管理的仓库，会多一个用来跟踪管理版本库的.git目录（默认隐藏，ls -ah可看）
2. `git add` 将文件添加到仓库
3. `git commit` 将文件提交到仓库 
4. commit可一次提交很多文件，即可多次add不同文件然后一起commit
5. `git status` 掌握仓库动态
6. `git diff` 查看difference，查看修改内容，也可比较两个版本内容之间的不同
7. 提交修改与提交新文件是相同的两个步骤
8. `git log` 查看历史记录（从最近到最远显示）
9. `git reflog` 记录每一次命令，找到相对应的commit id 就能去相应的版本
10. `git reset`回退版本   `HEAD` 表示当前版本，`HEAD^`表示上一个版本，`HEAD^^`上上一个版本，依次类推往上100个则`HEAD~100`  也可通过版本号返回
11. `git add`其实就是把要commit的内容放到暂存区，每次修改内容，如果不add到暂存区，就不会加入到commit中
12. `git checkout -- file` 可以丢弃工作区的修改，让文件回到最近一次`git commit` 或 `git add`状态
13. 改乱内容且添加到暂存区后，想丢弃修改则`git reset HAED file` 然后 `git checkout -- file`
14. 改错东西且已提交到版本库则`git reset 版本号`，前提是未推送到远程
15. `rm`删除文件后， 若也要删版本库中文件则 `git rm` 文件 且 `git commit`， 而若是rm 文件后发现删错文件可`git checkout -- 文件`， 用版本库里的版本替换工作区版本（rm了之后并没有commit）。若版本库中也不包含这个文件了，则执行版本回退 `git reset --head HEAD^` 或`commit id`

#### 远程仓库

创建SSH Key ：
 
    `$ ssh-keygen -t rsa -C "youremail@example.com" `

在用户主目录的.ssh目录里得到<strong>id_rsa</strong>和<strong>id-rsa.pub</strong>文件 然后添加key到GitHub的settings里面去
17. 先有本地库后，关联一个远程库，关联后，使用`git push -u origin master` 第一次推送master分支的所有内容，以后只要本地做了修改，就可通过 `$git push origin master`推送至GitHub
18. 从0开始，先创远程库，再克隆仓库的地址
19. Git支持多种协议，包括https，ssh 通过ssh支持的原生git协议速度最快

#### 分支管理

20. 
    
    * 查看分支：`git branch`  
    * 创建分支：` git branch <name>`
    * 切换分支：`git checkout <name> `
    * 创建+切换分支：`git checkout -b <name> `
    * 合并某分支到当前分支：`git merge <name>`
    * 删除分支：`git branch -d <name>`

21. Git无法自动合并分支时，要首先解决冲突再合并
22. `git log --graph` 可看到分支合并图 
23. 合并分支时，加上`--no-ff`参数可用普通模式合并，合并后的历史有分支，能看出曾经做过分支
24. 修复BUG，创建新的BUG分支修复，再合并后删除
25. 手头工作未完成时可`git stash`先存储起来，`git stash list`可看。有两种办法恢复：
    
    * 一是`git stash apply`，恢复后stash内容不删除，要用`git stash drop`删除。 
    * 二是`git stash pop` ，恢复的同时stash内容也删了

26. 开发一个新功能，最后新建一个分支。
27. 若要丢弃一个未被合并过的分支，用`git branch -D <name>`强行删除
28. 建立本地分支和远程分支的关联：
    
    `git branch --set-upstream branch-name origin/branch-name`

29. 本地创建和远程分支对应的分支：
    
    `git checkout -b branch-name origin/branch-name`

30. 多人协作时，从本地推送分支：
   
    `git push origin branch-name`

推送失败则git pull抓取远程的新提交，若有冲突要处理冲突

#### 标签管理
31. 标签tag名字易记，跟某个commit绑在一起
32. `git tag <name>` 可打一个新标签，默认HEAD,也可指定commit id
33. `git tag `查看所有标签，`git show <tagname>`查看标签信息
34. `-a `指定标签名 ， `-m`指定说明文字， `-s`用PGP签名标签
35. `git tag -d <tagname>`删除本地标签
36. 推送标签 `git push origin <tagname>`，一次性推送全部`git push origin --tags`
37. 删除远程标签：先从本地删除 `git tag -d <tagname>`再从远程删除：`git push origin：refs/tags/<tagname>`