---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 在 Unix 類似環境中變更 MySQL 資料目錄

請遵循下列步驟來變更 {{site.data.keyword.mysql}} 資料目錄：

1. 使用 [PuTTY ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html){: new_window} 或偏好的用戶端，來登入伺服器。

  **附註：**如果您是使用資料目錄的專用分割區，請務必在複製資料之後裝載新分割區來取代原始資料目錄。裝載新的分割區以儲存部分應用程式可能無法處理的非標準配置變更。

2. 關閉 mysqld（{{site.data.keyword.mysql}} 常駐程式/伺服器）。在不同的作業系統與配送之間，啟動及停止常駐程式的處理程序可能會不同。

  **附註：**在任何直接影響原始檔案的處理程序期間，必須停止 {{site.data.keyword.mysql}}。

  `/etc/init.d/mysql stop`
  或
  `/etc/init.d/mysqld, /etc/init.d/mysql-server, /usr/loca/etc/init.d/mysql, /opt/lamp…`

3. 先備份資料庫，再進行任何變更。請確定，當您直接複製原始資料庫檔案時，{{site.data.keyword.mysql}} 常駐程式未執行。

  如果您在伺服器上使用 cPanel，請先停止 cPanel（主要是 TailWatch/chkservd），再重新啟動常駐程式。您可以建立暫存檔 `/etc/chkserv.d/mysqlisevil`，來停止 'chkservd' 重新啟動服務。如果您不熟悉 rsync，則可以使用任何其他工具來建立備份（例如 cp、cpio 或 tar）。

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql.'date +%s'`

4. 建立資料目錄，並提供 {{site.data.keyword.mysql}} 使用者（或 'my.cnf' 廣域選項檔案中指定的任何使用者）所有權。在此範例中，使用位置 `/var/lib/mysql-data`，但您可以使用任何想要的位置。如果您要特別針對此用途新增磁碟/邏輯裝置，則還需要先將項目新增至 `/etc/fstab`，並裝載目錄，再繼續進行。

  `chown mysql:mysql /var/lib/mysql-data`

5. 製作原始目錄到新 {{site.data.keyword.mysql}} 資料目錄的最終副本（請務必在第一個目錄的結尾，保留尾端的 /）：

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql-data`

6. 確定新的資料目錄具有正確的所有權（預設 {{site.data.keyword.mysql}} 使用者/群組，或 'my.cnf' 廣域選項檔案中所指定的使用者）。如果不確定，您可以使用下列指令來遞迴地擁有 {{site.data.keyword.mysql}} 使用者及群組的整個階層。

  `chown -R mysql:mysql /var/lib/mysql-data`

  **附註：**使用者 {{site.data.keyword.mysql}} 需要具有資料庫資料夾的完整許可權 (rwx)，以及日誌、bin、資料、索引及表單檔案的讀寫許可權。<br/>
一般而言，資料庫資料夾具有許可權 700 (drwx------)，而且位在共用主機環境時，是由 mysql:mysql 所擁有。在專用環境中，許可權可以更寬鬆地配置為 755 (drwxr-xr-x)。

7. 更新 '/etc/my.cnf' 配置檔，以將它指向新的資料目錄。**重要事項：**請先備份所有項目，再對配置檔進行任何編輯。

  `cp -vp /etc/my.cnf /etc/my.cnf.'date +%s'`<br/>
  `vi /etc/my.cnf`

8. 將任何 '/var/lib/mysql' 實例取代為 '/var/lib/mysql-data'。如果您沒有 datadir 項目，則請將它放在 [mysqld] 段落內。

  `[mysqld]`<br/>
  `user = mysql`<br/>
  `datadir = /var/lib/mysql-data`<br/>
  `socket =  /var/lib/mysql-datal/mysql.sock`<br/>

9. 部分應用程式具有自訂配置，而此文件無法涵蓋它們。如果資料目錄不是 /var/lib/mysql，則已知部分 Script 會失敗。因此，符號鏈結是用來指向新的位置。<!--(first, moving the old data directory out of the way)-->

  `mv -v /var/lib/mysql /var/lib/mysql.orig`<br/>
  `ln -s /var/lib/mysql-data /var/lib/mysql`<br/>

  如果您不要建立鏈結，請務必變更 'php.ini' 中的 'mysql.default'_ socket 及 'mysqli.default'_ socket，並完全停止及啟動 apache。

10. 啟動 {{site.data.keyword.mysql}} 常駐程式。

  `/etc/init.d/mysql start`

11. 驗證 {{site.data.keyword.mysql}} 正常運作。如果 {{site.data.keyword.mysql}} 未回應，請檢閱錯誤日誌。必要的話，請回復變更。

  `mysqladmin ping`
