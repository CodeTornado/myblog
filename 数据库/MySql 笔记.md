# 初始 MySql

## 什么是数据库

数据库 ( **DataBase** , 简称**DB** )

**概念** : 长期存放在计算机内,有组织,可共享的大量数据的集合,是一个数据 "仓库"

**作用** : 保存,并能安全管理数据(如:增删改查等),减少冗余...



### **数据库分类 **:

关系型数据库 ( SQL )

- MySQL , Oracle , SQL Server , SQLite , DB2 , ...
- 关系型数据库通过外键关联来建立表与表之间的关系

非关系型数据库 ( NOSQL )

- Redis , MongoDB , ...
- 非关系型数据库通常指数据以对象的形式存储在数据库中，而对象之间的关系通过每个对象自

身的属性来决定



## 什么是DBMS

数据库管理系统 ( **D**ata**B**ase **M**anagement **S**ystem )

数据库管理软件 , 科学组织和存储数据 , 高效地获取和维护数据

MySQL是一个数据库管理系统



## MySQL简介

**概念** **:** 是现在**流行**的**开源**的,**免费**的 **关系型**数据库

**历史** **:** 由瑞典MySQL AB 公司开发，目前属于 Oracle 旗下产品。

**特点** **:**

- 免费 , 开源数据库

- 小巧 , 功能齐全

- 使用便捷

- 可运行于Windows或Linux操作系统

- 可适用于中小型甚至大型网站应用

**官网** **:** **https://www.mysql.com/**



## 使用命令行连接数据库

```sql
mysql -uroot -p123456

mysql -uroot -p
Enter password: *****


--修改登录密码
update mysql.user set authentication_string=password(‘123456’) where user=‘root’ and Host = ‘localhost’
flush privileges; --刷新权限

----------------------------------------------------------------------------
-- 所有的语句都需要用分号结尾

show databases; --看所有的数据库列出名称

use school; --切换到 use 数据库

show tables; --查看数据库中所有的表
describe student; --显示数据库中student的表的所有字段信息

create database westos; --创建一个数据库

exit; --退出连接

-- 单行注释
/*
多行注释
*/

-- 模式通配符： _ 任意单个字符 % 任意多个字符，甚至包括零字符 单引号需要进行转义 \'

-- SQL对大小写不敏感 （关键字）

-- 可用反引号（`）为标识符（库名、表名、字段名、索引、别名）包裹，以避免与关键字重名！中文 也可以作为标识符！

