---
title: MySQL_入门笔记
date: 2017-07-04 14:45:01
tags: MySQL
categories: MySQL&linux
---
# 学习笔记
mysql是开源的关系型数据库。可参见菜鸟教程[http://www.runoob.com](http://www.runoob.com "菜鸟教程")的介绍。
# 安装
（我用的是centos7 64位的系统）
### 检查

    rpm -qa|grep mysql
### 卸载
    rpm -e mysql

-----
    rpm -e--nodeps mysql

### 安装
用yum安装，centos7上**mysql**已经改为了**mariadb**，所以安装的时候和之前版本的有些不同，
### centos7下的mysql
    $ yum install mariadb-server mariadb #安装数据库和数据库服务器
（之前的centos版本可以这样安装：
`yum install mysql-server mysql mysql-develop`
）
或者

    $ yum install mariadb*   #把所有和mariadb相关的东西都装上
完成后，可以输入**`mysqladmin --version`** 来查看安装是否成功。
![https://github.com/hellowanghe/blogimg/blob/master/img/mysql1.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/mysql1.PNG?raw=true)
如果出现版本信息，就说明安装成功了。

注意：安装完之后，在命令行直接输入mysql是会报错了，
![https://github.com/hellowanghe/blogimg/blob/master/img/mysql2.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/mysql2.PNG?raw=true)
应该先启动数据库服务器，`$ systemctl start mariadb`

![https://github.com/hellowanghe/blogimg/blob/master/img/mysql3.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/mysql3.PNG?raw=true)

相关命令：（`systemctl stop mariadb #停止服务,systemctl restart mariadb #重启服务,systemctl enable mariadb #开机启动,systemctl status maridb #查看状态`）
启动之后，在次输入mysql就可以进入数据库了，Mysql服务器的密码为空，本次不用输入密码，如上图。

此时进入时没有用户名的。
### 创建root用户和密码
上面看到，在初次登录的时候mysql是没有密码的，所以要设置root用户的密码，root用户是超级用户，拥有的很大的权限，密码是很有必要的。
    
![https://github.com/hellowanghe/blogimg/blob/master/img/mysql4.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/mysql4.PNG?raw=true)

为了方便，我设置了简单的密码。下次登录的时候，就需要密码了，直接输mysql系统会告诉你Access denied。
## 基本命令
登录到mysql的命令行后，我们可以先查看一下有几个数据库。
![https://github.com/hellowanghe/blogimg/blob/master/img/mysqluse.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/mysqluse.PNG?raw=true)
### 创建数据库
可以看到所有的数据库。test，test1，test2是我自己建的。选择你要操作的数据库，用use语句，首先创建一个数据库test。

    create database test；

-------
### 选择数据库

      use test；
我们就进入到了`test`库。查看库中的表，由于这是个新建的库，当我用
`show tables`；的时候，他会提示空`empty set`；
### 删除数据库，
如果你要删除某个数据库。比如；

    drop database test2；删除掉test2数据库。
### 创建表
一般格式为
> CREATE TABLE table_name (column_name column_type);

简单的例子:<br>
    
> CREATE TABLE person(person_name CHAR,person_age INT,person_sex CHAR);

建立了名为`person`的表，字段有`person_name`,`person_age`,`person_sex`,
就是名字年龄和性别。`CHAR`代表字符 `INT`代表整数数字。可以用`desc ‘表名’`来查看表字段的属性。
![https://github.com/hellowanghe/blogimg/blob/master/img/mysqldesc.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/mysqldesc.PNG?raw=true)	
可以看到，`name`和`sex`字段的`type`属性为`char（1）`，这因为建表的时候没有声明字段的长度，默认为1了。
### 删除表
> drop table person；

和删除数据库命令类似，这里就不做演示了。

### INSERT插入数据

> INSERT INTO person（person_name，person_age,person_sex)<br>
values("jack",23, "male");

然后查看，
![https://github.com/hellowanghe/blogimg/blob/master/img/mysql_insert.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/mysql_insert.PNG?raw=true)
![https://github.com/hellowanghe/blogimg/blob/master/img/mysql_insert1.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/mysql_insert1.PNG?raw=true)

发现，`name`和`sex`字段只有一个字符，这就是之前的问题了，他的字符长度是1，只能容纳一个字符。现在改变他的属性。
### ALTER-删除，添加
ALTER TABLE

>ALTER TABLE person DROP person_name;
>\#删除person表的person_name字段
>ALTER TABLE person ADD person_name INT FIRST;
>\#给person表添加person_name字段，并放在第一列。
>ALTER TABLE person DROP person_age;
>ALTER TABLE person ADD person_age INT AFTER person_name;
>\#删除person_age字段，再添加person_age字段，并插在person_name字段后边。

注：默认的添加字段是放在最后面的。

### ALTER-修改字段
修改表字段的属性有两种方法：MODIFY和CHANGE。
下面是两种方法修改person表中，person_name字段的属性。
#### MODIFY
>ALTER TABLE person MODIFY person_name CHAR(10);

#### CHANGE
> ALTER TABLE person CHANGE COLUMN person_name person_name CHAR(10) NOT NULL;

修改完成后，再插入一条数据，可以发现，person_name已经可以，正常显示了。
![https://github.com/hellowanghe/blogimg/blob/master/img/mysql_insert2.PNG?raw=true](https://github.com/hellowanghe/blogimg/blob/master/img/mysql_insert2.PNG?raw=true)


### ALTER-修改表名
下面的语句可以修改表名。如果有需要的话。将表person重命名为person_tbl。
>ALTER TABLE person RENAME TO person_tbl;

## 创建用户与权限管理

之前我们已经有了root用户及密码，我们以root用户登录，创建其他的用户，用来控制权限。
创建用户有两种方法（前提以root用户登录）
1. GRANT命令<br>
2. 用insert 语句直接在mysql库user表中直接插入用户

### GRANT命令创建用户

>GRANT ALL PRIVILEGES 
>ON \*.\* TO 'monty'@'localhost'
>IDENTIFIED BY 'some_pass' WITH GRANT OPTION

超级用户，用于本机链接。

>GRANT ALL PRIVILEGES ON \*.\* TO 'monty'@'%'<br>
>IDENTIFIED BY 'some_pass' WITH GRANT OPTION;

超级用户，用于从其他主机连接。

>GRANT RELOAD,PROCESS ON \*.\* TO 'admin'@'localhost';

无密码admin账户，授予RELOAD和PROCESS权限。
这些权限允许`admin`用户执行`mysqladmin reload`，`mysqladmin refresh`， `mysqladmin flush-xxx`命令，
以及`mysqladmin processlist`。未授予访问数据库的权限。

>GRANT USAGE ON \*.\* TO 'dummy'@'localhost';


无密码，只用于从本机连接。未授予权限，

 >GRANT ALL PRIVILEGES ON db_1.\* to 'jack'@'localhost' <br>IDENTIFIED BY "jack" WITH GRANT OPTION；

该用户只能访问db_1的数据库。

### INSERT语句创建用户

> MariaDB>INSERT INTO user
> (host, user, authentication_string,
> select_priv, insert_priv, update_priv)
> VALUES ('localhost', 'guest',
> PASSWORD('guest123'), 'Y', 'Y', 'Y');

**注意:在用inser语句创建完用户后，需要执行 FLUSH PRIVILEGES命令。 这个命令执行后会重新载入授权表。否则，你插入所建的用户不会生效，除非你重启数据库服务。**

**注意：用insert创建用户时，可能会弹出，某字段不能空的错误，具体的语句可以参照mysql库user表的字段写，确保不会出错**