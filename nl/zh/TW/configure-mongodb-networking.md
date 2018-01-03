---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 配置 MongoDB 網路

## 概觀

已將安裝 {{site.data.keyword.mongodb}} 的 {{site.data.keyword.Bluemix}} 工程伺服器配置成讓 {{site.data.keyword.mongodb}} 連結至專用網路 IP 位址。這是 10gen 的建議，其作用是最小化在部署時公開給大眾使用的開放式可存取 {{site.data.keyword.mongodb}} 實例的安全風險。
{:shortdesc}

## 變更連結的介面

在安裝的 `/etc/mongod.conf` 檔案中變更 `‘bind_ip’` 屬性，即可以將 {{site.data.keyword.mongodb}} 配置成連結至任何介面，如下所示：

        # mongo.conf
        bind_ip = 0.0.0.0  

此屬性會變更所有介面上的連結，或者，您可以在此欄位中設定特定介面的 IP 位址（可從部署詳細資料取得）。需要重新啟動 {{site.data.keyword.mongodb}} 實例。

**重要事項：**不要將 {{site.data.keyword.mongodb}} 公開到沒有一些其他安全措施的公用介面（例如限制實例存取的防火牆或 iptable）。
