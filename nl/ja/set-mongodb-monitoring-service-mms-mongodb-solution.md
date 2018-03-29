---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MongoDB モニタリング・サービス (MMS) のセットアップ

{{site.data.keyword.mongodb}} ソリューションの完了後、レプリカ・セット内のホストを 10gen の無償の {{site.data.keyword.mongodb}} モニタリング・サービス (MMS) と連携するようにセットアップできます。 このモニタリング・サービスを使用すると、複製されたデータベースの詳細な技術分析を確認できます。 開始するには、MMS の API キーと秘密鍵が必要です。これは、[10gen MMS 登録 Web サイト ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.10gen.com/mongodb-monitoring-service){: new_window} でアカウントを登録して取得します。
{:shortdesc}

**注:** {{site.data.keyword.mongodb}} ソリューションの注文時に MMS キーまたは新規 MMS アカウント情報を入力した場合、これらの MMS 資格情報は既にセットアップされている可能性があります。

MMS の API キーとアカウントの秘密鍵は、[10gen MMS Web サイト ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://mms.10gen.com/){: new_window} にあります。 提供された資格情報を使用してログインし、**「設定」**を選択すると、MMS グループの **API キー**と**秘密鍵**が示されます。

## ホストの構成

MMS を構成する前に、ホスト上で API キーと秘密鍵を更新する必要があります。 **注:** 以下の手順は、セット内の単一ホストで実行するだけで済みます。 ただし、同じステップを複数のホストで実行して、フェイルオーバー・バックアップ MMS エージェントを有効にすることができます。 セット内の 1 つのエージェントのみが MMS サービスに情報を通信します。

1. SSH 経由でソリューション内のいずれかのホストに接続します (ネットワーク・アドレスと資格情報は {{site.data.keyword.slportal_full}} にあります)。
2. 以下のコマンドを、適切な API キーと秘密鍵に置き換えて実行します。

    `# /opt/local/bin/mongoConfigureAuthentication.sh -a -s`

    `Updating the /opt/local/10gen/mms-agent/settings.py file with the`
    `MMS API/secret keys...`

    `Restarting MMS agent...`

    `Shutting down MMS-agent:                                   [  OK  ]`

    `Starting MMS-agent:                                        [  OK  ]`


## MMS グループの構成

ホストを構成し、MMS エージェントを再始動した後、10gen MMS Web サイトで MMS グループを再始動する必要があります。

1. [10gen MMS Web サイト ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://mms.10gen.com/){: new_window} にログインします。
2. **「Hosts」>「Agent」**を選択します。
3. 構成されたエージェントがリストに含まれていることを確認します。 構成されて再始動されるごとに、1 つのエージェントがリストされます。
4. ホストをリストに追加するには、**「Hosts」**を選択して、**「プラス (+)」**をクリックします。
5. ホストの*プライベート IP アドレス* と {{site.data.keyword.mongodb}} のポート番号を入力します。 SoftLayer MongoDB ソリューションのデフォルトのポート番号は 27018 です。
6. データベース管理者のユーザー名とパスワード (これは、{{site.data.keyword.slportal}}内のデバイス**「パスワード」**にあります) を入力し、**「追加」**を選択します。
  * **重要:** これらの資格情報は必須です。

**注:** データが MMS に表示されるまでに最大 30 分かかることがあります。
