---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Changing a forgotten MySQL root password

To change the {{site.data.keyword.mysql}} root password, use the following steps:

1. Run the following commands:

```# /etc/init.d/mysqld stop```
```# mysqld_safe --skip-grant-tables --skip-networking```

2. Connect to {{site.data.keyword.mysql}} with the following command:

```# mysql -u root```

3. Run the following command in the {{site.data.keyword.mysql}} client:

```# UPDATE mysql.user SET Password=PASSWORD('newpassword') WHERE User='root';```

4. Replace `newpassword` with your new root password.

5. Restart the {{site.data.keyword.mysql}} server by using the following command:

```# /etc/init.d/mysqld start```
