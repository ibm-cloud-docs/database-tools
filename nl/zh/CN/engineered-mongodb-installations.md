---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 工程 MongoDB <!--installations-->的新增功能

为了提高工程 {{site.data.keyword.mongodb}} 安装的性能，进行了以下更改。这些更改使用 10gen 来尽可能提供最佳的工程服务器用户体验。10gen 和 {{site.data.keyword.cloud}} 使用各种 {{site.data.keyword.baremetal_short}} 作为平台基础<!--{{site.data.keyword.baremetal_short}} provide a consistent high performance set of available resources that cannot be matched in shared resource, multi-tenant platforms.-->。  

* **CentOS 6.X 作为首选操作系统** - 10gen 表示，他们发现在 CentOS 操作系统上可实现支持 {{site.data.keyword.mongodb}} 的最佳性能和功能。根据此建议，{{site.data.keyword.cloud_notm}} 只会将 {{site.data.keyword.mongodb}} 部署在 CentOS 6.X 平台上。

* **将 SSD 预读的缺省值设置为 16 个块** - SSD 驱动器的搜寻时间非常出色，所以可以将“预读”设置为 16 个块。旋转磁盘可能需要略微缓冲，所以旋转磁盘设置为 32 个块。

* **Noatime** - 通过添加 noatime，无需系统将正在读取的文件写入文件系统，这意味着访问文件的速度更快，磁盘磨损减少。

* **在 BIOS 中关闭 NUMA** - Linux、NUMA 和 {{site.data.keyword.mongodb}} 通常不会一起使用。如果在 NUMA 硬件上运行 {{site.data.keyword.mongodb}}，请将 NUMA 关闭（使用 interleave 内存策略运行）。否则，问题可能会以奇怪的方式出现，例如一段时间内速度大幅下降或系统 CPU 时间长。

* **Ulimit** - 对于打开文件数，ulimit 设置为 64,000，对于用户进程数，ulimit 设置为 32,000。这些限制可防止因可用文件句柄数或用户进程数丢失而导致的故障。

* **EXT4** - 选择时，Ext4 优先于 Ext3。Ext3 分配文件（或除去文件）的速度可能较慢，而且在大型文件中的访问性能不佳。

* **单独的日志卷** - 根据 10gen 的建议，{{site.data.keyword.cloud_notm}} 会使用单独为日志安装的 SSD 卷。此卷在更高端的工程服务器上提供，并可避免日志记录干扰对数据安装执行的读/写操作。

* **已预安装 MMS** - MMS 是 10gen 的监视服务，为所有 {{site.data.keyword.mongodb}} 实例免费提供。所有 {{site.data.keyword.cloud_notm}} 工程服务器均已预配置 MMS 代理程序。
