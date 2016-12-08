<!--
author: rickeryu
date: 2016-11-08
title: 在项目中git的常规操作及冲突解决方式
tags: Git,项目,冲突
category: 新手教程
status: publish
summary: 
在项目中git的常规操作及冲突解决方式.
-->

##更新时有可能存在冲突，解决冲突的办法

1. 如果自己确认没有修改过文件内容，那有可能是文件权限造成的，执行下面语句
```
git config core.fileMode false
git pull
```
2. 如果确认内容修改过，但不想要的
```
git log //找到上一个版本号
git reset 上一版本号 文件名
git checkout -- 文件名
```
3. 如果文件很多，大多数不想要了，**先备份想保留的文件**
```
git reset --hard
#还原已经备份的文件
```

####乐易考线上环境

线上的程序一般不会动，存在文件权限冲突的情况比较多，如果存在冲突，先解决权限，在更新
```
git config core.fileMode false
git pull
```

##常用操作

> 我们这里假如自己的项目目录为test目录。   

进入目录 	
```
cd test
```   
初始化git	
```
git init
```	
创建开发分支dev并切换到dev分支 	
```
git checkout -b dev
```	
理解git的文件提交流程 	
```
本地目录->提交到暂存区->提交到git本地仓库->推送到远程仓库
```		
添加文件到暂存区	
```
git add p.php //添加文件到暂存区   
git status //查看git状态，正常显示如下   
```		
把文件提交到本地git仓库	
```
git commit -m "添加p.php文件"   		
git status //查看git状态
```
分支切换，我们先创建一下“test”分支	
```
git checkout -b test	
```
我们新创建一个test.php文件，同样把这个文件提交到test分支的本地仓库		
```
git add test.php
git commit -m "add test.php"
```
然后我们切换回“dev”的分支，惊奇的发现，为什么刚才创建的"test.php"没有了？
```
git checkout dev
ls //查看目录文件
```
这里我们在理一下提交文件的流程并添加上分支名称
```
本地目录(test)->提交到暂存区(test)->提交到git本地仓库(test)
```
我们发现，我们刚才只是把“test.php”提交到“test”的分支里面，并没有提交到“dev”分支啊,既然我们创建的“test.php”只是提交到“test”分支，那现在我们就把他合并到“dev”分支	
```
git merge test
```
惊奇的发现，“test.php”文件合并过来了		

突然一天，我发现修改的东西错了，想还原到上一个版本
```
git log //查看历史日志,找到要还原的commit版本
git reset --hard d69774288bc3dc38e101fbc2bd17e2a491390a01
```
这时我们是把整个项目回滚到上一个版本，如果我们只是想把某一个文件回滚到上一版本
```
git reset d69774288bc3dc38e101fbc2bd17e2a491390a01 test.php
git checkout -- test.php
```
首先我们要在github或开源中国上创建自己的项目,创建项目完成后获取远程仓库地址
```
git remote add origin https://git.oschina.net/zyyu/test.git
git push -u origin dev
```

从远程仓库更新代码
```
git pull
```

####长久存储密码
**如果你已经在项目目录，使用下面命令**
```
git config credential.helper store
```

全局长期存储密码：
```
git config --global credential.helper store
```

####临时存储密码
**如果你已经在项目目录，使用下面命令**
```
git config credential.helper cache
```

如果想自己设置时间，可以这样做：
```
git config credential.helper 'cache --timeout=3600'
```
这样就设置一个小时之后失效


全局设置记住密码（默认15分钟）：
```
git config --global credential.helper cache
```











