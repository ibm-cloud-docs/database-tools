---

copyright:
  years: 2014, 2024
lastupdated: "2024-07-15"

keywords: mysql optimization, mysql repair

subcollection: database-tools

---

{{site.data.keyword.attribute-definition-list}}

# MySQL optimization and repair information
{: #dbt-optimize-repair-mysql}

Use the following information so optimize and repair information.
{: shortdesc}

## How MySQL uses memory
{: #how-mysql-uses-memory}
The following are some of the ways that the mysqld server uses memory, and associated mysqld variable names.

* [Memory Use MySQL 5.0](http://dev.mysql.com/doc/refman/5.0/en/memory-use.html){: external}
* [Memory Use MySQL 4.1](http://dev.mysql.com/doc/refman/4.1/en/memory-use.html){: external}

## MySQL optimization topics
{: #mysql-optimizations-topics}

MySQL optimization covers the following topics.

* Optimization overview
* Optimizing SELECT and other statements
* Locking issues
* Optimizing database structure
* Optimizing the MySQL Server
* Disk issues

[Optimization MySQL 5.0](http://dev.mysql.com/doc/refman/5.0/en/optimization.html){: external}
[Optimization MySQL 4.1](http://dev.mysql.com/doc/refman/4.1/en/optimization.html){: external}

## MySQL Server variables - SQL layer or Storage Engine specific
{: #mysql-variables-layer-or-storage-engine}

The following links list some of the more common variables.

* [Go to article 1](http://www.mysqlperformanceblog.com/2006/06/08/mysql-server-variables-sql-layer-or-storage-engine-specific/){: external}
* [Go to article 2](https://dev.mysql.com/doc/refman/5.7/en/server-system-variable-reference.html){: external}

## Optimizing the mysqld variables
{: #optimize-mysqlid-variables}

For more information, see the [Optimizing the mysqld variables](https://www.databasejournal.com/mysql/optimizing-the-mysqld-variables/){: external} article about MySQL optimization, including guidelines on setting a mysqld server variable such as key_buffer_size, query cache variables, table_cache, and sort_buffer.

## Repairing database corruption in MySQL
{: #repairing-database-corruption-mysql}

Table corruption is rare when you use {{site.data.keyword.mysql}}. However, it helps to know how to fix the problem when it occurs. For more information, see [Repairing database corruption in MySQL](https://www.databasejournal.com/mysql/repairing-database-corruption-in-mysql/){: external}.
