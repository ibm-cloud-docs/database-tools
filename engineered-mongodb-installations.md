---

copyright:
  years: 2014, 2023
lastupdated: "2018-11-15"

keywords: engineered MongoDB, {{site.data.keyword.cloud}}, {site.data.keyword.baremetal_short}}

subcollection: database-tools

---

{{site.data.keyword.attribute-definition-list}}

# What's new with engineered MongoDB
{: #bdt-engineered-mongodb}

The following changes were made to enhance the performance of engineered {{site.data.keyword.mongodb}} installations. These changes use 10gen to give the best possible user experience with engineered servers. 10gen and {{site.data.keyword.cloud}} use various {{site.data.keyword.baremetal_short}} to serve as the platform base.

* 10gen indicates that they found the best performance and ability to support {{site.data.keyword.mongodb}} is found on the CentOS operating system. Under this recommendation, {{site.data.keyword.cloud_notm}} exclusively deploys {{site.data.keyword.mongodb}} onto a CentOS 6.X platform.

* SSD drives have excellent seek times, so Read Ahead can be set to 16 blocks. Spinning disks can require slight buffering, so spinning disks are set to 32 blocks.

* Adding the noatime eliminates the need for the system to write to the file system for files that are being read, which means faster file access and less disk wear.

* Linux, NUMA, and {{site.data.keyword.mongodb}} tend not to work together. If you run {{site.data.keyword.mongodb}} on NUMA hardware, turn it off (running with an interleave memory policy). Problems can manifest in strange ways, such as massive slow downs for periods of time or high system CPU time.

* The ulimit is set to 64,000 for open files and 32,000 for user processes. These limits help prevent failures due to a loss of available file handles or user processes.

* Ext4 is selected over Ext3. Ext3 can be slow in allocating files (or removing them) and access within large files is also poor.

* Under the advice of 10gen, {{site.data.keyword.cloud_notm}} uses a separate SSD volume that is mounted for the journal. This configuration is available on the higher-end engineered servers and prevents journaling from interfering with read/write operations on the data mount.

* MMS is the 10gen monitoring service that is provided free of charge for all {{site.data.keyword.mongodb}} instances. All {{site.data.keyword.cloud_notm}} engineered servers are pre-configured with the MMS agent.
