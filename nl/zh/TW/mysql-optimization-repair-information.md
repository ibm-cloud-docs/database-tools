---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL 最佳化/修復資訊

## MySQL 如何使用記憶體 
下列是 mysqld 伺服器使用記憶體的一些方法，以及關聯的 mysqld 變數名稱。
* [記憶體使用 MySQL 5.0 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://dev.mysql.com/doc/refman/5.0/en/memory-use.html){: new_window}
* [記憶體使用 MySQL 4.1 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://dev.mysql.com/doc/refman/4.1/en/memory-use.html){: new_window}

## 「MySQL 最佳化」涵蓋下列項目：
- 最佳化概觀
- 最佳化 SELECT 及其他陳述式
- 鎖定問題
- 最佳化資料庫結構
- 最佳化 MySQL Server
- 磁碟問題

[最佳化 MySQL 5.0 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://dev.mysql.com/doc/refman/5.0/en/optimization.html){: new_window}
[最佳化 MySQL 4.1 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://dev.mysql.com/doc/refman/4.1/en/optimization.html){: new_window}

## MySQL Server 變數 - SQL 層或「儲存空間引擎」特有。
下列鏈結列出一些較常用的變數。
[移至文章 1 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.mysqlperformanceblog.com/2006/06/08/mysql-server-variables-sql-layer-or-storage-engine-specific/){: new_window}
[移至文章 2 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://forge.mysql.com/wiki/ServerVariables){: new_window}

## 由 Ian Gilfillan 最佳化 mysqld 變數
請參閱這篇有關 MySQL 最佳化的文章（包括設定 mysqld 伺服器變數的一些準則）
（key_buffer_size、查詢快取變數、table_cache、sort_buffer 等）。
[移至文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.databasejournal.com/features/mysql/article.php/3367871){: new_window}

## 由 Ian Gilfillan 修復 MySQL 中的資料庫毀損
當您使用 {{site.data.keyword.mysql}} 時，表格毀損十分罕見。不過，它有助於瞭解在發生時如何修正問題。
[移至文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.databasejournal.com/features/mysql/article.php/3300511){: new_window}

## 最佳化 MySQL：Ian Gilfillan 的查詢及索引
<!--The database is too slow. Queries are queuing up, backlogs growing, users being refused connection. Management is ready to spend millions on "upgrading" to some other system, when the problem is really that MySQL is simply not being used properly. Badly defined or non-existent indexes are one of the primary reasons for poor performance, and fixing these can often lead to phenomenal improvements.-->
[移至文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.databasejournal.com/features/mysql/article.php/1382791){: new_window}

[Ian Gilfillan 的其他 {{site.data.keyword.mysql}} 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.databasejournal.com/article.php/1474351){: new_window}
