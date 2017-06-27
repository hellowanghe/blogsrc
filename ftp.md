---
title: 一个简单的FTP服务器
date: 2017-06-23 16:27:58
tags: ftp
categories: linux
---
# FTP 服务器简单搭建
（centos7)
如果你的电脑是没有安装ftp。执行命令安装。

    yum install vsftpd

-------
    yum install ftp

在目录/var/ftp/pub下存放共享的文件。

开启ftp服务

    $ systemctl start vsftpd

查看ftp服务状态

    $ systemctl status vsftpd

状态为active表示成功开启
![https://github.com/hellowanghe/blogimg/blob/master/img/ftpstatus.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/ftpstatus.PNG?raw=true)


文件目录在`/var/ftp/`下有个`pub`文件夹，要分享的文件可以放在这里。
/etc/vsftpd/下vsftpd.conf是配置文件。
![https://github.com/hellowanghe/blogimg/blob/master/img/ftpconf.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/ftpconf.PNG?raw=true)

ftp://localhost/

ftp://10.238.49.54/

