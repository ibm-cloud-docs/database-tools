---
copyright:
  years: 1994, 2017
lastupdated: "2017-06-08"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MongoDB

MongoDB 是功能完整的 NoSQL 伺服器，可水平擴充以符合企業級資料庫服務需求。MongoDB 可以免費訂購，或使用 OS 重新載入予以要求。支援下列作業系統：

* CentOS 6.x
* RHEL 6.x
* Ubuntu 12.04
* Debian 6.x

在佈建 SL-MongoDB 安裝時，有一些需要注意的項目：

* 依預設，Mongod（MongoDB 服務）只會連結至專用網路介面。MongoDB 會佈建一個預先配置的管理使用者。使用者名稱是 'admin'，而密碼與伺服器 root 密碼相同。
* 如果您是要訂購「MongoDB 解決方案」（例如抄本集叢集），則會在叢集配置處理程序結束時，在解決方案的所有 MongoDB 伺服器上設定 admin 密碼。

如需 MongoDB 的相關資訊，請參閱下列鏈結：

* [MongoDB 文件庫](http://www.mongodb.org/display/DOCS/Home)
* [MongoDB 討論區及開放程式碼支援](https://groups.google.com/forum/?fromgroups#!forum/mongodb-user)
* [Karl Seguin 的 The Little Mongo DB Book (PDF)](http://openmymind.net/mongodb.pdf)

## 如何做？

* [配置 MongoDB 網路](configure-mongodb-networking.html)
* [設定 MongoDB 解決方案的 MongoDB Monitoring Service (MMS)](set-mongodb-monitoring-service-mms-mongodb-solution.html)
