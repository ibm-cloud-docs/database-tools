---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 開かない MySQL テーブルの修復

{{site.data.keyword.mysql}} テーブルの修復は、ケース・バイ・ケースで処理されますが、デフォルトの {{site.data.keyword.mysql}} テーブル・タイプである MyISAM (別途変更または指定されていない場合のデフォルト・ストレージ・エンジン) を使用している場合は、いくつかの選択肢があります。

1. コマンド・ラインから myisamchk ユーティリティーを実行して、テーブルの検査、修理、または最適化を行うことができます。 これは通常、データベースが稼働していない間に実行されます。 詳しくは、[myisamchk ![バックアップ](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://dev.mysql.com/doc/refman/5.0/en/myisamchk.html){: new_window} を参照してください。
2. mysqlcheck は、myisamchk の機能と似ていますが、これはデータベースの稼働中に実行できます。 詳しくは、[mysqlcheck ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://dev.mysql.com/doc/refman/5.0/en/mysqlcheck.html){: new_window} を参照してください。
3. データベースにログインしている場合は、SQL コマンドを実行して問題を修正できる可能性もあります。

    コマンドの例:
    *mysql> optimize table your-tablename
    *mysql> analyze table your-tablename
    *mysql> repair table your-tablename
    詳しくは、[テーブル保守 SQL ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://dev.mysql.com/doc/refman/5.0/en/table-maintenance-sql.html){: new_window} を参照してください。
4. {{site.data.keyword.mysql}} エラー番号が出されているが、それが何を意味するか分からない場合は、perror ユーティリティーを使用して、コマンド・ラインからエラーを検索できます。 詳しくは、[perror ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://dev.mysql.com/doc/refman/5.0/en/perror.html){: new_window} を参照してください。

    例:
    *shell> perror 13 64
    *Error code 13: Permission denied
    *Error code 64: Machine is not on the network
