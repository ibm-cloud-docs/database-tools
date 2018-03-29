---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# エンジニアリング MongoDB の新機能 <!--installations-->

エンジニアリング {{site.data.keyword.mongodb}} のインストール済み環境のパフォーマンスを向上させるために、以下の変更が行われました。 これらの変更は 10gen を使用して、エンジニアリング・サーバーで可能な最良のユーザー・エクスペリエンスを提供しています。 10gen および {{site.data.keyword.cloud}} では、プラットフォーム・ベースとしての機能を果たすために各種の{{site.data.keyword.baremetal_short}}を使用しています。<!--{{site.data.keyword.baremetal_short}} provide a consistent high performance set of available resources that cannot be matched in shared resource, multi-tenant platforms.-->  

* **CentOS 6.X を優先 OS として使用** – 10gen では、{{site.data.keyword.mongodb}} をサポートする最適なパフォーマンスと機能は CentOS オペレーティング・システムで得られることを示しています。 この推奨に基づき、{{site.data.keyword.cloud_notm}} では {{site.data.keyword.mongodb}} を CentOS 6.X プラットフォームにのみデプロイしています。

* **SSD 先読みのデフォルトを 16 ブロックに設定** - SSD ドライブはシーク時間が優れているため、先読みを 16 ブロックに設定できます。 回転ディスクには多少のバッファリングが必要になることがあるため、回転ディスクは 32 ブロックに設定されます。

* **Noatime** - noatime を追加することで、システムは読み取り中のファイルをファイル・システムに書き込む必要がなくなります。これにより、ファイル・アクセスが高速になり、ディスクの摩耗が軽減されます。

* **BIOS での NUMA のオフ** - Linux、NUMA、および {{site.data.keyword.mongodb}} は、連携しない傾向があります。 NUMA ハードウェア上で {{site.data.keyword.mongodb}} を実行する場合は、NUMA をオフにします (インターリーブ・メモリー・ポリシーを使用して稼働する)。一定期間の大幅なスローダウンや高いシステム CPU 時間が発生するなど、予想外の形で問題が明らかになることがあります。

* **Ulimit** – ulimit は、オープン・ファイルの場合は 64,000、ユーザー・プロセスの場合は 32,000 に設定されます。これらの制限は、使用可能なファイル・ハンドルやユーザー・プロセスの不足が原因での障害を防ぐのに役立ちます。

* **EXT4** – Ext3 より優先して Ext4 が選択されます。Ext3 は、ファイルの割り振り (または、ファイルの削除) が低速になる可能性があり、大きいファイル内でのアクセスも低下する可能性があります。

* **別個のジャーナル・ボリューム** – 10gen のアドバイスに基づき、{{site.data.keyword.cloud_notm}} では、ジャーナル用にマウントされた別個の SSD ボリュームを使用しています。 これは、ハイエンドのエンジニアリング・サーバーで使用可能であり、データ・マウント時の読み取り/書き込み操作がジャーナル処理に妨げられないようにします。

* **MMS がプリインストール済み** -  MMS は、すべての {{site.data.keyword.mongodb}} インスタンスに無償で提供される 10gen モニタリング・サービスです。 すべての {{site.data.keyword.cloud_notm}} エンジニアリング・サーバーは MMS エージェントを使用して事前構成されています。
