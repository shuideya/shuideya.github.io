---
layout:     post
title:      Git&Github
subtitle:   用git在GitHub的海洋遨游
date:       2018-03-24
author:     Yfan
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - 分享
    - Git
    - 技术
    
---

前言
===
>这里是简单的共同学习分享时刻，主要是以下几个方面的探讨：**Git的基础**、**Github使用**、**迅速查找问题**

1.iterm
在这之前先说工具Sourcetree 和iTerm。
主要说下iterm：
com+d，com+shitf+d
control + a: 到行首
control + e: 行末
命令回放: Cmd+Alt+B
清屏：cmd+l
这里有一些方便写和查看命令的主题：<https://github.com/robbyrussell/oh-my-zsh>

2.readme要写的、Tree这个树形库 可以了解一下

# Git的基础


##1.平台：国内，国外
 
 		github
		gitLab
		bitbucket
		coding 国内的
		oschina 国内的
		

##2.git与svn对比
 	
##3.常用命令

```
1.git add .
2.git commit －m""

  1和2 类似于 git commit -am

3.git pull 拉取
4.git push 提交
5.git status 查状态
6.git branch dev 新建分支
7.git checkout dev 切换分支
8.git reset --hard 版本号   本地恢复到某个版本,注意和soft的区别，这里的内容还很多,大家可以细细研究
  git reset --soft（简单说：重置后，版本之后的都在暂存区，hard是后面的销毁了）
9.git rev-parse HEAD 或 git rev-parse --short HEAD  查询当前分支版本号
10.分支合并
git checkout master
git merge featureA
或git rebase featureA 重新排序
11.git checkout --orphan gh-pages 创建一个无历史的分支

```
		
eg.打一个tag：
	
```
➜  Wangshop git:(master) git tag 2.0.1
➜  Wangshop git:(master) git tag
2.0.1
➜  Wangshop git:(master) git push --tag
Total 0 (delta 0), reused 0 (delta 0)
To git@git.yunpro.cn:wangdian/app-ui-android.git
 * [new tag]         2.0.1 -> 2.0.1
➜  Wangshop git:(master) git checkout dev
Switched to branch 'dev'
➜  Wangshop git:(dev)
```
```
为什么打tag，有的同事说，打个release 版本分支不也一样吗
git show v3.8.703  (这里标签的版本信息就更全一些)
git checkout v3.8.703 (切到tag)
git tag -d <tagname> （删除tag）
git push origin :<tagname>
```
	
	
###别名alias设置

	git config --global alias.co checkout  # 别名
	git config --global alias.ci commit
	git config --global alias.st status
	git config --global alias.br branch
  
当然以上别名不是固定的，你完全可以根据自己的习惯去定制，除此之外还可以设置组合，比如：

	git config --global alias.psm 'push origin master'
	git config --global alias.plm 'pull origin master'

之后经常用到的 git push origin master 和 git pull origin master 直接就用 git psm 和 git plm 代替了。

一个很吊的命令：

	git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative 
	
	
###git stash

>当前分支暂存。这些就不写了

###分支


![](http://images2015.cnblogs.com/blog/747889/201610/747889-20161026183005062-1944621251.jpg)


###文档终极版
	
<http://wiki.yunpro.cn/index.php?title=Git_%E7%9A%84%E7%94%A8%E6%B3%95>

##4.git工具
 *SourceTree
 *git客户端


##5.其他命令：
svn 迁移到 git
    git svn clone svn://center.11bbt.com/bbtwork/project/bbt2.0/02.bbtClient/02.bbtstore/02_code/02_ios/trunk/BBTB/BBTBusiness –no-metadata –trunk=trunk BBTBusine

git push.default设置：
git config --global push.default simple

//忽略.xcuserstate 文件
git rm --cached ProjectFolder.xcodeproj/project.xcworkspace/xcuserdata/myUserName.xcuserdatad/UserInterfaceState.xcuserstate
git commit -m "Removed file that shouldn't be tracked"

##6.git的一些其他设置
1.git push origin master 设置成 git push 等

##7.gitignore 使用

#Github的使用

* 流程
* readme了解一下，树状图了解一下
* 做静态网站 <https://pages.github.com/>
* 短链生成 <http://git.io/>
* 活跃项目 <https://github.com/explore>
* 通过关键字查找项目 awesome
* 发现好的开源项目explore ，市场上的好的工具market
* 等等


#迅速查找问题

<http://yfan.net/SomeShare/>


