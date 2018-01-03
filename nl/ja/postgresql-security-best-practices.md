---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# PostgreSQL セキュリティーのベスト・プラクティス

## 概要

多くの {{site.data.keyword.BluSoftlayer_full}} ユーザーは、データベース・ソリューションを {{site.data.keyword.mysql}} に依存しています。データベースには、各種の重要な情報や、ときには機密性の高い情報が格納されているため、{{site.data.keyword.mysql}} データベースをセキュアに維持し、情報を保護することが推奨されます。{{site.data.keyword.mysql}} のセキュリティーの実施は、個々のニーズおよびビジネス要件によって異なります。ただし、始めに推奨されるベスト・プラクティスがあります。必ず、以下のヒントに従って、{{site.data.keyword.mysql}} データベースをセキュアな状態で始められるようにしてください。
{:shortdesc}

* ルート {{site.data.keyword.mysql}} パスワードを設定します。
* {{site.data.keyword.mysql}} の初期インストール中に作成されたテスト・アカウントとデータベースを削除します。
* 個々の {{site.data.keyword.mysql}} アカウントのパスワードが設定されていることを確認します。
* 必要に応じて、特権を付与します。不必要にグローバル特権を付与しないでください。
* アカウントに関連付けられたホスト名の値には、[ワイルドカード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://en.wikipedia.org/wiki/Wildcard_character){: new_window} を使用しないでください。
* アカウントの {{site.data.keyword.mysql}} ユーザーおよびデータベースを定期的に検討し、許可が正確に保たれていることを確認します。

## 追加リソース

この他にも、役に立つ可能性のある、{{site.data.keyword.mysql}} 管理対象外のさまざまな追加リソースがあります。こうしたリソースは、検索エンジンを使用して「{{site.data.keyword.mysql}} セキュリティー」を検索することで見つかります。サード・パーティーのリソースは {{site.data.keyword.mysql}} の製造元によって保守されていないため、十分に注意して使用する必要があります。あらゆるリソースと同様に、信頼できるサイトを使用し、可能な限り公式サイトの資料およびサポートを参照してください。
