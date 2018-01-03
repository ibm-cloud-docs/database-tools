---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Cambiar una contraseña raíz MySQL olvidada

Para cambiar la contraseña raíz de {{site.data.keyword.mysql}}, utilice los pasos siguientes: 

1. Ejecute los siguientes mandatos:

        # /etc/init.d/mysqld stop
        # mysqld_safe --skip-grant-tables --skip-networking

2. Conéctese a {{site.data.keyword.mysql}} con el mandato siguiente:

        # mysql -u root

3. Ejecute el mandato siguiente en el cliente de {{site.data.keyword.mysql}}:

        # UPDATE mysql.user SET Password=PASSWORD('newpassword') WHERE User='root';

4. Sustituya 'newpassword' por su nueva contraseña raíz.

5. Reinicie el servidor de {{site.data.keyword.mysql}} utilizando el mandato siguiente: 

        # /etc/init.d/mysqld start
