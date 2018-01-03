---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 變更忘記的 MySQL root 密碼

若要變更 {{site.data.keyword.mysql}} root 密碼，請使用下列步驟： 

1. 執行下列指令：

        # /etc/init.d/mysqld stop
        # mysqld_safe --skip-grant-tables --skip-networking

2. 使用下列指令，連接至 {{site.data.keyword.mysql}}：

        # mysql -u root

3. 在 {{site.data.keyword.mysql}} 用戶端中，執行下列指令：

        # UPDATE mysql.user SET Password=PASSWORD('newpassword') WHERE User='root';

4. 將 'newpassword' 取代為新的 root 密碼。

5. 使用下列指令，重新啟動 {{site.data.keyword.mysql}} 伺服器：

        # /etc/init.d/mysqld start
