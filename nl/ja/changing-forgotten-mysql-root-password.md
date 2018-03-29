---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL ルート・パスワードを忘れた場合の変更

{{site.data.keyword.mysql}} ルート・パスワードを変更するには、以下の手順を使用します。 

1. 以下のコマンドを実行します。

        # /etc/init.d/mysqld stop
        # mysqld_safe --skip-grant-tables --skip-networking

2. 次のコマンドを使用して、{{site.data.keyword.mysql}} に接続します。

        # mysql -u root

3. {{site.data.keyword.mysql}} クライアントで、次のコマンドを実行します。

        # UPDATE mysql.user SET Password=PASSWORD('newpassword') WHERE User='root';

4. 'newpassword' を新しいルート・パスワードに置き換えます。

5. 次のコマンドを使用して、{{site.data.keyword.mysql}} サーバーを再始動します。

        # /etc/init.d/mysqld start
