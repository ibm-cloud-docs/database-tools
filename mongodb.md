---
copyright:
  years: 1994, 2017
lastupdated: "2017-06-08"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MongoDB

MongoDB a fully featured NoSQL server that is horizontally scalable to meet your enterprise class database service needs. MongoDB can be ordered at no cost or requested with an OS reload. The following operating systems are supported:

* CentOS 6.x
* RHEL 6.x
* Ubuntu 12.04
* Debian 6.x

Some items of note when you provision a SL-MongoDB installation:

* By default, Mongod (the MongoDB service) is bound only to your private network interface.    MongoDB is provisioned with an administrative user pre-configured. The username is 'admin' and the password is the same as the server root password.
* If you are ordering a MongoDB Solution, like a replica set cluster, then your admin password is set on all MongoDB server in the solution at the end of the cluster configuration process.

For more information about MongoDB see the following links:

* [MongoDB Document Library](http://www.mongodb.org/display/DOCS/Home)
* [MongoDB Forums and Open Source Support](https://groups.google.com/forum/?fromgroups#!forum/mongodb-user)
* [Karl Seguin's The Little Mongo DB Book (PDF)](http://openmymind.net/mongodb.pdf)

## How Do I?

* [Configure MongoDB Networking](configure-mongodb-networking.html)
* [Set Up MongoDB Monitoring Service (MMS) for a MongoDB Solution](set-mongodb-monitoring-service-mms-mongodb-solution.html)
