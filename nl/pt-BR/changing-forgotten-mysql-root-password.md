---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Mudando uma senha raiz do MySQL esquecida

Para mudar a senha raiz do {{site.data.keyword.mysql}}, use as etapas a seguir: 

1. Execute os seguintes comandos:

        # /etc/init.d/mysqld stop
        # mysqld_safe --skip-grant-tables --skip-networking

2. Conecte-se ao {{site.data.keyword.mysql}} com o comando a seguir:

        # mysql -u root

3. Execute o comando a seguir no cliente {{site.data.keyword.mysql}}:

        # UPDATE mysql.user SET Password=PASSWORD('newpassword') WHERE User='root';

4. Substitua 'newpassword' por sua nova senha raiz.

5. Reinicie o servidor {{site.data.keyword.mysql}} usando o comando a seguir:

        # /etc/init.d/mysqld start
