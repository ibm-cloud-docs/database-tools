---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 重置 MySQL root 用户密码

如果需要重置 {{site.data.keyword.mysql}} root 用户密码，请完成以下步骤：

1. 通过向 mysqld 服务器发出 kill（不是 kill -9）命令，使 mysqld 服务器停止运行。PID 存储在 .pid 文件中，该文件通常位于 {{site.data.keyword.mysql}} 数据库目录中：
  * 示例：`shell> kill cat /your-mysql-data-directory/hostname.pid`
  * 在 Red Hat 中，也可以停止数据库：
    * 示例：`shell> service mysqld stop`
    * 您必须是 Unix root 用户或者是运行服务器的用户才可停止数据库。
2. 使用 --skip-grant-tables 选项重新启动 mysqld。
3. 连接到 mysqld 服务器：
  * **选项 1：**mysql -h hostname mysql，并使用 GRANT 命令更改密码。
    * 有关 GRANT 命令的更多信息，请参阅 [{{site.data.keyword.mysql}} 文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.mysql.com/doc/G/R/GRANT.html){: new_window}。
  * **选项 2：**`shell> mysqladmin -h hostname -u user password 'new password'`
4. 使用 `shell> mysqladmin -h hostname flush-privileges` 或 SQL 命令 `mysql> FLUSH PRIVILEGES;` 装入特权表。


**注：**使用 --skip-grant-tables 启动 mysqld 后，如果未运行 _FLUSH PRIVILEGES_，那么对 GRANT 命令的任何使用都会提供 `Unknown command` 错误。*
