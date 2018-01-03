---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-15"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MongoDB

{{site.data.keyword.mongodb}} エンタープライズ・クラスのデータベース・サービスのニーズに対応するために水平に拡張可能なフル機能の NoSQL サーバーです。{{site.data.keyword.mongodb}} は、{{site.data.keyword.BluSoftlayer_full}} のショッピング・カートから無償で注文するか、OS 再ロードを使用して要求することができます。現時点では、以下のオペレーティング・システムがサポートされています。

* CentOS 6.x
* RHEL 6.x
* Ubuntu 12.04
* Debian 6.x

SL-MongoDB のインストールに関する注意事項は、以下のとおりです。

* デフォルトでは、Mongod ({{site.data.keyword.mongodb}} サービス) はプライベート・ネットワーク・インターフェースにのみバインドされます。{{site.data.keyword.mongodb}} は、事前構成された管理ユーザーによってプロビジョンされます。ユーザー名は _admin_ で、パスワードはサーバー・ルート・パスワードと同じです。
* レプリカ・セット・クラスターなどの {{site.data.keyword.mongodb}} ソリューションを注文する場合、管理者パスワードはクラスター構成プロセスの最後に、ソリューションのすべての {{site.data.keyword.mongodb}} サーバーで設定されます。

{{site.data.keyword.mongodb}} について詳しくは、は、以下のリンクを参照してください。 

* [{{site.data.keyword.mongodb}} 資料ライブラリー ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.mongodb.org/display/DOCS/Home){: new_window}
* [{{site.data.keyword.mongodb}} フォーラムおよびオープン・ソース・サポート ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://groups.google.com/forum/?fromgroups#!forum/mongodb-user){: new_window}
* [Karl Seguin の「The Little Mongo DB Book」(PDF) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://openmymind.net/mongodb.pdf){: new_window}
