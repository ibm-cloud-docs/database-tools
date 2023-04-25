---

copyright:
  years: 2014, 2023
lastupdated: "2018-01-26"

keywords: reset mysql password

subcollection: database-tools

---

{{site.data.keyword.attribute-definition-list}}

# Resetting MySQL root user password
{: #dbt-reset-mysql-password}

Complete the following steps if you need to reset your {{site.data.keyword.mysql}} root user password:

1. Take down the mysqld server by sending a kill (not kill -9) to the mysqld server. The pid is stored in a .pid file, which is normally in the {{site.data.keyword.mysql}} database directory:
   * `shell> kill cat /your-mysql-data-directory/hostname.pid`
   * In Red Hat, you can also stop the database:
      * `shell> service mysqld stop`
      * You must be either the UNIX root user or the same user the server runs as to stop the database.
2. Restart mysqld with the `--skip-grant-tables` option.
3. Connect to the mysqld server.

   * **Option 1:** mysql -h host name mysql and change the password with a GRANT command.
   * For more information about GRANT commands, see [{{site.data.keyword.mysql}} Documentation](http://www.mysql.com/doc/G/R/GRANT.html){: external}
   * **Option 2:** `shell> mysqladmin -h hostname -u user password 'new password'`

4. Load the privilege tables by using `shell> mysqladmin -h hostname flush-privileges` or with the SQL command `mysql> FLUSH PRIVILEGES;`.

After you start mysqld with --skip-grant-tables, any usage of GRANT commands gives you an `Unknown command` error until you run _FLUSH PRIVILEGES_.
{: note}
