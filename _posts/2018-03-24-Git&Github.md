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
>这里是简单的共同学习分享时刻，主要是提高效率，对以下几个方面的探讨：**工具使用**、**Git的基础**、**Github使用**、**迅速查找问题**


# 工具使用

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
 tree 还可以列出文件或目录大小，排序，权限等等
3.浏览器使用：搜索，收藏夹，搜索引擎语法啊...等等

4.一般繁琐重复的工作都有工具，来提高效率。GitHub市场里也有工具这一块，我们的trello，fir 也都是工具。
对iOS：也有特别多。比如json数据直接生成模型 工具，有的几年开发经验的开发者也不知道使用。

5.电脑快捷键：多屏幕，触发角，手势，快捷键   ==>苹果电脑适合开发。🙂

# Git的基础


##1.平台：国内，国外
 
 		github
		gitLab
		bitbucket
		coding 国内的
		oschina 国内的
		

##2.git与svn对比
 	
##3.常用命令

![](https://images2015.cnblogs.com/blog/747889/201610/747889-20161026145220500-1320304386.jpg)
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
git rebase 里面的东西也很多，大家自己细细研究
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

>当前分支暂存。保存一下，干其他事情
git stash == git stash save ""
git stash list
git stash pop [--index] [<stash>] (eg. git stash pop stash@{1})
git stash clear

###分支


![](http://images2015.cnblogs.com/blog/747889/201610/747889-20161026183005062-1944621251.jpg)

* Production 分支  
也就是我们经常使用的Master分支，这个分支最近发布到生产环境的代码，最近发布的Release， 这个分支只能从其他分支合并，不能在这个分支直接修改
* Develop 分支  
这个分支是我们是我们的主开发分支，包含所有要发布到下一个Release的代码，这个主要合并与其他分支，比如Feature分支
* Feature 分支  
这个分支主要是用来开发一个新的功能，一旦开发完成，我们合并回Develop分支进入下一个Release
* Release分支  
当你需要一个发布一个新Release的时候，我们基于Develop分支创建一个Release分支，完成Release后，我们合并到Master和Develop分支,release 发布分支打完，新的dev分支改动不要合并到release。
* Hotfix分支  
当我们在Production发现新的Bug时候，我们需要创建一个Hotfix, 完成Hotfix后，我们合并回Master和Develop分支，所以Hotfix的改动会进入下一个Release

###文档终极版
	
<http://wiki.yunpro.cn/index.php?title=Git_%E7%9A%84%E7%94%A8%E6%B3%95>

##4.git工具
 *SourceTree
 *git客户端


##5.其他命令：
* svn 迁移到 git
    git svn clone svn://center.11bbt.com/bbtwork/project/bbt2.0/02.bbtClient/02.bbtstore/02_code/02_ios/trunk/BBTB/BBTBusiness –no-metadata –trunk=trunk BBTBusine

* git push --set-upstream origin master 以后直接 git push 就可以
* git push.default设置：（设置push.default为upstream ,和simple类似的）
git config --global push.default simple
git config --global push.default upstream（git config push.default upstream）


#取消设置
git config --unset push.default

//忽略.xcuserstate 文件
git rm --cached ProjectFolder.xcodeproj/project.xcworkspace/xcuserdata/myUserName.xcuserdatad/UserInterfaceState.xcuserstate
git commit -m "Removed file that shouldn't be tracked"


##6.gitignore 使用

#Github的使用

* 流程
* 做静态网站 <https://pages.github.com/>
* 短链生成 <http://git.io/>
* 活跃项目 <https://github.com/explore>
* 通过关键字查找项目 awesome Android iOS Learning(eg.Machine learning)
* 发现好的开源项目explore ，市场上的好的工具market
* github一些排行<https://github-ranking.com/>
* 国内的一些大牛 <http://outofmemory.cn/github/> （找到他们的微博什么的，可以问一些问题，简单问题就不要烦人家了）
* github给的一些搜索技巧 <https://help.github.com/categories/search/>
	(stars:10..20;  forks:>100)
	
* github排在第三的一个项目，里面是一些书。 <https://github.com/vhf/free-programming-books>
* 国内一线互联网公司内部面试题库 <https://github.com/GeniusVJR/LearningNotes>
* github秘籍 <https://github.com/tiimgreen/github-cheat-sheet/>
* git 秘籍 <http://wiki.yunpro.cn/index.php?title=Git_%E7%9A%84%E7%94%A8%E6%B3%95>


#迅速查找问题

<http://yfan.net/SomeShare/>


