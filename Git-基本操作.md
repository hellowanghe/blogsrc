---
title: Git 基本操作
date: 2017-06-15 08:17:49
tags: Git
categories: Tools
---
# Git是分布式的版本控制工具
这是git的官网，可以下载最新版本的git使用。我只装了windows版本的git。想详细了解的同学可以去廖雪峰的Git教程看看。
[https://git-scm.com/](https://git-scm.com/ "Git 官网")

[http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000 "廖雪峰Git")


安装成功git，在cmd命令行输入 `git --version` 就可以看到git的版本号了（注意两个是`--`）![https://github.com/hellowanghe/blogimg/blob/master/img/git1.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/git1.PNG?raw=true)

安装完成后，首先需要配置一下，用户名和邮箱，每次的`commit`都会记录下是哪个用户推送的。

    $ git config --global user.name "Your Name"

---
    $ git config --global user.email "email@example.com"

## 基本命令 
### 1.初始化

    git init test 

 初始化一个名为test的仓库。test里有一个.git的文件夹（默认为隐藏），这个是用来管理仓库的。一个本地仓库就建好了。（版本库又名仓库，英文名repository，大概就是一个目录的样子）

或者新建文件夹test，`cd test`之后，输入`git init`，和上步有同样的效果
### 2.查看仓库状态

     git status
  
用于查看仓库状态，一旦发生改变就会有提示。我们在test文件夹下新建一个文本文件名为one.txt,并写入this is test，保存。运行此命令，如图所示。

![https://github.com/hellowanghe/blogimg/blob/master/img/git2.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/git2.PNG?raw=true)
### 3.对比差异

    git diff one.txt

可以查看你所修改的东西，在提交之前查看，一旦你add之后，这个命令就不起作用了。
### 4.添加到暂存区

    git add filesname 

将文件添加到暂存区
### 5.提交到分支

    git commit -m "添加了一些东西，删除了一些东西"

提交到分支，-m后面是你提交的说明。可以填写你所修改的东西。
### 6.查看历史提交记录

    git log

会显示你所提交的日志，及版本号，版本号是用sh1计算出的一串字符，为了避免重复。在后面加上参数--pretty=oneline会让日志成行显示，
![https://github.com/hellowanghe/blogimg/blob/master/img/gitlog.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/gitlog.PNG?raw=true)
![https://github.com/hellowanghe/blogimg/blob/master/img/githead.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/githead.PNG?raw=true)

### 7.版本回退

    git reset --hard "版本号"

回退到制定的版本号。`git log` 显示出你的所有提交记录，想要回退到那个版本，就输入版本号，一般输个前5位就行，如果没有相同的话。
如上图

    git reset --hard HEAD

可以查看当前的版本号
![https://github.com/hellowanghe/blogimg/blob/master/img/gitreset.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/gitreset.PNG?raw=true)
### 8.后悔药

    git reflog 

可以查看你所有的操作记录。也可以用reset命令，回退到你想要回退的版本。

![https://github.com/hellowanghe/blogimg/blob/master/img/git.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/git.PNG?raw=true)
### 9.添加远程仓库
在你的仓库文件中运行

    git remote add origin git@github.com:michaelliao/fortest.git

把仓库名改成自己的就行了。
### 10.推送到远程仓库

在仓库运行

    git push -u origin master

-u表示，将本地仓库同步到远程仓库，并关联到远程仓库。
### 11.将远程仓库同步到本地
git pull会同步远程分支到本地。

    git pull
### 12.创建分支
新建一个dev分支

    git branch dev
切换到dev分支

    git checkout dev
查看当前分支 

    git branch
删除分支

    git branch -d dev

查看分支合并图

    git log --graph
### 13.合并分支
在切换回master分之后，运行命令，会将dev分支合并到master分支，也就是当前分支

    git merge dev

# Git ssh 配置

打开Gitbash，创建SSH Key ，可以一路回车

    ssh-keygen -t rsa -C "email"

会在 `C:\Users\dell`目录下生产.ssh文件夹，文件夹下有id_rsa和id_rsa.pub，id_rsa.pub就是公钥，复制粘贴到，github的相应位置就可以远程推送了。


