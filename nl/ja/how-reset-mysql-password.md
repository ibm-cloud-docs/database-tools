---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL root ユーザー・パスワードの再設定

{{site.data.keyword.mysql}} root ユーザー・パスワードを再設定する必要がある場合は、以下の手順を実行します。

1. mysqld サーバーに kill (kill -9 ではなく) を送信して、mysqld サーバーを停止します。 pid は .pid ファイルに格納されています。このファイルは、通常 {{site.data.keyword.mysql}} データベース・ディレクトリーにあります。
  * 例: `shell> kill cat /your-mysql-data-directory/hostname.pid`
  * Red Hat で、以下のようにしてデータベースを停止することもできます。
    * 例: `shell> service mysqld stop`
    * ユーザーは、Unix root ユーザーであるか、サーバーを実行するのとデータベースを停止するのが同じユーザーでなければなりません。
2. --skip-grant-tables オプションを指定して、mysqld を再始動します。
3. mysqld サーバーに接続します。
  * **オプション 1:** mysql -h hostname mysql を指定し、GRANT コマンドを使用してパスワードを変更します。
    * GRANT コマンドについて詳しくは、[{{site.data.keyword.mysql}} 資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.mysql.com/doc/G/R/GRANT.html){: new_window} を参照してください。
  * **オプション 2:** `shell> mysqladmin -h hostname -u user password 'new password'`
4. `shell> mysqladmin -h hostname flush-privileges` を使用するか、SQL コマンド `mysql> FLUSH PRIVILEGES;` を使用して、特権テーブルをロードします。


**注:** --skip-grant-tables を指定して mysqld を始動した後、_FLUSH PRIVILEGES_.* を実行するまでは、GRANT コマンドを使用すると `Unknown command` エラーになります。
