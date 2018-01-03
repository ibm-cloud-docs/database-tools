---
copyright:
  years: 1994, 2017
lastupdated: "2017-06-08"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MongoDB

MongoDB 是一个全功能 NoSQL 服务器，可水平扩展以满足企业级数据库服务的需求。MongoDB 可以通过免费订购，也可以通过操作系统重装进行请求。支持以下操作系统：

* CentOS 6.x
* RHEL 6.x
* Ubuntu 12.04
* Debian 6.x

供应 SL-MongoDB 安装时的一些说明项：

* 缺省情况下，Mongod（MongoDB 服务）仅绑定到专用网络接口。为 MongoDB 供应了预配置的管理用户。用户名为“admin”，密码与服务器 root 用户密码相同。
* 如果订购的是 MongoDB 解决方案（例如，副本集集群），那么会在集群配置流程结束时，在该解决方案的所有 MongoDB 服务器上设置 admin 密码。

有关 MongoDB 的更多信息，请参阅以下链接：

* [MongoDB 文档库](http://www.mongodb.org/display/DOCS/Home)
* [MongoDB 论坛和开放式源代码支持](https://groups.google.com/forum/?fromgroups#!forum/mongodb-user)
* [Karl Seguin 所著的 The Little Mongo DB Book (PDF)](http://openmymind.net/mongodb.pdf)

## 我应该如何做？

* [配置 MongoDB 联网](configure-mongodb-networking.html)
* [为 MongoDB 解决方案设置 MongoDB 监视服务 (MMS)](set-mongodb-monitoring-service-mms-mongodb-solution.html)
