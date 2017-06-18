---
title: Linux 常用命令
date: 2017-06-10 18:43:14
tags: 常用命令
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









