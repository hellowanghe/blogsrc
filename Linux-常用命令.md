---
title: Linux 常用命令
date: 2017-06-10 18:43:14
tags: Linux常用命令
categories: Linux
---
### 常用基本命令（Centos7）
`# ls`  查看当前目录下文件和文件夹<br>

`# ll`  查看当前目录下文件和文件夹的详细信息<br>

`# ls -lh` 文件和文件的大小一k,M显示，不加h是以字节显示（`-lhr`正序排列，`-lhv`倒序排列） <br>

`# cd /home` 改变目录到绝对路径的home目录下（`/`表示绝对定位）<br>

`# cd home` 到当前目录下的`home`路径<br>

`# cp 1.txt /home/jack` 复制名叫`1.txt`的文件到`/home/jack`目录下<br>

`# cp one.txt /home/jack/two.txt` 复制名叫`one.txt`的文件到`/home/jack`下并重命名为`two.txt`<br>

`# mv one.txt three.txt` 将名为`one.txt`的文件重命名为`three.txt`<br>

`# mv one.txt /root` 将名为`one.txt`的文件移动到`/root`目录下<br>

`# mkdir tom` 新建名为`tom`的目录（文件夹）<br>

`# touch main.java` 新建名为`main`的`java`格式文件<br>

`# touch book.txt` 新建名为`book`的`txt`格式文件<br>

`# rm one.txt` 删除名为`one.txt`的文件，（rm意为remove）<br>

`# rmdir tom` 删除名为`tom`的文件夹，只能删除空文件夹（同 `# rm -d`）<br>

`# rm -r tom` （recursive递归删除文件夹，及其包含的内容，每次删除都会有提示。<br>

`# rm -rf tom` 删除文件夹，强制删除文件夹中所有内容，不再询问<br>

### 压缩命令

tar命令可以为linux的文件和目录创建档案。利用tar，可以为某一特定文件创建档案（备份文件），也可以在档案中改变文件，或者向档案中加入新的文件。tar最初被用来在磁带上创建档案，现在，用户可以在任何设备上创建档案。利用tar命令，可以把一大堆的文件和目录全部打包成一个文件，这对于备份文件或将几个文件组合成为一个文件以便于网络传输是非常有用的。

**首先要弄清两个概念：打包和压缩。打包是指将一大堆文件或目录变成一个总的文件；压缩则是将一个大的文件通过一些压缩算法变成一个小文件。**

为什么要区分这两个概念呢？这源于Linux中很多压缩程序只能针对一个文件进行压缩，这样当你想要压缩一大堆文件时，你得先将这一大堆文件先打成一个包（tar命令），然后再用压缩程序进行压缩（gzip bzip2命令）。

打包压缩文件，不加z时，只打包不压缩

    $ tar -zcvf file.tar.gz file

解压缩文件

    $ tar -zxvf file.tar.gz


压缩一个tar备份文件，此时压缩文件的扩展名为.tar.gz

    $ gzip -r log.tar
解压缩tar.gz文件

     $ gzip -d log.tar.gz









