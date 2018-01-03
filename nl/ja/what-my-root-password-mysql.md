---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL のルート・パスワードは何ですか

* サーバーが {{site.data.keyword.mysql}} を使用して自動プロビジョンされた場合、ルート・パスワードはサーバー・ルート・パスワードと同じです。
* サーバー上で Plesk が自動プロビジョンされた場合、「admin」と Plesk の管理パスワードを使用します。
* source、RPM、または up2date を使用して {{site.data.keyword.mysql}} をインストールした場合、初期 root アカウント・パスワードは空です。{{site.data.keyword.mysql}} のインストール中またはインストール後にルート・パスワードを設定しない限り、すべてのユーザーがパスワードなしに root として {{site.data.keyword.mysql}} サーバーに接続することができ、すべての特権が付与されます。
