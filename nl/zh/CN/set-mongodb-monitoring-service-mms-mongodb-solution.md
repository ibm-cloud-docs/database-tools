---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# 设置 MongoDB 监视服务 (MMS)

## 概述

完成 {{site.data.keyword.mongodb}} 解决方案后，可以将副本集内的主机设置为与 10gen 的免费 {{site.data.keyword.mongodb}} 监视服务（MMS）配合使用。可以使用此监视服务来查看复制数据库的详细技术分析。为此，首先您需要有通过在 [10gen MMS 注册 Web 站点 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.10gen.com/mongodb-monitoring-service){: new_window} 上注册帐户而获取的 MMS API 密钥和私钥。
{:shortdesc}

**注：**如果在订购 {{site.data.keyword.mongodb}} 解决方案时，已输入 MMS 密钥或新的 MMS 帐户信息，那么这些 MMS 凭证可能已经设置。

帐户的 MMS API 密钥和私钥可在 [10gen MMS Web 站点 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://mms.10gen.com/){: new_window} 上找到。使用提供的凭证登录，然后选择**设置**以显示 MMS 组的 **API 密钥**和**私钥**。

## 配置主机

配置 MMS 之前，您需要更新主机上的 API 密钥和私钥。**注：**以下步骤只需要在集内的单个主机上执行即可。不过，也可以在多个主机上执行相同的步骤，以启用故障转移备份 MMS 代理程序。集内只有一个代理程序会向 MMS 服务传递信息。

1. 通过 SSH 连接到解决方案中的一个主机（网络地址和凭证可以在 {{site.data.keyword.slportal_full}} 中找到）。
2. 运行以下命令，并替换相应的 API 密钥和私钥。

    `# /opt/local/bin/mongoConfigureAuthentication.sh -a -s`

    `Updating the /opt/local/10gen/mms-agent/settings.py file with the`
    `MMS API/secret keys...`

    `Restarting MMS agent...`

    `Shutting down MMS-agent:                                   [  OK  ]`

    `Starting MMS-agent:                                        [  OK  ]`


## 配置 MMS 组

配置主机并重新启动 MMS 代理程序后，需要在 10gen MMS Web 站点上重新启动 MMS 组。

1. 登录到 [10gen MMS Web 站点 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://mms.10gen.com/){: new_window}。
2. 选择**主机 > 代理程序**。
3. 验证已配置的代理程序是否位于列表中。在列表中，每个已配置并重新启动的组都会列出一个代理程序。
4. 要向列表中添加主机，请选择**主机**，然后单击**加号 (+)**。
5. 输入主机的*专用 IP 地址*和 {{site.data.keyword.mongodb}} 的端口号。SoftLayer MongoDB 解决方案的缺省端口号为 27018。
6. 输入数据库管理用户名和密码（可在 {{site.data.keyword.slportal}} 中设备的**密码**中找到），然后选择**添加**。
  * **重要信息：**这些凭证是必需的。

**注：**最长可能需要 30 分钟数据才会在 MMS 中显示。
