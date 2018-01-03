---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL 安全性最佳作法

## 概觀

許多 {{site.data.keyword.BluSoftlayer_full}} 使用者都依賴 {{site.data.keyword.mysql}} 來進行其資料庫解決方案。因為資料庫內含各種重要資訊，而且有時還包含機密性資訊，所以建議您保護 {{site.data.keyword.mysql}} 資料庫安全，以保護資訊。{{site.data.keyword.mysql}} 的安全作法取決於個別需求及商業需求；不過，有一些建議開始使用的最佳作法。請確定您遵循下列提示來取得保護 {{site.data.keyword.mysql}} 資料庫安全的起點。

* 設定 root {{site.data.keyword.mysql}} 密碼。
* 刪除在起始安裝 {{site.data.keyword.mysql}} 期間所建立的測試帳戶及資料庫。
* 確定已設定每一個個別 {{site.data.keyword.mysql}} 帳戶密碼。
* 視需要授與專用權。請避免不必要地授與廣域專用權。
* 不要在與帳戶相關聯的主機名稱值中使用[萬用字元 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://en.wikipedia.org/wiki/Wildcard_character){: new_window}。
* 定期檢閱帳戶的 {{site.data.keyword.mysql}} 使用者及資料庫，以確定許可權保持正確。
* 不要在具有指令 `shell>mysql -u root - password=somepassword mysql` 的指令行中使用密碼。

**附註：**使用下列指令來授與具有指令行存取的任何其他使用者，以使用指令 `shell>ps` 來取回密碼。系統提示輸入密碼時，請改用指令 `shell>mysql -u root -p mysql`。這會保護密碼安全。

## 其他資源

有各種資源會提供用來保護 {{site.data.keyword.mysql}} 資料庫安全的其他詳細資料。建議開始使用起始於您裝置上 {{site.data.keyword.mysql}} 版本的 {{site.data.keyword.mysql}} 安全準則：

* [{{site.data.keyword.mysql}} 5.7 版 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://dev.mysql.com/doc/refman/5.7/en/security.html){: new_window}

有各種 {{site.data.keyword.mysql}} 未管理但有用的額外資源。使用任何搜尋引擎搜尋「{{site.data.keyword.mysql}} 安全」，即可找到這些資源。因為 {{site.data.keyword.mysql}} 製作者不會維護協力廠商資源，所以請小心執行這些作法。與使用所有資源一樣，請使用授信網站，並參照正式文件及支援網站（盡可能）。
