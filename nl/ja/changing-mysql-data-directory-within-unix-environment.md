---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Unix 系環境での MySQL データ・ディレクトリーの変更

{{site.data.keyword.mysql}} データ・ディレクトリーを変更するには、以下のステップに従ってください。

1. [PuTTY ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html){: new_window} または優先クライアントを使用して、サーバーにログインします。

  **注:** データ・ディレクトリーに専用パーティションを使用している場合は、データをコピーした後で、元のデータ・ディレクトリーの代わりに新規パーティションを必ずマウントしてください。 新規パーティションをマウントすると、一部のアプリケーションが機能しない可能性がある非標準の構成変更を行わずに済みます。

2. mysqld ({{site.data.keyword.mysql}} デーモン/サーバー) をシャットダウンします。デーモンを開始および停止するプロセスは、異なるオペレーティング・システムとディストリビューションの間では異なる場合があります。

  **注:** 未加工ファイルに直接影響する処理の間は、{{site.data.keyword.mysql}} を停止する必要があります。

  `/etc/init.d/mysql stop`
  または
  `/etc/init.d/mysqld、/etc/init.d/mysql-server、/usr/loca/etc/init.d/mysql、/opt/lamp…`

3. 変更を行う前に、データベースをバックアップします。 未加工データベース・ファイルの直接コピーを作成するときは、{{site.data.keyword.mysql}} デーモンが実行されていないことを確認してください。<!--(or be good at flushing and locking)-->

  サーバー上で cPanel を使用している場合、デーモンを再始動する前に cPanel (主として TailWatch/chkservd) を停止します。 「chkservd」がサービスを再始動するのを停止するために、一時ファイル `/etc/chkserv.d/mysqlisevil` を作成できます。 rsync を使い慣れていない場合は、他のツール (cp、cpio、tar など) を使用してバックアップを作成できます。

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql.'date +%s'`

4. データ・ディレクトリーを作成し、{{site.data.keyword.mysql}} ユーザー (または「my.cnf」グローバル・オプション・ファイルで指定されているいずれかのユーザー) の所有権を提供します。この例では、ロケーション `/var/lib/mysql-data` が使用されていますが、希望する任意のロケーションを使用できます。 この目的のために特別にディスクまたは論理装置を追加する場合は、先に進む前に、`/etc/fstab` にもエントリーを追加して、ディレクトリーをマウントする必要があります。

  `chown mysql:mysql /var/lib/mysql-data`

5. 元のディレクトリーの最終コピーを新規 {{site.data.keyword.mysql}} データ・ディレクトリーに作成します (最初のディレクトリーの最後にある末尾の / は必ず保持してください)。

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql-data`

6. 新規データ・ディレクトリーに正しい所有権 (デフォルト {{site.data.keyword.mysql}} ユーザー/グループ、または「my.cnf」グローバル・オプション・ファイルで指定されたユーザー) があることを確認します。不確かな場合は、次のコマンドを使用して、{{site.data.keyword.mysql}} ユーザーおよびグループまでの階層全体を再帰的に所有できます。

  `chown -R mysql:mysql /var/lib/mysql-data`

  **注:** ユーザー {{site.data.keyword.mysql}} は、データベース・フォルダーに対する全権限 (rwx) と、ログ、bin、データ、索引、およびフォームの各ファイルに対する読み取り/書き込み権限が必要です。<br/>
通常、データベース・フォルダーは 700 (drwx------) の権限を持ち、共有ホスティング環境にある間は mysql:mysql の所有権の下にあります。 専用環境では、755 (drwxr-xr-x) を使用して、より自由に権限を構成できます。

7. 「/etc/my.cnf」構成ファイルを更新して、新しいデータ・ディレクトリーを指すようにします。 
  **重要:** 構成ファイルを編集する前に、すべてをバックアップしてください。

  `cp -vp /etc/my.cnf /etc/my.cnf.'date +%s'`<br/>
  `vi /etc/my.cnf`

8. 「/var/lib/mysql」のインスタンスを「/var/lib/mysql-data」に置き換えます。 datadir エントリーがない場合は、[mysqld] スタンザ内に配置してください。

  `[mysqld]`<br/>
  `user = mysql`<br/>
  `datadir = /var/lib/mysql-data`<br/>
  `socket =  /var/lib/mysql-datal/mysql.sock`<br/>

9. 一部のアプリケーションではカスタム構成を使用していますが、この資料では扱うことができません。 データ・ディレクトリーが /var/lib/mysql ではない場合、一部のスクリプトが失敗することが分かっています。 そのため、新しいロケーションを指すためにシンボリック・リンクが使用されています。<!--(first, moving the old data directory out of the way)-->

  `mv -v /var/lib/mysql /var/lib/mysql.orig`<br/>
  `ln -s /var/lib/mysql-data /var/lib/mysql`<br/>

  リンクを作成しない場合は、必ず「php.ini」内の 'mysql.default'_socket と 'mysqli.default'_socket を変更し、Apache を完全に停止してから開始してください。

10. {{site.data.keyword.mysql}} デーモンを開始します。

  `/etc/init.d/mysql start`

11. {{site.data.keyword.mysql}} が動作していることを確認します。If {{site.data.keyword.mysql}} が応答しない場合は、エラー・ログを確認してください。必要に応じて、変更を元に戻してください。

  `mysqladmin ping`
