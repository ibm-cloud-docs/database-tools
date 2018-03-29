---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 修复无法打开的 MySQL 表

对 {{site.data.keyword.mysql}} 表的修复会视情况进行处理，但是如果使用的是缺省 {{site.data.keyword.mysql}} 表类型 MyISAM（这是缺省 Storage Engine，除非已另外更改或指定），那么您有以下若干选项。

1. 可以通过命令行运行 myisamchk 实用程序来检查、修复或优化表。此命令通常在数据库不运行期间执行。有关更多信息，请参阅 [myisamchk ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://dev.mysql.com/doc/refman/5.0/en/myisamchk.html){: new_window}。
2. mysqlcheck 的功能类似于 myisamchk，但 mysqlcheck 可以在数据库运行期间执行。有关更多信息，请参阅 [mysqlcheck ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://dev.mysql.com/doc/refman/5.0/en/mysqlcheck.html){: new_window}。
3. 如果您已登录到数据库，那么还可以运行 SQL 命令来解决问题。

    示例命令：
    *mysql> optimize table your-tablename
    *mysql> analyze table your-tablename
    *mysql> repair table your-tablename
    有关更多信息，请参阅[表维护 SQL ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://dev.mysql.com/doc/refman/5.0/en/table-maintenance-sql.html){: new_window}。
4. 如果要获取 {{site.data.keyword.mysql}} 错误数，并且您不确定错误的内容，那么可以通过命令行运行 perror 实用程序来查找错误数。有关更多信息，请参阅 [perror ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://dev.mysql.com/doc/refman/5.0/en/perror.html){: new_window}。

    示例：
    *shell> perror 13 64
    *错误代码 13：许可权被拒绝
    *错误代码 64：机器未联网
