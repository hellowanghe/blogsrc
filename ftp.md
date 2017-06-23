---
title: ftp
date: 2017-06-23 16:27:58
tags: ftp
categories: linux
---
# FTP 服务器简单搭建
（centos7)
如果你的电脑是没有安装ftp。执行命令安装。

    yum install vsftpd

    yum install ftp

在目录/var/ftp/pub下存放共享的文件。

开启ftp服务

    systemctl start vsftpd

查看ftp服务状态

systemctl status vsftpd

状态为