```





## 数据库语句分类 Ddata DMQC Language

| 名称                 | 解释                                         | 命令                    |
| -------------------- | -------------------------------------------- | ----------------------- |
| DDL （数据定义语言） | 定义和管理数据对象，如数据库，数据表等       | CREATE、DROP、ALTER     |
| DML （数据操作语言） | 用于操作数据库对象中所包含的数据             | INSERT、UPDATE、DELETE  |
| DQL （数据查询语言） | 用于查询数据库数据                           | SELECT                  |
| DCL （数据控制语言） | 用于管理数据库的语言，包括管理权限及数据更改 | GRANT、commit、rollback |




# 操作数据库
## 基本命令

创建数据库

```sql
create database [if not exists] 数据库名;
```

删除数据库
```sql
DROP DATABASE [IF EXISTS] 数据库名;
```
使用数据库
```sql
USE 数据库名;
```
查看数据库
```sql
SHOW DATABASES;
```



> 操作可视化数据库管理工具，然后查看历史记录中sql语句来学习mysql

---





## 数据库列的数据类型

> 数值

| 数据类型 | 说明 | 占字节 |
| -------- | ---- | ------ |
| tinyint | 十分小的数据 | 1    |
| smallint | 较小的数据 | 2    |
| mediumint | 中等大小的数据 | 3    |
| int  | 标准的整数 | 4    |
| bigint | 较大的数据 | 8    |
| float | 浮点数 | 4    |
| double | 浮点数 | 8    |
| decimal (m, d) | 字符串形式的浮点数 | mysql < 3.23 为 m个字节；mysql > 3.23 为 m+2个字节； |


> 字符串

| 数据类型 | 说明             | 占用byte |
| -------- | ---------------- | -------- |
| char     | 固定大小的字符串 | 0~255    |
| varchar  | 可变字符串       | 0~65535  |
| tinytext | 微型文本         | 2^8 - 1  |
| text     | 文本串           | 2^16 - 1 |



> 时间日期

| 数据类型  | 说明     | 格式                                      |
| --------- | -------- | ----------------------------------------- |
| date      | 日期     | YYY-MM-DD                                 |
| Time      | 时间     | HH:mm:ss                                  |
| Datetime  | 日期时间 | YYY-MM-DD HH:mm:ss                        |
| Timestamp | 时间戳   | 时间戳, 1970.1.1 到现在时间差的毫秒数表示 |
| year      | 年份     | 1901~2155                                 |





## 表的字段属性

**Unsigned**

- 无符号的整数
- 声明了该列不能声明为复数



**zerofill**

- 0填充的
- 不足的位数,使用0来填充, int (3) ,  5---> 005



**自增** AUTO_INCREMENT

- 通常理解为自增,自动在上一条记录的基础上+1 (默认)
- 通常用来设计唯一的主键~ index,必须是整数类型
- 可以自定义设计主键自增的起始值和步长



**非空 ** NUll not null

- 假设设置为not null ,如果不给它赋值,就会报错!
- NUIl ,如果不填写值,默认就是null!



**默认** DEFAULT

- 置默的值!

- sex,默认值为男,如果不指定该列的值,则会有默认的值!





##  创建表

> 字符串用单引号包裹
>
> 两个列声明语句用英文逗号连接
>
> PRIMARY KEY 表示主键, 一般一个表只有一个主键

```sql
CREATE TABLE [IF NOT EXISTS] `表名`(
	`字段名` 列类型 [属性] [索引] [字段注释],
  
	`字段名` 列类型 [属性] [索引] [字段注释]
) [表引擎类型] [字符集设置] [注释]
```

```sql
create table if not exists `student` (
	`id` int(4) not null auto_increment comment '学号',
	`name` varchar(30) not null default '匿名' comment '姓名',
	`pwd` varchar(20) not null default '123456' comment '密码',
	`sex` varchar(2) not null default '女' comment '性别',
	`birthday` datetime  default NULL comment '生日',
	`address` varchar(100) default NULL comment '住址',
	`email` varchar(50) default NULL comment '邮箱',
	PRIMARY KEY(`id`)
) ENGINE=INNODB DEFAULT CHARSET=UTF8;

--- 用↑↓都可以 ---

