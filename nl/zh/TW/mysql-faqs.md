---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 常見問題：MySQL

## 如何監視 MySQL 伺服器？

_mytop_ 這個隨手可得的小型 Linux 應用程式是一種接近即時的監視器（與 UNIX 公用程式 'top' 類似），可特別查看 {{site.data.keyword.mysql}} 伺服器正在執行的作業。_mytop_ 會每隔幾秒更新一次，因此您可以適當地查看 SQL 效能。_mytop_ 也可以顯示大量資訊。它也假設您是使用 root 使用者身分連線至 localhost 上的 {{site.data.keyword.mysql}} 伺服器，且未使用密碼。您可以在 Script 本身中或指令行上變更認證。


## 針對 MySQL，我的 root 密碼為何？

* 如果伺服器已自動佈建 {{site.data.keyword.mysql}}，則 root 密碼與伺服器 root 密碼相同。
* 如果伺服器上已自動佈建 Plesk，則請針對 Plesk 使用 "admin" 及 admin 密碼。
* 如果已透過 source、RPM 或 up2date 安裝 {{site.data.keyword.mysql}}，則起始 root 帳戶密碼會是空的。除非您在 {{site.data.keyword.mysql}} 安裝期間或之後設定 root 密碼，否則任何人都可以使用 root 身分且不需要密碼即連接至 {{site.data.keyword.mysql}} 伺服器，並獲授與所有專用權。

## MySQL 相關資訊的最佳線上資源為何？

[{{site.data.keyword.mysql}} 網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://dev.mysql.com/doc/){: new_window} 具有含可用搜尋功能的完整參照手冊。

此文件涵蓋從基本安裝、SQL 語法到進階用法（例如抄寫及叢集）的所有內容。此外，也提供德文、法文、日文、葡萄牙文及俄文版參照手冊的翻譯版本。
