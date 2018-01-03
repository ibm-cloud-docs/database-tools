---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 常见问题：MySQL

## 如何监视 MySQL 服务器？

_mytop_ 是一个使用方便的小型 Linux 应用程序，同时也是一个近实时监视器（类似于 UNIX 实用程序“top”），专用于监视 {{site.data.keyword.mysql}} 服务器正在执行的操作。_mytop_ 每若干秒更新一次，以便您可以合理地了解 SQL 性能。_mytop_ 还能够显示大量信息。它还假定您无需密码就能以 root 用户身份来连接到本地主机上的 {{site.data.keyword.mysql}} 服务器。凭证可以在脚本本身或命令行中进行更改。


## MySQL 的 root 用户密码是什么？

* 如果服务器是使用 {{site.data.keyword.mysql}} 自动供应的，那么 root 用户密码与服务器 root 用户密码相同。
* 如果在服务器上自动供应了 Plesk，请使用 Plesk 的“admin”和 admin 密码。
* 如果是通过源、RPM 或 up2date 安装的 {{site.data.keyword.mysql}}，那么初始 root 用户帐户密码为空。任何人都无需密码就能以 root 用户身份连接到 {{site.data.keyword.mysql}} 服务器，并且会授予这些用户所有特权，除非已在 {{site.data.keyword.mysql}} 安装期间或之后设置 root 用户密码。

## 获取 MySQL 相关信息的最佳联机资源是什么？

[{{site.data.keyword.mysql}} Web 站点 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://dev.mysql.com/doc/){: new_window} 上有完整的参考手册并提供了搜索功能。

该文档涵盖从基本安装、SQL 语法一直到复制和集群等高级用法的所有内容。此外还有德语、法语、日语、葡萄牙语和俄语翻译版本的参考手册。
