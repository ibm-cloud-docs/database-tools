---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# PostgreSQL 安全性最佳做法

## 概述

许多 {{site.data.keyword.BluSoftlayer_full}} 用户依赖 {{site.data.keyword.mysql}} 来实现其数据库解决方案。由于数据库中保存着各种重要信息，有时甚至是敏感信息，因此建议您确保 {{site.data.keyword.mysql}} 数据库安全以保护您的信息。{{site.data.keyword.mysql}} 的安全做法取决于个人需要和业务需求。不过，建议您从最佳做法开始。请确保遵循以下提示，为确保 {{site.data.keyword.mysql}} 数据库安全开个好头。
{:shortdesc}

* 设置 root 用户的 {{site.data.keyword.mysql}} 密码。
* 删除初始安装 {{site.data.keyword.mysql}} 时创建的测试帐户和数据库。
* 确保为每个 {{site.data.keyword.mysql}} 帐户分别设置密码。
* 根据需要授予特权。避免不必要地授予全局特权。
* 不要在与帐户关联的主机名值中使用[通配符 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://en.wikipedia.org/wiki/Wildcard_character){: new_window}。
* 定期复查帐户的 {{site.data.keyword.mysql}} 用户和数据库，以确保许可权始终正确。

## 其他资源

另外还有各种非 {{site.data.keyword.mysql}} 管理的额外资源可能会非常有帮助。使用任何搜索引擎搜索“{{site.data.keyword.mysql}} 安全性”都能找到这些资源。由于第三方资源不是 {{site.data.keyword.mysql}} 制造商维护的，因此请谨慎采用这些做法。与所有资源一样，请尽可能使用可信站点并参阅官方文档和支持站点。
