----
title: Apache And nginx
date: 2017-06-21 14:45:01
tags: webserver
categories: web&linux
---
# 学习笔记
主流的web服务器软件，一个是Apache HTTP Server，一个是Nginx。Nginx是款轻量级的web服务器和反向代理服务器软件，处理静态请求有极高的性能，国内的淘宝，百度，微博都在使用。
使用系统为CentOS7，不同系统可能有差易
# systemctl 工具

centOS7中，systemctl是个新的工具，据说是集合了service和chkconfig的功能。如果你的网站，在别的电脑打不开，可能是防火墙打开了。如果不知道如何只开启80端口，在自己实验的时候可以把防火墙全部关掉。
查看防火墙状态
`$ systemctl status firewalld  #查看防火墙状态`
`$ systemctl stop firewalld  #关闭防火墙`
`$ systemctl start firewalld #启动防火墙`
`$ systemctl restart firewalld #重启防火墙`
`$ systemctl enable firewalld #开机启动防火墙`
`$ systemctl disable firewalld #禁止开机启动防火墙`

上面的命令将firewalld替换为其他服务，对绝大多数的服务有相同的效果，比如（`$ systemctl status httpd`）查看httpd服务的状态。
# 压缩与解压
## zip
`$ unzip filename.zip #解压文件到当前目录`

`$ zip 1.zip 2.txt  #将名为2.txt的文件压缩为1.zip`

`$ zip -r 1.zip uuu #将名为uuu的文件夹压缩为1.zip，文件夹压缩加参数-r`
## tar
`$ tar xvf filename.tar #解压文件到当前目录`

`$ tar cvf 目标文件 源文件 #压缩命令`
## tar.gz
`$ tar zxvf name.tar.gz  #解压文件到当前目录`

`$ tar zcvf name.tar.gz 2.txt  #压缩命令，将2.txt压缩到name.tar.gz `
# Apache
## 安装

在Linux中Apache是个叫做httpd的软件，安装之前可以用命令rpm -qa|grep httpd查看是否安装了软件。如未安装，可以用yum install命令安装

       $ yum install httpd

系统会自动从软件仓库安装。

安装完成后存放html文件的目录为*`/var/www/html/`*下，你的网站页面文件就放在这个目录下。

配置文件的目录为*`/etc/httpd/conf/`*下，有一个*`httpd.conf`*的文件。可以配置详细的功能，有兴趣的同学可以深入学习。

httpd默认开启80端口，打开浏览器输入localhost就能看到Apache的默认页面了。如果你的电脑在局域网中，在其他电脑上打开浏览器，输入你的电脑的IP地址，也可以访问到你的网页。你的电脑，就相当于一个WEB服务器了。




# nginx
## 安装
在nginx的官网下载nginx的linux版本包。

[http://nginx.org/en/download.html](http://nginx.org/en/download.html "http://nginx.org/en/download.html")

解压文件

    $ tar zxvf nginx-1.13.1.tar.gz #我下载的为此版本

----------
    $ cd nginx-1.13.1

----------
	$ ./configure

----------
	$ make && make install

nginx的执行目录在*`/usr/local/nginx/sbin/`*

静态文件的存放路径在*`/usr/local/nginx/html`*进入到此目录可一看到一个index.html（默认主页）文件和50x.html文件（错误的时候反会的402页面）。

### 启动&软连接&基本命令
#### 软链接
由于`nginx`命令没有加到系统路径，所以启动的时候要输入
`$ /usr/local/nginx/sbin/nginx`这么一大串完整路径，为了方便，
可以给nginx加一个软连接到bin目录下，就是一个程序的快捷方式，这样当你在命令行ngnix的时候就不会提示`no command`了。

    ln -s /usr/local/nginx/sbin/nginx /bin/nginx

(ln -s 源文件 目标文件）这样就在bin目录下添加了一个软链接，到`bin`目录下用`ll`命令查看`nginx`是这样的，如图
![https://github.com/hellowanghe/blogimg/blob/master/img/nginxln.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/nginxln.PNG?raw=true)可以发现，nginx指向nginx所在的目录。
#### 启动
当在命令行输入nginx的时候，系统会到bin下找nginx的命令，nginx就会到它指向的目录寻找。这时就能启动nginx了，在浏览器输入localhost，就可以看到nginx的默认页面。或者在局域网内的其他电脑上输入，nginx服务所在电脑的IP也可以看到（80端口开启的情况下）。
可以输入


	$ nginx -h #查看帮助

nignx的命令不多，常用的就nginx -s了，在帮助里可以看到他的意思。-s是向ngnix传递信息的意思。
`$ nginx -s stop #直接退出，不做保存`

`$ nginx -s quit #温和的退出`

`$ nginx -s reopen #重新打开`

`$ nginx -s reload #重新加载配置文件，如果配置文件有修改的话`

## 遇到的问题
在./configure的时候回报找不到PCRE library，gzip需要zlib库的错误，或者找不到g++的错误。所以在这之前需要把这些库安装好。
先安装编译工具。

    $ yum install gcc

---------

    $ yum install gcc-c++

### PCRE:
rewrite所要使用的第三方模块
http://www.pcre.org/

	$ wget ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.13.zip

### openssl：
https协议所要使用的模块
http://www.openssl.org/source/下载源码包安装。

    $ wget http://www.openssl.org/source/openssl-1.0.0e.tar.gz
或者

    yum install -y openssl
### zlib
缺少zlib的情况，

    yum install -y zlib-devel

### uploadprogress
如果你用到uploadprogress模块
http://wiki.nginx.org/HttpUploadProgressModule

	wget https://github.com/masterzen/nginx-upload-progress-module/downloads
 

将所需模块安装完成后，照如下步骤安装即可。

`$ ./configure`

`$ make`

`$ make install`
### libpcre.so.0
在安装完pcre的依赖包之后，启动nginx时，又爆出了错误，提示没有libpcre.so.0文件。我进到lib64目录发现，有一个libpcre.so.1的软链接到了libpcre.so.1.2.0文件。于是我加了一个libpcre.so.0的软链接到libpcre.so.1.2.0.再次启动,启动成功。

    $ ln -s /lib64/libpcre.so.1.2.0  /lib64/libpcre.so.0

# Windows下的Nginx
windows的下的Nginx比较简单，到nginx的官网下载，nginx的windows压缩包，解压到一个目录下，最好是英文的目录。
打开cmd命令行
进入到nginx的目录，
敲入
`nginx`，

或者

`start nginx`
然后，在浏览器打开localhost就可以看到nginx的页面了。关掉dos窗口，nginx会在后台运行。
若要停止，命令行进入，nginx所在目录，运行

`nginx -s stop`

