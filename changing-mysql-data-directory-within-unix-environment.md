---

copyright:
  years: 2014, 2023
lastupdated: "2018-11-15"

keywords: mysql data directory, unix

subcollection: database-tools

---

{{site.data.keyword.attribute-definition-list}}

# Changing the MySQL data directory in a UNIX or similar environment
{: #dbt-change-mysql-directory}

Follow these steps to change your {{site.data.keyword.mysql}} data directory:

1. Log in to the server by using [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html){: external}, or your preferred client.

   If you are using a dedicated partition for the data directory, make sure to mount the new partition in place of the original data directory after you copy the data over. Mounting a new partition saves non-standard configuration changes that some applications might not work with.
   {: note}

2. Shut down `mysqld` ({{site.data.keyword.mysql}} daemon). The process to start and stop the daemon can differ between different operating systems and distributions. {{site.data.keyword.mysql}} must be stopped during any process that directly affects the raw files.

   `/etc/init.d/mysql stop`

   OR

   `/etc/init.d/mysqld, /etc/init.d/mysql-server, /usr/loca/etc/init.d/mysql, /opt/lamp…`

3. Back up your database before you make any changes. Make sure that the {{site.data.keyword.mysql}} daemon is not running when you make direct copies of the raw database files.

If you use cPanel on the server, stop cPanel (TailWatch and chkservd) before the daemon restarts. You can create a temporary file `/etc/chkserv.d/mysqlisevil` to stop `chkservd` from restarting the service. If you are not familiar with rsync, you can use any other tool to create your backup.

   `rsync -vaP /var/lib/mysql/ /var/lib/mysql.'date +%s'`

4. Create the data directory and provide the {{site.data.keyword.mysql}} user (or whichever user is specified in your 'my.cnf' global option file) ownership. In this example, the location `/var/lib/mysql-data` is used, but you can use any location that you want. If you are adding a disk or logical device specifically for this purpose, then you also need to add the entry into `/etc/fstab` and mount the directory before you proceed.

   `chown mysql:mysql /var/lib/mysql-data`

5. Make a final copy of the original directory to the new {{site.data.keyword.mysql}} data directory (make sure to keep the trailing / at the end of the first directory):

   `rsync -vaP /var/lib/mysql/ /var/lib/mysql-data`

6. Make sure that the new data directory has the correct ownership, either the default {{site.data.keyword.mysql}} user and group or the user that is specified in your 'my.cnf' global option file. If you are unsure, you can use the following command to recursively own the entire hierarchy to the {{site.data.keyword.mysql}} user and group.

   `chown -R mysql:mysql /var/lib/mysql-data`

User {{site.data.keyword.mysql}} needs to have full permission (rwx) to the database folders and read/write permission to the log, bin, data, index, and form files.

Typically, database folders have a permission of 700 (drwx------) and be under ownership of mysql:mysql while in a shared hosting environment. The permission can be more liberally configurated with 755 (drwxr-xr-x) in a dedicated environment.

7. Update your '/etc/my.cnf' configuration file to point it to the new data directory.

   Make sure that you back up everything before you make any edits to the configuration file.
   {: important}

   `cp -vp /etc/my.cnf /etc/my.cnf.'date +%s'`
   `vi /etc/my.cnf`

8. Replace any instance of '/var/lib/mysql' with '/var/lib/mysql-data'. If you do not have a `datadir` entry, then place it within the [mysqld] stanza.

   `[mysqld]`
   `user = mysql`
   `datadir = /var/lib/mysql-data`
   `socket =  /var/lib/mysql-datal/mysql.sock`

9. Some applications have custom configuration and this document cannot cover them. Some scripts are known to fail if the data directory is not /var/lib/mysql. So, a symbolic link is used to point to the new location.

   `mv -v /var/lib/mysql /var/lib/mysql.orig`

   `ln -s /var/lib/mysql-data /var/lib/mysql`

If you do not want to create the link, make sure to change the 'mysql.default'_socket and 'mysqli.default'_socket in 'php.ini' and completely stop and start Apache.

10. Start the {{site.data.keyword.mysql}} daemon.

   `/etc/init.d/mysql start`

11. Verify that {{site.data.keyword.mysql}} is working. If {{site.data.keyword.mysql}} does not respond, review your error logs. Revert the changes if necessary.

   `mysqladmin ping`
