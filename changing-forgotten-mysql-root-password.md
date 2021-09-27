---

copyright:
  years: 2014, 2021
lastupdated: "2017-11-10"

keywords: mysql password

subcollection: database-tools

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Changing a forgotten MySQL root password
{: #dbt-change-mysql-password}

To change the {{site.data.keyword.mysql}} root password, use the following steps:

1. Run the following commands:

   ```text
   # /etc/init.d/mysqld stop
   ```
   {: pre}

   ```
   # mysqld_safe --skip-grant-tables --skip-networking
   ```
   {: pre}

2. Connect to {{site.data.keyword.mysql}} with the following command:

   ```text
   # mysql -u root
   ```
   {: pre}

3. Run the following command in the {{site.data.keyword.mysql}} client:

   ```text
   # UPDATE mysql.user SET Password=PASSWORD('newpassword') WHERE User='root';
   ```
   {: pre}

4. Replace `newpassword` with your new root password.

5. Restart the {{site.data.keyword.mysql}} server by using the following command:

   ```text
   # /etc/init.d/mysqld start
   ```
   {: pre}
