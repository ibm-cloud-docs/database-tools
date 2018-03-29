---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Modification d'un mot de passe root MySQL oublié

Pour modifier le mot de passe root {{site.data.keyword.mysql}}, procédez comme suit : 

1. Exécutez les commandes suivantes :

        # /etc/init.d/mysqld stop
        # mysqld_safe --skip-grant-tables --skip-networking

2. Connectez-vous à {{site.data.keyword.mysql}} avec la commande suivante :

        # mysql -u root

3. Exécutez la commande suivante dans le client {{site.data.keyword.mysql}} :

        # UPDATE mysql.user SET Password=PASSWORD('newpassword') WHERE User='root';

4. Remplacez 'newpassword' par votre nouveau mot de passe root.

5. Redémarrez le serveur {{site.data.keyword.mysql}} avec la commande suivante :

        # /etc/init.d/mysqld start
