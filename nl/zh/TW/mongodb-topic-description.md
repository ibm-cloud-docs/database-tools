---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-15"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MongoDB

{{site.data.keyword.mongodb}} 是功能完整的 NoSQL 伺服器，可水平擴充以符合企業級資料庫服務需求。{{site.data.keyword.mongodb}} 可以在 {{site.data.keyword.BluSoftlayer_full}} 購物車中免費訂購，或使用 OS 重新載入予以要求。目前支援下列作業系統：

* CentOS 6.x
* RHEL 6.x
* Ubuntu 12.04
* Debian 6.x

SL-MongoDB 安裝的注意事項：

* 依預設，Mongod（{{site.data.keyword.mongodb}} 服務）只會連結至專用網路介面。{{site.data.keyword.mongodb}} 會佈建一個預先配置的管理使用者。使用者名稱是 _admin_，而密碼與伺服器 root 密碼相同。
* 如果您訂購「{{site.data.keyword.mongodb}} 解決方案」（例如抄本集叢集），則會在叢集配置處理程序結束時，在解決方案的所有 {{site.data.keyword.mongodb}} 伺服器上設定 admin 密碼。

如需 {{site.data.keyword.mongodb}} 的相關資訊，請參閱下列鏈結： 

* [{{site.data.keyword.mongodb}} 文件庫 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.mongodb.org/display/DOCS/Home){: new_window}
* [{{site.data.keyword.mongodb}} 討論區及開放程式碼支援 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://groups.google.com/forum/?fromgroups#!forum/mongodb-user){: new_window}
* [Karl Seguin 的 The Little Mongo DB Book (PDF) ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://openmymind.net/mongodb.pdf){: new_window}
