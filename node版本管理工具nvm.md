---
title: nvm-node版本管理工具
date: 2017-06-15 08:17:49
tags: nvm
categories: node
---
### nvm出现的原因
在nodejs的开发中，会需要用到不同的nodejs版本，**现阶段node各个版本对一些软件支持不太够**，js新的技术层出不穷，各种新的框架，js语言的不断更新，ES6/ES7新标准的js，nodejs也在不断更新。为了方便切换到不同的nodejs版本。

淘宝的nodejs所有的镜像
[https://npm.taobao.org/mirrors/node](https://npm.taobao.org/mirrors/node "nodejs镜像")

nvm-windows的github地址
[https://github.com/coreybutler/nvm-windows](https://github.com/coreybutler/nvm-windows "nvm-windows")

nvm的linux版本的github地址
[https://github.com/creationix/nvm](https://github.com/creationix/nvm "nvm")

### 安装

windows下nvm的安装比较简单，最好先卸载nodejs，下载nvm的windows的安装包，像安装其他软件一样。安装完成后，可以在淘宝的npm镜像下载你所需要的不同的版本的nodejs的压缩包zip格式就行。

nvm管理nodejs的目录默认在`C:\Users\dell\AppData\Roaming\nvm`，你的电脑上用户名就是你自己的，AppData有的是隐藏的，需要设置一下文件的查看方式，将其显示出来。将下载好的压缩包解压到，nvm的目录下，并重命名为`vx.x.x`即可，如图
![https://github.com/hellowanghe/blogimg/blob/master/img/nvm1.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/nvm1.PNG?raw=true)

在命令行输入

    nvm list

会显示可用的nodejs版本列表，当前再用版本也会显示出来。如图：
![https://github.com/hellowanghe/blogimg/blob/master/img/nvmlist.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/nvmlist.PNG?raw=true)

在命令行输入

    nvm use 4.5.0

nvm会自动切换到所选版本，nvm list可以看到，当前使用版本变为了4.5.0，也可用node -v查看版本是否改变。
![https://github.com/hellowanghe/blogimg/blob/master/img/nvmuse.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/nvmuse.PNG?raw=true)

### npm配置

国内使用npm如果速度比较慢，可以装上cnpm，cnpm是淘宝在国内的做的镜像，10分钟更新一次。
```
$ npm install -g cnpm --registry=https://registry.npm.taobao.org

$ npm config set registry https://registry.npm.taobao.org
可用以下命令查看，是否配置是否成功
$ npm config get registry
```