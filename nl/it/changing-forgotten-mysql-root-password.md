---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Modifica di una password root MySQL dimenticata

Per modificare la password root {{site.data.keyword.mysql}}, utilizza la seguente procedura: 

1. Esegui questi comandi:

        # /etc/init.d/mysqld stop
        # mysqld_safe --skip-grant-tables --skip-networking

2. Collegati a {{site.data.keyword.mysql}} con il seguente comando:

        # mysql -u root

3. Immetti il seguente comando nel client {{site.data.keyword.mysql}}:

        # UPDATE mysql.user SET Password=PASSWORD('newpassword') WHERE User='root';

4. Sostituisci 'newpassword' con la nuova password root.

5. Riavvia il server {{site.data.keyword.mysql}} utilizzando il seguente comando:

        # /etc/init.d/mysqld start
