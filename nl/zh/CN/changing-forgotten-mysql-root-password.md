---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 更改忘记的 MySQL root 用户密码

要更改 {{site.data.keyword.mysql}} root 用户密码，请使用以下步骤： 

1. 运行以下命令：

        # /etc/init.d/mysqld stop
        # mysqld_safe --skip-grant-tables --skip-networking

2. 使用以下命令连接到 {{site.data.keyword.mysql}}：

        # mysql -u root

3. 在 {{site.data.keyword.mysql}} 客户机中运行以下命令：

        # UPDATE mysql.user SET Password=PASSWORD('newpassword') WHERE User='root';

4. 将“newpassword”替换为新的 root 用户密码。

5. 使用以下命令重新启动 {{site.data.keyword.mysql}} 服务器： 

        # /etc/init.d/mysqld start
