---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 重設 MySQL root 使用者密碼

如果您需要重設 {{site.data.keyword.mysql}} root 使用者密碼，請完成下列步驟：

1. 將結束 (kill)（非結束 (kill) -9）傳送至 mysqld 伺服器，以關閉 mysqld 伺服器。pid 儲存在 .pid 檔案中，此檔案一般位在 {{site.data.keyword.mysql}} 資料庫目錄中：
  * 範例：`shell> kill cat /your-mysql-data-directory/hostname.pid`
  * 在 Red Hat 中，您也可以停止資料庫：
    * 範例：`shell> service mysqld stop`
    * 您必須是 Unix root 使用者，或伺服器執行以停止資料庫的相同使用者。
2. 使用 --skip-grant-tables 選項，以重新啟動 mysqld。
3. 連接至 mysqld 伺服器：
  * **選項 1：**mysql -h hostname mysql，並使用 GRANT 指令來變更密碼。
    * 如需 GRANT 指令的相關資訊，請參閱 [{{site.data.keyword.mysql}} 文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.mysql.com/doc/G/R/GRANT.html){: new_window}
  * **選項 2：**`shell> mysqladmin -h hostname -u user password 'new password'`
4. 使用 `shell> mysqladmin -h hostname flush-privileges` 或使用 SQL 指令 `mysql> FLUSH PRIVILEGES;`，以載入專用權表格。


**附註：**在您使用 --skip-grant-tables 啟動 mysqld 之後，除非執行 _FLUSH PRIVILEGES_，否則任何使用的 GRANT 指令都會提供 `Unknown command` 錯誤。*
