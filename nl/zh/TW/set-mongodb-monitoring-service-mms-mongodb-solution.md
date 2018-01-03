---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# 設定 MongoDB Monitoring Service (MMS)

## 概觀

在完成 {{site.data.keyword.mongodb}} 解決方案之後，可以設定抄本集中的主機，以使用 10gen 的免費 {{site.data.keyword.mongodb}} Monitoring Service (MMS)。您可以使用此監視服務來查看已抄寫資料庫的詳細技術分析。您需要有 MMS API 金鑰及秘密金鑰才能開始使用，這些金鑰是透過在 [10gen MMS 登錄網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.10gen.com/mongodb-monitoring-service){: new_window} 上登錄帳戶而取得。
{:shortdesc}

**附註：**如果您在訂購 {{site.data.keyword.mongodb}} 解決方案時已輸入 MMS 金鑰或新 MMS 帳戶資訊，則可能已設定這些 MMS 認證。

您可以在 [10gen MMS 網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://mms.10gen.com/){: new_window} 中找到帳戶的 MMS API 金鑰及秘密金鑰。請使用提供的認證來登入，然後選取**設定**來顯示 MMS 群組的 **API 金鑰**及**秘密金鑰**。

## 配置主機

您需要先更新主機上的 API 金鑰及秘密金鑰，才能配置 MMS。**附註：**只需要在集合的單一主機上執行這些步驟。不過，您可以在多個主機上執行相同的步驟，以啟用失效接手備份 MMS 代理程式。集合中只有一個代理程式可以與 MMS 服務溝通資訊。

1. 對解決方案中的其中一個主機進行 SSH（在 {{site.data.keyword.slportal_full}} 中可以找到網址及認證）。
2. 執行下列指令，並替換適當的 API 及秘密金鑰。

    `# /opt/local/bin/mongoConfigureAuthentication.sh -a -s`

    `Updating the /opt/local/10gen/mms-agent/settings.py file with the`
    `MMS API/secret keys...`

    `Restarting MMS agent...`

    `Shutting down MMS-agent:                                   [  OK  ]`

    `Starting MMS-agent:                                        [  OK  ]`


## 配置 MMS 群組

在配置主機並重新啟動 MMS 代理程式之後，您需要在 10gen MMS 網站上重新啟動 MMS 群組。

1. 登入 [10gen MMS 網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://mms.10gen.com/){: new_window}。
2. 選取**主機 > 代理程式**。
3. 驗證已配置的代理程式在清單中。已配置及重新啟動的每一個項目都會列出一個代理程式。
4. 若要將主機新增至清單，請選取**主機**，然後按一下**加號 (+)**。
5. 輸入主機的*專用 IP 位址*，以及 {{site.data.keyword.mongodb}} 的埠號。SoftLayer MongoDB 解決方案的預設埠號是 27018。
6. 輸入資料庫管理者使用者名稱及密碼（這些可以在 {{site.data.keyword.slportal}} 中於裝置的**密碼**中找到），然後選取**新增**。
  * **重要事項：**這些是必要認證。

**附註：**最多需要 30 分鐘，資料才會顯示在 MMS 中。
