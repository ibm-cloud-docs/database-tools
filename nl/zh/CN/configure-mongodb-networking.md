---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 配置 MongoDB 联网

## 概述

安装了 {{site.data.keyword.mongodb}} 的 {{site.data.keyword.Bluemix}} 工程服务器已配置为将 {{site.data.keyword.mongodb}} 绑定到专用网络 IP 地址。这是根据 10gen 的建议执行的操作，用于最大程度降低开放式可访问 {{site.data.keyword.mongodb}} 实例在部署时公共公开的安全风险。
{:shortdesc}

## 更改绑定的接口

如下所示，通过更改安装中 `/etc/mongod.conf` 文件中的“`bind_ip`”属性，可以将 {{site.data.keyword.mongodb}} 配置为绑定到任何接口：

        # mongo.conf
        bind_ip = 0.0.0.0  

此属性将更改为在所有接口上使用该绑定，也可以在此字段（在部署详细信息中提供）中设置特定接口的 IP 地址。需要重新启动 {{site.data.keyword.mongodb}} 实例。

**重要信息：**在未落实其他任何安全措施的情况下（例如，用于限制对实例进行访问的防火墙和 iptables），不要将 {{site.data.keyword.mongodb}} 公开到公共接口。
