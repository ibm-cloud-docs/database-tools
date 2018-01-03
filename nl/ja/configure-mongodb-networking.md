---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MongoDB ネットワーキングの構成

## 概要

{{site.data.keyword.mongodb}} がインストールされた {{site.data.keyword.Bluemix}} エンジニアリング・サーバーは、{{site.data.keyword.mongodb}} をプライベート・ネットワーク IP アドレスにバインドするように構成されています。これは 10gen の推奨によるもので、オープンのアクセス可能な {{site.data.keyword.mongodb}} インスタンスがデプロイメント時にパブリックに公開されることによるセキュリティー・リスクを最小限に抑えるために役立ちます。
{:shortdesc}

## バインドされたインターフェースの変更

インストール・システムの `/etc/mongod.conf` ファイル内の `「bind_ip」` 属性を以下のように変更することで、{{site.data.keyword.mongodb}} をすべてのインターフェースにバインドするように構成できます。

        # mongo.conf
        bind_ip = 0.0.0.0  

この属性では、バインディングの対象をすべてのインターフェースに変更するか、あるいは特定のインターフェースの IP アドレス (デプロイメントの詳細から入手可能) をこのフィールドで設定できます。{{site.data.keyword.mongodb}} インスタンスの再始動が必要です。

**重要:** ファイアウォールや iptables など、インスタンスへのアクセスを制限する他のセキュリティー手段を講じることなく、{{site.data.keyword.mongodb}} をパブリック・インターフェースに公開しないでください。