DROP TABLE IF EXISTS `student`;
CREATE TABLE `student` (
  `id` int(4) NOT NULL AUTO_INCREMENT COMMENT '学号',
  `name` varchar(30) NOT NULL DEFAULT '匿名' COMMENT '姓名',
  `pwd` varchar(20) NOT NULL DEFAULT '123456' COMMENT '密码',
  `sex` varchar(2) NOT NULL DEFAULT '女' COMMENT '性别',
  `birthday` datetime DEFAULT NULL COMMENT '生日',
  `address` varchar(100) DEFAULT NULL COMMENT '住址',
  `email` varchar(50) DEFAULT NULL COMMENT '邮箱',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

```



> 建表常用命令

```sql
SHOW CREATE DATABASE `school`; -- 查看建库语句
SHOW CREATE TABLE `student`; -- 查看建表语句
DESC `student`; -- 查看表结构
```



## MySql 表的引擎类型

查看mysql所支持的全部引擎类型 (表类型)

```sql
SHOW ENGINES;
```

| Engine 引擎 | Support 支持 | Comment 注释 |
| ------ | ------- | ------- |
|ARCHIVE			|		YES	|			 Archive storage engine|
|BLACKHOLE		|	  YES		|	 	/dev/null storage engine (anything you write to it disappears)|
|MRG_MYISAM	|	  YES		|	 	Collection of identical MyISAM tables|
|FEDERATED		|	  NO		|		  Federated MySQL storage engine|
|**MyISAM**				|	 YES			| MyISAM storage engine; MyISAM存储引擎 |
|PERFORMANCE_SCHEMA|	YES |	Performance Schema|
|**InnoDB**				|	  **DEFAULT**	| Supports transactions, row-level locking, and foreign keys ;支持事务、行级锁定和外键 |
|MEMORY		|		   YES		|	 	Hash based, stored in memory, useful for temporary tables|
|CSV					|	     YES	|		 	CSV storage engine|

## MyISAM 与 InnoDB 存储引擎对比

| 名称       | MylSAM | InnoDB       |
| ---------- | ------ | ------------ |
| 事务处理   | 不支持 | 支持         |
| 数据行锁定 | 不支持 | 支持         |
| 外键约束   | 不支持 | 支持         |
| 全文索引   | 支持   | 不支持       |
| 表空间大小 | 教小   | 较大，约2倍! |

经验 ( 适用场合 ) :

​	适用 MyISAM : 节约空间及相应速度

​	适用 InnoDB : 安全性 , 事务处理及多用户操作数据表



## **修改表结构**

>  修改表 ( ALTER TABLE )

修改表名 : `ALTER TABLE 旧表名 RENAME AS 新表名`

添加字段 : `ALTER TABLE 表名 ADD 字段名 列属性[属性]`

修改字段 :

- `ALTER TABLE 表名 MODIFY 字段名 列类型[属性]` 

- `ALTER TABLE 表名 CHANGE 旧字段名 新字段名 列属性[属性]
  `

删除字段 : `ALTER TABLE 表名 DROP 字段名`



>  删除数据表

语法： `DROP TABLE [IF EXISTS] 表名` 

- `IF EXISTS` 为可选 , 判断是否存在该数据表
- 如删除不存在的数据表会抛出错误



# MySQL数据管理

## 外键

如果公共关键字在一个关系中是主关键字，那么这个公共关键字被称为另一个关系的外键。由此可见，

外键表示了两个关系之间的相关联系。以另一个关系的外键作主关键字的表被称为**主表**，具有此外键的

表被称为主表的**从表**。



在实际操作中，将一个表的值放入第二个表来表示关联，所使用的值是第一个表的主键值(在必要时可包

括复合主键值)。此时，第二个表中保存这些值的属性称为外键(**foreign key**)。



**外键作用**

保持数据**一致性**，**完整性**，主要目的是控制存储在外键表中的数据,**约束**。 使两张表形成关联，外键只能

引用外表中的列的值或使用空值。



>  创建外键

建表时指定外键约束

```sql
-- 创建外键的方式一 : 创建子表同时创建外键

CREATE TABLE `student` (
	`studentname` VARCHAR ( 20 ) NOT NULL DEFAULT '匿名' COMMENT '姓名',
  
	`gradeid` INT ( 10 ) DEFAULT NULL COMMENT '年级',
	PRIMARY KEY ( `studentno` ),
	KEY `FK_gradeid` ( `gradeid` ),
	CONSTRAINT `FK_gradeid` FOREIGN KEY ( `gradeid` ) REFERENCES `grade` ( `gradeid` ) 
) ENGINE = INNODB DEFAULT CHARSET = utf8

-- 创建外键方式二 : 创建子表完毕后,修改子表添加外键 
ALTER TABLE `student` 
ADD CONSTRAINT `FK_gradeid` FOREIGN KEY (`gradeid`) 
REFERENCES `grade` (`gradeid`);
```



> 删除具有主外键关系的表时 , 要先删子表的外键, 子表的外键索引 , 后删主表
>
> 不建议使用↑物理外键, 要使用逻辑外键:
>
> - 不得使用外键与级联,一切外键概念必须在应用层解决。
> - 每次做DELETE或者UPDATE都必须考虑外键约束,会导致开发的时候很痛苦,测试数据极为不方便。



## DML 数据操作语言 

Data Manipulation Language 数据操作语言

用于操作数据库对象中所包含的数据

包括 :

- INSERT (添加数据语句)
- UPDATE (更新数据语句)
- DELETE (删除数据语句)



## **添加数据**

> INSERT 命令

**语法**

```sql
INSERT INTO 表名[(字段1,字段2,字段3,...)] VALUES('值1','值2','值3') 
```

字段或值之间用英文逗号隔开 .

' 字段1,字段2...' 该部分可省略 , 但添加的值务必与表结构,数据列,顺序相对应,且数量一致 .

可同时插入多条数据 , values 后用英文逗号隔开 .



```sql
-- 使用语句如何增加语句? 
-- 语法 : INSERT INTO 表名[(字段1,字段2,字段3,...)] VALUES('值1','值2','值3') 
INSERT INTO grade(gradename) VALUES ('大一'); 
-- '字段1,字段2...'该部分可省略 , 但添加的值务必与表结构,数据列,顺序相对应,且数量一 致. 

-- 一次插入多条数据 
INSERT INTO grade(gradename) VALUES ('大三'),('大四');
```















