---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 針對 MySQL，我的 root 密碼為何？

* 如果伺服器已自動佈建 {{site.data.keyword.mysql}}，則 root 密碼與伺服器 root 密碼相同。
* 如果伺服器上已自動佈建 Plesk，則請針對 Plesk 使用 "admin" 及 admin 密碼。
* 如果已透過 source、RPM 或 up2date 安裝 {{site.data.keyword.mysql}}，則起始 root 帳戶密碼會是空的。除非您在 {{site.data.keyword.mysql}} 安裝期間或之後設定 root 密碼，否則任何人都可以使用 root 身分且不需要密碼即連接至 {{site.data.keyword.mysql}} 伺服器，並獲授與所有專用權。
