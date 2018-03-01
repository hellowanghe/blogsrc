---
title: vmlinux虚拟机找不到ip
date: 2018-01-24 18:43:14
tags: Linux虚拟机ip问题
categories: Linux
---
### 虚拟机下linux没有ip（Centos7）

虚拟机环境

- 操作系统windows7专业版64位系统
- 虚拟机软件VMware® Workstation 12 Pro
- 虚拟机系统Centos7mini版

常在虚拟机上学习linux，昨天装了一个Centos7的mini版本，试着安装禅道。可以装完后用ip address 查看不到ip地址，ip都查不到如何连接呢。

![](https://github.com/hellowanghe/blogimg/blob/master/img/vmipissue1.png?raw=true)

即使配置了ip和路由也不行。在`/etc/sysconfig/network-scripts`中可以看到一个ifcfg-ens33的配置文件，用vi或vim工具打开后，编辑文件，在文件尾部增加`GATEWAY=10.10.10.10`（具体网关地址，根据自己情况填写），加上`IPADDR=192.168.0.1`则给电脑配置了固定ip。

折腾了半天，上网找答案没有找到结果。桥接模式后虚拟机应该是连接到本机的物理网卡的，打开编辑菜单，选择虚拟网络编辑器，
![](https://github.com/hellowanghe/blogimg/blob/master/img/vmipissue2.png?raw=true)

点击更改设置，将类型选为桥接模式，
![](https://github.com/hellowanghe/blogimg/blob/master/img/vmipissue3.png?raw=true)



选择桥接到网卡时，一定注意，可以看到下拉框下有好几个网卡，大部分为虚拟网卡，这时指定选择你的电脑所用的网卡，
![](https://github.com/hellowanghe/blogimg/blob/master/img/vmipissue6.png?raw=true)

如果不清楚，可到控制面板，网络连接中，查看电脑现用网卡的名字。
![](https://github.com/hellowanghe/blogimg/blob/master/img/vmipissue7.png?raw=true)

点击应用，确定。

![](https://github.com/hellowanghe/blogimg/blob/master/img/vmipissue4.png?raw=true)

稍等一会，vmworkstation应用完设置后，我们再在虚拟机中，查看ip会发现已经有了ip，和电脑在同一网段。
这会就可以在本机上访问虚拟机上的服务了。如果还访问不到，可以查看80等端口有没有开放。



![](https://github.com/hellowanghe/blogimg/blob/master/img/vmipissue5.png?raw=true)











