---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 修復未開啟的 MySQL 表格

{{site.data.keyword.mysql}} 表格修復是依個案處理，但如果您是使用預設 {{site.data.keyword.mysql}} 表格類型 MyISAM（除非變更或指定不同的表格類型，否則這是預設儲存空間引擎），則會有一些選項。

1. 您可以從指令行執行 myisamchk 公用程式來檢查、修復或最佳化表格。它在資料庫未執行時可正常執行。如需相關資訊，請參閱 [myisamchk ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://dev.mysql.com/doc/refman/5.0/en/myisamchk.html){: new_window}。
2. mysqlcheck 的功能與 myisamchk 類似，但它可以在資料庫執行時執行。如需相關資訊，請參閱 [mysqlcheck ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://dev.mysql.com/doc/refman/5.0/en/mysqlcheck.html){: new_window}。
3. 如果您登入資料庫，則也可以執行可修正問題的 SQL 指令。

    範例指令：
    *mysql> optimize table your-tablename
    *mysql> analyze table your-tablename
    *mysql> repair table your-tablename
    如需相關資訊，請參閱[表格維護 SQL ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://dev.mysql.com/doc/refman/5.0/en/table-maintenance-sql.html){: new_window}。
4. 如果您是取得 {{site.data.keyword.mysql}} 錯誤號碼，但不確定它們是什麼，則可以從指令行執行 perror 公用程式來查閱錯誤。如需相關資訊，請參閱 [perror ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://dev.mysql.com/doc/refman/5.0/en/perror.html){: new_window}。

    Examples:
    *shell> perror 13 64
    *Error code 13: Permission denied
    *Error code 64: Machine is not on the network
