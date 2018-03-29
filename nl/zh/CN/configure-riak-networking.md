---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 配置 Riak 联网

在 {{site.data.keyword.Bluemix}} 工程服务器上安装 Riak 时，Riak 已绑定到[专用网络 IP 地址 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.softlayer.com/about/datacenters/rack-architecture){: new_window}。绑定 Riak 可最大程度降低开放式可访问 Riak 实例在部署时公共公开的安全风险。绑定到 Riak 的 IP 地址可以随时更改。**注：**在未落实任何安全措施以限制对实例的外部访问的情况下（例如，防火墙和 iptables），Riak 不应公开到公共接口。
{:shortdesc}

要配置 Riak 联网以绑定到新接口，请完成以下步骤。

## 将 Riak 绑定到新接口

1. 转至安装中 `/etc/riak/app.config` 文件的 `riak_core` 部分。
2. 更新 `riak_core` 部分中的 `http{}` 属性，以反映出 Riak 绑定到的新 IP 地址。<br/>`{http, [ {"127.0.0.1", 8098 } ] },`
3. 找到安装中的 `/etc/vm.args` 文件。
4. 编辑 `/etc/vm.args` 文件的 `-name` 属性，以反映出新的 IP 地址：<br/>`-name riak@127.0.0.1`
5. 重新启动 Riak 以完成绑定更改。

## 后续步骤

对绑定所做的更改会影响与 Riak 实例关联的任何接口的所有先前绑定。重新启动后，绑定的 IP 地址将更新并正常运行。如果重新启动 Riak 实例后，绑定并未成功，请联系[支持](/docs/get-support/getstarttssup.html)。
