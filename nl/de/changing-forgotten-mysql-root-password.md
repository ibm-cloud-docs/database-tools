---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Vergessenes MySQL-Rootkennwort ändern

Führen Sie die folgenden Schritte aus, um das {{site.data.keyword.mysql}}-Rootkennwort zu ändern: 

1. Führen Sie die folgenden Befehle aus:

        # /etc/init.d/mysqld stop
        # mysqld_safe --skip-grant-tables --skip-networking

2. Stellen Sie mit dem folgenden Befehl eine Verbindung zu {{site.data.keyword.mysql}} her:

        # mysql -u root

3. Führen Sie den folgenden Befehl im {{site.data.keyword.mysql}}-Client aus:

        # UPDATE mysql.user SET Password=PASSWORD('newpassword') WHERE User='root';

4. Ersetzen Sie 'newpassword' durch Ihr neues Rootkennwort.

5. Führen Sie den folgenden Befehl aus, um einen Neustart für den {{site.data.keyword.mysql}}-Server durchzuführen:

        # /etc/init.d/mysqld start
