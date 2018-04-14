git简单介绍
======================
[git是什么](#1)
--------
> ***git***是一个`开源`的`分布式`版本控制系统
[git与svn简单对比](#2)
-------
  | 区别 | git | svn |
  | :- | :-: | :-: |
  | 结构 | 分布式 | 集中式 |
  | 单一节点是否存有完整版本库信息 | 是 | 否 |
  | 存储方式 | 元数据 | 文件 |
  | 分支支持完善程度 | 强大的分支控制支持 | 有，但概念模糊 |
> 分布式与集中式最大也是最明显的区别是否必须具有中央服务器，
>> 平时使用git是有中央服务器的，但其并不是必选项。完全可以将该中央服务器看作一台在任何地点任何时间都能连接的另一台节点，该节点的作用更多的是用来作为方便各节点之间方便的通信修改
[git结构介绍](#3)
-----------
![][git]

* **工作区**:就是你在电脑里能看到的目录。
* **暂存区**:英文叫stage, 或index。一般存放在 ".git目录下" 下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。
* **版本库**:工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。

[使用方式-常用命令](#4)
------------
#### 基本操作
* 初始化项目
```shell
git init
```
* 查看当前工作区内的修改状况
```shell
git status
```
* 添加修改到暂存区
```shell
git add -A #添加所有修改到暂存区
git add <file> #添加指定文件到暂存区
```
* 从暂存区撤销文件修改
```shell
git reset HEAD <file> #将暂存区指定文件的修改撤销回工作区，不指定文件则为所有
```
* 将文件恢复为版本库中最新的版本
```shell
git checkout -- <file>
```
* commit操作
```shell
git commit -m "版本信息" #将暂存区修改信息作为一个新版本添加到仓库内
```
* 以时间线查看当前分支的所有log
```shell
git log
```
* 版本回退
```shell
git reset --hard HEAD^ #版本库回退到上一个版本
```
* 指定切换到的版本
```shell
git reset --hard <commit> #commit id可以通过git log命令查看，该操作会将HEAD指针指向指定的commit id版本，后续的commit信息将会丢失
git revert <commit> #将指定版本到现在的所有操作做逆向并作为一次新的commit操作
```
* 查看执行命令历史
```shell
git reflog
```
* 从版本控制中删除文件
```shell
git rm <file>
```
###### tag操作
* 添加tag
```shell
git tag -a <version> <commit> #为指定commit添加一个tag，当没有指定commit时默认为当前commit添加tag
```
* 删除tag
```shell
git tag -d <version>
```
* 列出所有tag
```shell
git tag
```
* 查看tag详情
```shell
git show <version>
```
* stash暂存
```shell
git stash #将当前分支工作区所有修改stash起来
```
* 获取stash列表
```shell
git stash list
```
* 恢复stash
```shell
git stash apply #将stash内容恢复到当前工作区后不删除之前的stash
git stash pop #将stash内容恢复到当前工作区并删除该stash
```
#### 分支操作
* 查看现有分支
```shell
git branch #查看本地所有分支
git branch -a #查看包括远程分支在内的项目所有分支
```
* 切换分支
```shell
git checkout <branchname>
```
* 新建分支
```shell
git branch <branchname> #新建一个branch
git checkout -b <branchname> #新建一个branch并切换过去
```
* 删除分支
```shell
git branch -d <branchname>
```
* 合并分支
```shell
git merge <branchname> #将指定分支merge到当前分支
```
###### 远程仓库操作
* 设置本地分支与远程分支的关联
```shell
git branch --set-upstream <branch> <origin/branch>
```
* 添加远程仓库
```shell
git remote add origin <url> #为当前项目添加名为origin的远程仓库地址
git push -u origin master #把本地库的所有内容推送到远程库上
```

[配置git排除文件方式](#5)
----------
> **.gitignore**文件中列出需要排除的文件或目录
> 各语言的示例可以参考[github/gitignore](https://github.com/github/gitignore)

[git]: ./git.jpg
