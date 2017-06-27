---
title: 一个简单的FTP服务器
date: 2017-06-23 16:27:58
tags: ftp
categories: linux
---
# FTP 服务器简单搭建
（centos7)
## 安装
如果你的电脑是没有安装ftp。执行命令安装。

    yum install vsftpd

-------
    yum install ftp

在目录/var/ftp/pub下存放共享的文件。

## 开启ftp服务

    $ systemctl start vsftpd

## 查看ftp服务状态

    $ systemctl status vsftpd

状态为active表示成功开启
![https://github.com/hellowanghe/blogimg/blob/master/img/ftpstatus.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/ftpstatus.PNG?raw=true)


文件目录在`/var/ftp/`下有个`pub`文件夹，要分享的文件可以放在这里。
`/etc/vsftpd/`下`vsftpd.conf`是配置文件。
![https://github.com/hellowanghe/blogimg/blob/master/img/ftpconf.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/ftpconf.PNG?raw=true)

如果修改成NO，在登录的时候会需要服务器密码。目录也不再是默认的目录，而是你所登录用户的目录。
在浏览器输入地址

    ftp://localhost/

或者

	ftp://10.238.49.54/

就可以看到ftp目录了。

2017/6/27 21:12:16 

