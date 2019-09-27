---
title: 2019年9月26日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
## mysql
        引擎类型:可以省略不写,默认引擎就是myisam
                engine=innodb和engine=myisam
                在创建表时可以设置
                将定界符分号转成定界符//    delimiter //
                bdban启动xmapp：sudo /opt/lampp/manager-linux-x64.run
                启动MySQL：在命令行下进入到/opt/lampp/bin目录，使用命令：sudo ./mysql，回车即可

                MySQL语句不区分大小写
                查看所有数据库
                show databases;
                创建数据库
                create database 库名;
                删除数据库
                drop database 库名;
                使用该数据库
                use 库名;
                显示库中的所有表
                show tables;
                创建表：
                create table student( id int, name char(10) )default charset=utf8;
                查看表结构:
                describe 表名;
                show columns from 表名;
                删除表:
                drop table 表名;
                插入数据:
                insert into 表名 values(数据1,数据2,数据3);
                insert into 表名 values(数据1,数据2,数据3),(数据1,数据2,数据3)；
                主键:
                主键primary key 是唯一的并不能为null
                主要是更新或删除特定的行,因为他是唯一的,可以快速锁定到某行数据,
                主键可以应用到多个列(字段)上
                自增:
                auto_increment
                外键:
                foreign key
                可伸缩性:
                scale
                使用null值
                不能为空 not  null
                默认值default
                default 1
                重命名表:
                rename table 原名 to  新名;
                视图:
                创建视图	:create view name as select id,name,age from xd;
                创建名为name的视图字段数据为 xd表的id name age字段
                查看视图:select*from 视图名 where 字段='值';
                原表的数据修改的时候视图中的数据也会跟着修改
                视图的数据修改的时候视图中的数据也会随着修改
                update 表名 set 字段名=值 where 修改的字段=值;
