---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL 最適化/修復情報

## MySQL のメモリーの使用方法 
以下に、mysqld サーバーがメモリーを使用する方法と関連の mysqld 変数名をいくつか示します。
* [MySQL 5.0 のメモリーの使用 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://dev.mysql.com/doc/refman/5.0/en/memory-use.html){: new_window}
* [MySQL 4.1 のメモリーの使用 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://dev.mysql.com/doc/refman/4.1/en/memory-use.html){: new_window}

## MySQL 最適化では、以下の項目が扱われています。
- 最適化の概要
- SELECT およびその他のステートメントの最適化
- ロック問題
- データベース構造の最適化
- MySQL サーバーの最適化
- ディスク問題

[MySQL 5.0 の最適化![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://dev.mysql.com/doc/refman/5.0/en/optimization.html){: new_window}
[MySQL 4.1 の最適化![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://dev.mysql.com/doc/refman/4.1/en/optimization.html){: new_window}

## MySQL サーバー変数 - SQL 層またはストレージ・エンジン固有。
以下のリンクには、一般的な変数がいくつかリストされています。
[記事 1 にアクセス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.mysqlperformanceblog.com/2006/06/08/mysql-server-variables-sql-layer-or-storage-engine-specific/){: new_window}
[記事 2 にアクセス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://forge.mysql.com/wiki/ServerVariables){: new_window}

## mysqld 変数の最適化 (Ian Gilfillan 著)  
MySQL 最適化に関するこの記事を参照してください。mysqld サーバー変数 (key_buffer_size、Query cache variables、table_cache、sort_buffer など) の設定に関するガイドラインがいくつか含まれています。
[記事にアクセス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.databasejournal.com/features/mysql/article.php/3367871){: new_window}

## MySQL 内のデータベース破壊の修復 (Ian Gilfillan 著) 
{{site.data.keyword.mysql}} の使用時にテーブルが破損するのはまれです。しかし、発生した場合に問題を修正する方法を知っておくと役立ちます。
[記事にアクセス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.databasejournal.com/features/mysql/article.php/3300511){: new_window}

## MySQL: 照会および索引の最適化 (Ian Gilfillan 著)
<!--The database is too slow. Queries are queuing up, backlogs growing, users being refused connection. Management is ready to spend millions on "upgrading" to some other system, when the problem is really that MySQL is simply not being used properly. Badly defined or non-existent indexes are one of the primary reasons for poor performance, and fixing these can often lead to phenomenal improvements.-->
[記事にアクセス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.databasejournal.com/features/mysql/article.php/1382791){: new_window}

[その他の {{site.data.keyword.mysql}} 記事 (Ian Gilfillan 著) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.databasejournal.com/article.php/1474351){: new_window}
