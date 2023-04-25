---

copyright:
  years: 2014, 2023
lastupdated: "2018-01-26"

keywords: backing up mysql, linux

subcollection: database-tools

---

{{site.data.keyword.attribute-definition-list}}

# Backing up MySQL in Linux
{: #dbt-back-up-mysql-linux}

By default, {{site.data.keyword.mysql}} databases on Linux servers are stored in the following directory:

`/var/lib/mysql/`

If you shut down the mysqld service first, you can copy your databases to an example /backup directory by using the following command:

`cp –Rp /var/lib/mysql/*.* /backup`

The –R switch for the cp command means recursive, which you want to use because each database is in a separate directory. The –p switch is for permissions, which maintains the permissions of what is copied.

Generally, you shut down the mysqld service before you use the preceding method. If a database is copied while it is being used, the backup corrupts and is rendered worthless. If you are certain none of the databases are not being used at the time, you can use the preceding command.

## The mysqldump command
{: #sbt-mysqldump}

You use the mysqldump command to back up both individual databases and all databases on a server without having to shut down the mysqld service. Because of this ability to make backups while still keeping databases online, this method is preferred.

## Individual databases
{: #dbt-ind-databases}

The following code is an example command that you use to back up a database that is named _'example'_ to the directory /backup while logged in as root:

`mysqldump example > /backup/example_backup.sql`

Unless it is a small database, then compress the database backup to reduce the amount of time to transfer the backup. The following command compresses the backup of the example database:

`tar czvf /backup/example_backup.tar.gz /backup./example_backup.sql`

## All databases
{: #dbt-all-databases}

If you have several databases to back up, the following command backups all {{site.data.keyword.mysql}} databases on your server to the /backup directory:

`mysqldump -A > /backup/databases.sql(or --all-databases)`

The –A switch (“-all-databases” has the same function) dumps all databases on the server.
