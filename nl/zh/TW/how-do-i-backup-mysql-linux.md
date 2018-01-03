---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-15"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# 在 Linux 中備份 MySQL

## 從 mysql 目錄中複製

依預設，Linux 伺服器上的 {{site.data.keyword.mysql}} 資料庫會儲存至下列目錄：

`/var/lib/mysql/`

如果您先關閉 mysqld 服務，則可以使用下列指令，將資料庫複製到範例 /backup 目錄：

`cp –Rp /var/lib/mysql/*.* /backup`

cp 指令的 -R 參數表示遞迴，而使用的原因是每一個資料庫都在不同的目錄中。-p 參數是表示許可權，可維護所複製項目的許可權。

一般而言，您會先關閉 mysqld 服務，再使用之前的方法。如果複製正在使用的資料庫，則備份會毀損，並呈現為無用。如果您確定同時未使用任何資料庫，則可以使用之前的指令。

## mysqldump 指令

您可以使用 mysqldump 指令來備份伺服器上的個別資料庫及所有資料庫，而不需要關閉 mysqld 服務。因為這可以製作備份，同時仍保持資料庫上線，所以偏好使用此方法。

## 個別資料庫

以 root 身分登入時，您可以使用下列範例指令，將名稱為 _'example'_ 的資料庫備份到 /backup 目錄：

`mysqldump example > /backup/example_backup.sql`

除非它是小型資料庫，否則建議您接著壓縮資料庫備份，以減少備份傳送時間量。下列指令會壓縮範例資料庫的備份：

`tar czvf /backup/example_backup.tar.gz /backup./example_backup.sql`

## 所有資料庫

如果您有數個要備份的資料庫，則下列指令會將伺服器上的所有 {{site.data.keyword.mysql}} 資料庫都備份到 /backup 目錄：

`mysqldump -A > /backup/databases.sql（或 --all-databases）`

-A 參數（"-all-databases" 執行相同功能）會傾出伺服器上的所有資料庫。
