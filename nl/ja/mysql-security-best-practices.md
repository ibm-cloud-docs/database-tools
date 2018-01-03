---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL セキュリティーのベスト・プラクティス

## 概要

多くの {{site.data.keyword.BluSoftlayer_full}} ユーザーは、データベース・ソリューションを {{site.data.keyword.mysql}} に依存しています。データベースには、各種の重要な情報や、ときには機密性の高い情報が格納されているため、{{site.data.keyword.mysql}} データベースをセキュアに維持し、情報を保護することが推奨されます。{{site.data.keyword.mysql}} のセキュリティーの実施は、個々のニーズやビジネス要件によって異なりますが、始めに推奨されるベスト・プラクティスがあります。必ず、以下のヒントに従って、{{site.data.keyword.mysql}} データベースをセキュアな状態で始められるようにしてください。

* ルート {{site.data.keyword.mysql}} パスワードを設定します。
* {{site.data.keyword.mysql}} の初期インストール中に作成されたテスト・アカウントとデータベースを削除します。
* 個々の {{site.data.keyword.mysql}} アカウントのパスワードが設定されていることを確認します。
* 必要に応じて、特権を付与します。不必要にグローバル特権を付与しないでください。
* アカウントに関連付けられたホスト名の値には、[ワイルドカード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://en.wikipedia.org/wiki/Wildcard_character){: new_window} を使用しないでください。
* アカウントの {{site.data.keyword.mysql}} ユーザーおよびデータベースを定期的に検討し、許可が正確に保たれていることを確認します。
* コマンド・ラインでコマンド `shell>mysql -u root - password=somepassword mysql` を使用して、パスワードを指定しないでください。

**注:** 以下のコマンドを使用して他のユーザーにコマンド・ライン・アクセス権限を付与し、コマンド `shell>ps` を使用してパスワードをプルするようにします。代わりに、コマンド `shell>mysql -u root -p mysql` を使用して、パスワードの入力を求めるプロンプトが出されるようにします。これにより、パスワードが保護されます。

## 追加リソース

{{site.data.keyword.mysql}} データベースの保護について詳しい情報を提供するさまざまなリソースがあります。最初に、ご使用のデバイス上の {{site.data.keyword.mysql}} のバージョンに基づいた {{site.data.keyword.mysql}} セキュリティー・ガイドラインを使用することをお勧めします。

* [{{site.data.keyword.mysql}} バージョン 5.7 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://dev.mysql.com/doc/refman/5.7/en/security.html){: new_window}

この他にも、役に立つ可能性のある、{{site.data.keyword.mysql}} 管理対象外のさまざまな追加リソースがあります。こうしたリソースは、検索エンジンを使用して「{{site.data.keyword.mysql}} セキュリティー」を検索することで見つかります。サード・パーティーのリソースは {{site.data.keyword.mysql}} の製造元によって保守されていないため、十分に注意して使用する必要があります。あらゆるリソースと同様に、信頼できるサイトを使用し、可能な限り公式サイトの資料およびサポートを参照してください。
