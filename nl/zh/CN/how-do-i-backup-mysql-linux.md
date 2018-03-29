---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# 在 Linux 中备份 MySQL

## 从 MySQL 目录复制

缺省情况下，Linux 服务器上的 {{site.data.keyword.mysql}} 数据库存储在以下目录中：

`/var/lib/mysql/`

如果已先关闭 mysqld 服务，那么可以使用以下命令将数据库复制到示例 /backup 目录：

`cp –Rp /var/lib/mysql/*.* /backup`

cp 命令的 -R 开关表示递归，因为每个数据库均位于单独的目录中，所以需要使用此开关。-p 开关表示许可权，用于保持复制内容的许可权不变。

通常，在使用上述方法之前，要关闭 mysqld 服务。如果复制的数据库正在使用，那么备份会损坏而变得毫无价值。如果确定复制时没有任何数据库正在使用，那么可以使用上述命令。

## mysqldump 命令

使用 mysqldump 命令可备份服务器上的单个数据库和所有数据库，而不必关闭 mysqld 服务。由于这种方法能在使数据库保持联机的同时进行备份，因此首选此方法。

## 单个数据库

下面是示例命令，用于在您以 root 用户身份登录期间，将名为“_example_”的数据库备份到 /backup 目录：

`mysqldump example > /backup/example_backup.sql`

除非是小型数据库，否则请压缩数据库备份以减少备份传输时间。以下命令将压缩示例数据库的备份：

`tar czvf /backup/example_backup.tar.gz /backup./example_backup.sql`

## 所有数据库

如果有多个数据库要备份，请使用以下命令将服务器上的所有 {{site.data.keyword.mysql}} 数据库备份到 /backup 目录：

`mysqldump -A > /backup/databases.sql(or --all-databases)`

-A 开关（“-all-databases”可执行相同功能）用于转储服务器上的所有数据库。
