---

copyright:
  years: 2014, 2019
lastupdated: "2018-01-26"

keywords: MongoDB architectural best practices

subcollection: database-tools

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# MongoDB - Architectural best practices
{: #dbt-mongobd-best-practices}

Use the following best practices for using {{site.data.keyword.mongodb}} in deployments on {{site.data.keyword.cloud}}. If you selected engineered servers, several of these recommendations are already implemented. 

## Deployment strategy

When you plan your deployment of {{site.data.keyword.mongodb}}, you need to consider several key areas. The most important is your current and anticipated data set size. These two areas are the primary driver for your choice of individual physical node resource needs and guides your sharding plans. You also need to consider the importance of your data and how tolerant you are of the possibility of lost or lagging data (especially in replicated scenarios). 
## Memory sizing

{{site.data.keyword.mongodb}} (like many data-oriented applications) works best when the data set stays in memory. Nothing performs better than a {{site.data.keyword.mongodb}} instance that does not require disk I/O. Whenever possible, select a platform that has more available RAM than your working data set size. If your data set exceeds the available RAM for a single node, then consider taking advantage of sharding. Sharding increases the amount of available RAM in a cluster to accommodate the larger data set. Thus, you maximize the overall performance of your deployment. Page faults can indicate that you might be exceeding the available RAM in your deployment. You need to consider increasing your available RAM.

## Disk type
If speed is not a concern, or if you have a data set that is larger than your available memory strategy can support, a proper disk type for your deployment is important. IOPS is key in selecting your disk type. The higher the IOPS, the better the performance of {{site.data.keyword.mongodb}}. Local disks need to be used if possible as network storage can cause high latency and poor performance for your deployment. It is advised that you use RAID 10 for disk arrays.

## CPU
Clock speed and the number of available processors becomes a consideration if you want to use a map-reduce. However, when you run a {{site.data.keyword.mongodb}} instance with most of the data in memory, clock speed can impact performance. If your system runs under these circumstances and you want to maximize your operations per second, consider a deployment strategy that includes a CPU with a high clock bus speed.

## Replication
Replication provides high availability of your data if a node fails in your cluster. For best results, replicate with at least three nodes in any {{site.data.keyword.mongodb}} deployment. The most common configuration for replication with three nodes is a 2x1 deployment that has two primary nodes in a single data center with a backup server in a secondary data center.

## Sharding
If you anticipate a large data set, it is advised that you deploy a sharded {{site.data.keyword.mongodb}} deployment. You can use sharding to partition your data set across multiple nodes. {{site.data.keyword.mongodb}} can automatically distribute the data across nodes in the cluster. Or, define a shard key and create range-based sharding for that key. Sharding can help write performance. So it's possible that you can shard even if your data set is small but requires a high number of updates or inserts. When you deploy a sharded set, {{site.data.keyword.mongodb}} requires only three config server instances that are specialized Mongo runtimes to track the current shard configuration. Loss of one of these nodes causes the cluster to go into a read only mode for the configuration. Read only mode requires that all nodes be brought back online before any configuration changes can be made.

## Write safety mode
You have multiple options to write safety modes that govern how {{site.data.keyword.mongodb}} handles the persistence of the data to disk. It is important to consider which strategy best fits your needs for both data integrity and performance. You have the following write safety modes available:

* **None** – Provides a deferred writing strategy that is non-blocking that helps with high performance. However, a node failure and data loss is a small possibility. It is also possible data that is written to one node in a cluster is not immediately available on all nodes in that cluster for read consistency. The None mode does not provide any data protection for network failures. This mode is highly unreliable and is used only when performance is a priority and data integrity is not a concern.
* **Normal** – Is the default for {{site.data.keyword.mongodb}}. Normal mode is also a non-blocking deferred writing strategy.  
* **Safe** – Blocks until {{site.data.keyword.mongodb}} acknowledges that it received the write request, but does block until the write is complete. Safe mode provides a better level of data integrity and read consistency within a cluster.
* **Journal Safe** – Provides a recovery option for {{site.data.keyword.mongodb}}. Journal Safe mode makes sure that the data is acknowledged and that a Journal update is complete before it returns.
* **Fsync** – Provides the highest level of data integrity and blocks until a physical write of the data occurs. Using Fsync comes with a degradation in performance and you use it only if data integrity is the primary concern for your application.

## Testing the deployment
10gen has several tools to help you load test your deployment. A console tool, benchRun, can run operations from within a JavaScript test harness. benchRun returns operation information and latency numbers for each operation. If more detailed information is needed about the {{site.data.keyword.mongodb}} instance, consider running the `mongostat` command or MMS to monitor your deployment during the testing. For more information about these tools, see the following references:

[MongoStat Overview ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://docs.mongodb.org/manual/reference/mongostat/){: new_window}

[10gen's {{site.data.keyword.mongodb}} Monitoring Service ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.10gen.com/products/mongodb-monitoring-service){: new_window}

## Installation
You have several considerations when you install {{site.data.keyword.mongodb}} that can help create a stable and performance-oriented solution. 10gen recommends that you use CentOS (64-bit) if possible. Avoid deploying on 32-bit operating systems and Windows operating systems. These systems provide a poor deployment platform. 32-bit operating systems have file size limits that cause problems and Windows can cause performance issues if virtual memory is used by the OS to make up for a lack of RAM in your deployment. By default, {{site.data.keyword.cloud_notm}} provides CentOS 64-bit operating systems for all engineered server deployments.

Additionally, make sure that you make the following alterations to the base OS installation to maximize performance:
* **Set SSD Read Ahead Defaults to 16 Blocks** – SSD drives have excellent seek times that allow for shrinking the Read Ahead to 16 blocks. Spinning disks can require slight buffering so these disks are set to 32 blocks.
* **noatime** – Noatime eliminates the need for the system to write to the file system for files that are being read. This means that you experience faster file access and less disk wear.
* **Turn NUMA Off in BIOS** Linux, NUMA, and {{site.data.keyword.mongodb}} generally do not work together. If you are running {{site.data.keyword.mongodb}} on NUMA hardware, it is recommended that you turning it off (running with an interleave memory policy). If you don’t, problems like massive slow downs or high system CPU time can manifest.
* **Set ulimit** – The ulimit is set to 64000 for open files and 32000 for user processes. These ulimits prevent failures due to a loss of available file handles or user processes. 
* **Use ext4** – Ext3 is slow in allocating files (or removing them). Additionally, access within large files is poor with ext3.

**Note:** By default, these alterations are set on all {{site.data.keyword.cloud_notm}} servers.

It is also recommended that the Journal and Data volumes be distinct physical volumes. If the Journal and Data directories reside on a single physical volume, flushes to the Journal interrupt the access of data and provide spikes of high latency within your {{site.data.keyword.mongodb}} deployment.

## Operations
After a {{site.data.keyword.mongodb}} deployment is promoted to production, consider the following recommendations for monitoring and performance optimization. 
* Make sure that the MMS agent is running on all instances of {{site.data.keyword.mongodb}}, which helps monitor the health and performance of the deployment. The MMS agent provides useful debugging data to 10gen during support interactions. 
* The `mongostat` command also provides runtime information about the performance of a {{site.data.keyword.mongobd}} node.

If either of these tools discover performance issues, sharding or indexing can help to correct these performance issues. 

* Create indexes for a {{site.data.keyword.mongodb}} deployment if the monitoring tools indicate that field-based queries are operating poorly. To help improve performance, always use indexes when you query data that is based on distinct fields.
* Use sharding when the overall performance of the node suffers because of a large operating data set. Make sure to shard before you get in the red. The system splits chunks only for sharding on insert or update. If you wait too long to shard, you can have uneven distribution. 

