---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-15"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 配置 Riak 網路

## 概觀

當您在 {{site.data.keyword.Bluemix}} 工程伺服器上安裝 Riak 時，Riak 會連結至[專用網路 IP 位址 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.softlayer.com/about/datacenters/rack-architecture){: new_window}。連結 Riak 時可最小化在部署時公開給大眾使用的開放式可存取 Riak 實例的安全風險。隨時都可以變更連結至 Riak 的 IP 位址。**附註：**Riak 不應該公開開放給沒有其他安全措施的公用介面，而是限制對實例（例如，防火牆及 iptable) 的外部存取。
{:shortdesc}

完成下列步驟，以配置 Riak 網路連結至新的介面。

## 將 Riak 連結至新的介面

1. 移至安裝中 `/etc/riak/app.config` 檔案的 `riak_core` 區段。
2. 更新 `riak_core` 區段中的 `http{}` 屬性，以反映 Riak 所連結的新 IP 位址。<br/>`{http, [ {"127.0.0.1", 8098 } ] },`
3. 在安裝中找出 `/etc/vm.args` 檔案。
4. 編輯 `/etc/vm.args` 檔案內的 `-name` 屬性，以反映新的 IP 位址：<br/>`-name riak@127.0.0.1`
5. 重新啟動 Riak，以完成連結變更。

## 後續步驟

對連結所進行的變更會影響所有先前任何與 Riak 實例相關聯的介面的連結。重新啟動之後，即會更新連結的 IP 位址並且正確運作。如果您重新啟動 Riak 實例，但未導致成功連結，請聯絡[支援中心](/general/support.html)。
