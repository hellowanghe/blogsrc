---
title: Apache And nginx
date: 2017-06-21 14:45:01
tags: webserver
categories: web&linux
---
主流的web服务器软件，一个是Apache HTTP Server，一个是Nginx。Nginx是款轻量级的web服务器和反向代理服务器软件，处理静态请求有极高的性能，国内的淘宝，百度，微博都在使用。
使用系统为CentOS7，不同系统可能有差易
# Apache
## 安装

在Linux中Apache是个叫做httpd的软件，安装之前可以用命令rpm -qa|grep httpd查看是否安装了软件。如未安装，可以用yum install命令安装

       $ yum install httpd

系统会自动从软件仓库安装。

安装完成后存放html文件的目录为*`/var/www/html/`*下，你的网站页面文件就放在这个目录下。

配置文件的目录为*`/etc/httpd/conf/`*下，有一个*`httpd.conf`*的文件。可以配置详细的功能，有兴趣的同学可以深入学习。

httpd默认开启80端口，打开浏览器输入localhost就能看到Apache的默认页面了。如果你的电脑在局域网中，在其他电脑上打开浏览器，输入你的电脑的IP地址，也可以访问到你的网页。你的电脑，就相当于一个WEB服务器了。

## systemctl 工具

centOS7中，systemctl是个新的工具，据说是集合了service和chkconfig的功能。如果你的网站，在别的电脑打不开，可能是防火墙打开了。如果不知道如何只开启80端口，在自己实验的时候可以把防火墙全部关掉。
查看防火墙状态

    $ systemctl status firewalld  #查看防火墙状态

    $ systemctl stop firewalld  #关闭防火墙

    $ systemctl start firewalld #启动防火墙

    $ systemctl restart firewalld #重启防火墙

    $ systemctl enable firewalld #开机启动防火墙

    $ systemctl disable firewalld #禁止开机启动防火墙

上面的命令将firewalld替换为其他服务，对绝大多数的服务有相同的效果，比如（`$ systemctl status httpd`）查看httpd服务的状态。


## 安装nginx出现的问题

在./configure的时候回报找不到PCRE library，gzip需要zlib库的错误，所以在这之前需要把这些库安装好。
如果编译工具也没有，可以安装一下。

`$ yum install gcc`

`$ yum install gcc-c++`

pcre:rewrite所要使用的第三方模块
http://www.pcre.org/

	$ wget ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.13.zip

openssl：https协议所要使用的模块
http://www.openssl.org/source/下载源码包安装。

    $ wget http://www.openssl.org/source/openssl-1.0.0e.tar.gz
或者

    yum install -y openssl

缺少zlib的情况，

    yum install -y zlib-devel

如果你用到uploadprogress模块
http://wiki.nginx.org/HttpUploadProgressModule

	wget https://github.com/masterzen/nginx-upload-progress-module/downloads
 

2>配置

    ./configure --prefix=/opt/nginx-1.0.6 --with-openssl=../openssl-1.0.0e --with-pcre=../pcre-8.13 --add-module=../masterzen-nginx-upload-progress-module-c7c663f --add-module=../vkholodkov-nginx-upload-module-2ec4e4f