# 关于Mysql字符集编码的问题解决方案

每次在新电脑上安装了MySQL或者重装MySQL后，总会出现汉字输入出现乱码的问题，这个问题本身不是很难，但是好记性不如烂笔头，何况自己的记性一直不好，遇到该类问题总要咨询百度，每次都需要打开N个页面，还需要综合好几个人的回答，才能找到解决方案。索性自己写一篇文章记录下来，既节约时间，也避免浪费精力去筛选各个网站信息。

 MySQL无法存储中文或者中文乱码，当然是编码的问题。你可以输入：**`mysql -u root -p`**进入Mysql命令行环境，然后输入命令:**` show variables like '%char%'; `**查看当前编码格式:

```sql
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8                       |
| character_set_connection | utf8                       |
| character_set_database   | latin1                     |
| character_set_filesystem | binary                     |
| character_set_results    | utf8                       |
| character_set_server     | latin1                     |
| character_set_system     | utf8                       |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
```

可以看出，其中的character_set_database 和character_set_server的value为latin1；此时你如果使用insert插入中文字符就会出现如下的错误：

**`ERROR 1366 (HY000): Incorrect string value: '\xE5\x93\x88\xE5\x93\x88' for column`**

此时，我们需要将其改为支持中文的编码格式，比如gb2312，gbk，utf8等。gb2312是简体中文的码，gbk支持简体中文及繁体中文，utf8支持几乎所有字符。这里我们就将其改为**utf8**。 

#### 1. 查找my.ini文件

修改MySQL的编码格式，需要修改my.ini文件中的配置信息；网上说这个文件在MySQL的安装路径，不知道他们的电脑和MySQL的版本是什么，反正我是翻遍了也没找到，最终在`C:\ProgramData\MySQL\MySQL Server 5.7`下找到了。

#### 2.修改my.ini文件

打开my.ini文件，需要对其中的三处进行修改，在其中添加字符集设置：

```
[mysqld]
character-set-server = utf8

[client]
default-character-set=utf8

[mysql]
default-character-set=utf8
```

#### 3.复制my.ini文件

将修改完成的my.ini文件，复制粘贴到MySQL的安装路径；我的路径：`C:\Program Files\MySQL\MySQL Server 5.7`

#### 4.重启MySQL服务器

以管理员身份打开cmd，先后输入`net stop mysql`和`net start mysql`两个命令重启MySQL服务。

#### 5.确认修改效果

进入MySQL的命令行环境，输入编码查看口令:` show variables like '%char%';`

```
mysql> show variables like '%char%';
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8                       |
| character_set_connection | utf8                       |
| character_set_database   | utf8                       |
| character_set_filesystem | binary                     |
| character_set_results    | utf8                       |
| character_set_server     | utf8                       |
| character_set_system     | utf8                       |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
```

到此为止，MySQL数据库的编码格式修改完成，可顺畅的输入中文字符了！

以上内容借鉴了如下文章的内容。

> [Windows mysql默认字符集修改](https://www.cnblogs.com/wuyongyu/p/6640940.html)

> [ 解决Mysql存储中文的问题](https://blog.csdn.net/lisonglisonglisong/article/details/25315965)

> [关于Mysql的安装遇到的问题，找不到my.ini , 以及修改Mysql密码](https://blog.csdn.net/believe_today/article/details/79223684)

> [如何修改MySQL字符集](http://www.cnblogs.com/HondaHsu/p/3640180.html)

