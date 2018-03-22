---
title: Chrome Package-extensions
date: 2018-03-22 13:25:14
tags: Chrome
categories: web
---
在使用谷歌的Chrome的时候，原本有很多插件可以使用，由于众所周知的原因，国内访问不到浏览器的应用商店。想分享插件不知如何是好，在网络上搜索一下，Chrome有一个打包扩展程序的功能，可以将下载的插件打包成crx格式文件。

首先，在谷歌浏览器中输入地址chrome://extensions/，即可打开扩展程序管理，将右上角的开发者模式打开后，可以看到浏览器上所安装的插件。还可以看到有`打包扩展程序`的功能

![https://raw.githubusercontent.com/hellowanghe/blogimg/master/chromep/chromep1.png](https://raw.githubusercontent.com/hellowanghe/blogimg/master/chromep/chromep1.png)

点击打包扩展程序，可以看见弹出框，让我们输入扩展程序的地址。
![https://raw.githubusercontent.com/hellowanghe/blogimg/master/chromep/chromep3.png](https://raw.githubusercontent.com/hellowanghe/blogimg/master/chromep/chromep3.png)


Chrome插件的地址一般为。
    `C:\Users\dell\AppData\Local\Google\Chrome\User Data\Default\Extensions\`
用户下为你自己的用户名，自己根据情况修改。在资源管理器中输入地址，可以看到Extensions目录下边，我们所安装的插件，文件夹的名称是插件的ID，在第一张图片中可以看到，每个插件的ID，ID所对应的文件夹就是该扩展程序的文件夹，可以看到上图，复制扩展程序目录的时候，一定把版本号地址也带过去
    
    C:\Users\dell\AppData\Local\Google\Chrome\User Data\Default\Extensions\mooikfkahbdckldjjndioackbalphokd\1.0.3.0_0
![https://raw.githubusercontent.com/hellowanghe/blogimg/master/chromep/chromep2.png](https://raw.githubusercontent.com/hellowanghe/blogimg/master/chromep/chromep2.png)

然后点击打包扩展程序，提示已创建。

![https://raw.githubusercontent.com/hellowanghe/blogimg/master/chromep/chromep4.png](https://raw.githubusercontent.com/hellowanghe/blogimg/master/chromep/chromep4.png)

此时我们到`C:\Users\dell\AppData\Local\Google\Chrome\User Data\Default\Extensions\mooikfkahbdckldjjndioackbalphokd\1.0.3.0_0`
目录下可以看到打包好的插件。

![https://raw.githubusercontent.com/hellowanghe/blogimg/master/chromep/chromep5.png](https://raw.githubusercontent.com/hellowanghe/blogimg/master/chromep/chromep5.png)

安装的时候，只需打开chrome浏览器输入chrome://extensions，然后将crx文件拖拽过去，点击添加扩展程序即可，不再赘述。

