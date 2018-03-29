---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL 优化/修复信息

## MySQL 如何使用内存 
下面是 mysqld 服务器使用内存的一些方法以及关联的 mysqld 变量名称。
* [内存使用 MySQL 5.0 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://dev.mysql.com/doc/refman/5.0/en/memory-use.html){: new_window}
* [内存使用 MySQL 4.1 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://dev.mysql.com/doc/refman/4.1/en/memory-use.html){: new_window}

## MySQL 优化涵盖以下各项：
- 优化概述
- 优化 SELECT 和其他语句
- 锁定问题
- 优化数据库结构
- 优化 MySQL 服务器
- 磁盘问题

[优化 MySQL 5.0 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://dev.mysql.com/doc/refman/5.0/en/optimization.html){: new_window}
[优化 MySQL 4.1 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://dev.mysql.com/doc/refman/4.1/en/optimization.html){: new_window}

## MySQL 服务器变量 - 特定于 SQL 层或 Storage Engine。
以下链接列出其中一些更常用的变量。
[转至文章 1 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.mysqlperformanceblog.com/2006/06/08/mysql-server-variables-sql-layer-or-storage-engine-specific/){: new_window}
[转至文章 2 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://forge.mysql.com/wiki/ServerVariables){: new_window}

## 优化 mysqld 变量（作者：Ian Gilfillan）
请参阅此文章了解有关 MySQL 优化的信息，包括设置 mysqld 服务器变量（key_buffer_size、Query 高速缓存变量、table_cache、sort_buffer 等）的一些准则。
[转至文章 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.databasejournal.com/features/mysql/article.php/3367871){: new_window}

## 修复 MySQL 中的数据库损坏（作者：Ian Gilfillan）
使用 {{site.data.keyword.mysql}} 时，表损坏的情况十分罕见。但是，此文章有助于了解发生此类问题时如何进行修复。
[转至文章 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.databasejournal.com/features/mysql/article.php/3300511){: new_window}

## 优化 MySQL：查询和索引（作者：Ian Gilfillan）
<!--The database is too slow. Queries are queuing up, backlogs growing, users being refused connection. Management is ready to spend millions on "upgrading" to some other system, when the problem is really that MySQL is simply not being used properly. Badly defined or non-existent indexes are one of the primary reasons for poor performance, and fixing these can often lead to phenomenal improvements.-->
[转至文章 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.databasejournal.com/features/mysql/article.php/1382791){: new_window}

[Ian Gilfillan 编著的其他 {{site.data.keyword.mysql}} 文章 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.databasejournal.com/article.php/1474351){: new_window}
