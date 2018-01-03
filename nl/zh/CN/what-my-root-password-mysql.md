---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL 的 root 用户密码是什么？

* 如果服务器是使用 {{site.data.keyword.mysql}} 自动供应的，那么 root 用户密码与服务器 root 用户密码相同。
* 如果在服务器上自动供应了 Plesk，请使用 Plesk 的“admin”和 admin 密码。
* 如果是通过源、RPM 或 up2date 安装的 {{site.data.keyword.mysql}}，那么初始 root 用户帐户密码为空。任何人都无需密码就能以 root 用户身份连接到 {{site.data.keyword.mysql}} 服务器，并且会授予这些用户所有特权，除非已在 {{site.data.keyword.mysql}} 安装期间或之后设置 root 用户密码。
