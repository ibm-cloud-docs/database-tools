---
copyright:
  years: 1994, 2017
lastupdated: "2017-06-08"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MongoDB

MongoDB は、エンタープライズ・クラスのデータベース・サービスのニーズに対応するために水平に拡張可能なフル機能の NoSQL サーバーです。MongoDB は、無償で注文するか、OS 再ロードを使用して要求することができます。以下のオペレーティング・システムがサポートされています。



* CentOS 6.x
* RHEL 6.x
* Ubuntu 12.04
* Debian 6.x

SL-MongoDB のインストールのプロビジョンを行う際に、以下の項目に注意してください。

* デフォルトでは、Mongod (MongoDB サービス) はプライベート・ネットワーク・インターフェースにのみバインドされます。MongoDB は、事前構成された管理ユーザーによってプロビジョンされます。ユーザー名は「admin」で、パスワードはサーバー・ルート・パスワードと同じです。
* レプリカ・セット・クラスターなどの MongoDB ソリューションを注文する場合、管理者パスワードはクラスター構成プロセスの最後に、ソリューションのすべての MongoDB サーバーで設定されます。

MongoDB について詳しくは、以下のリンクを参照してください。

* [MongoDB 資料ライブラリー](http://www.mongodb.org/display/DOCS/Home)
* [MongoDB フォーラムおよびオープン・ソース・サポート](https://groups.google.com/forum/?fromgroups#!forum/mongodb-user)
* [Karl Seguin の「The Little Mongo DB Book」(PDF)](http://openmymind.net/mongodb.pdf)

## 操作方法

* [MongoDB ネットワーキングの構成](configure-mongodb-networking.html)
* [MongoDB ソリューションの MongoDB モニタリング・サービス (MMS) のセットアップ](set-mongodb-monitoring-service-mms-mongodb-solution.html)
