---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Réinitialisation du mot de passe de l'utilisateur root MySQL

Si vous avez besoin de réinitialiser votre mot de passe d'utilisateur root {{site.data.keyword.mysql}}, procédez comme suit :

1. Arrêtez le serveur mysqld en lui envoyant une commande kill (pas kill -9). L'ID de processus est stocké dans un fichier .pid, qui se trouve normalement dans le répertoire des bases de données {{site.data.keyword.mysql}} :
  * Exemple : `shell> kill cat /your-mysql-data-directory/hostname.pid`
  * Dans Red Hat, vous pouvez également arrêter la base de données :
    * Exemple : `shell> service mysqld stop`
    * Vous devez être l'utilisateur root Unix ou celui pour lequel le serveur a exécuté la commande d'arrêt de la base de données.
2. Redémarrez mysqld avec l'option --skip-grant-tables.
3. Connectez-vous au serveur mysqld :
  * **Option 1 :** mysql -h hostname mysql et modifiez le mot de passe avec une commande GRANT.
    * Pour plus d'informations sur la commande GRANT, voir la [documentation {{site.data.keyword.mysql}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.mysql.com/doc/G/R/GRANT.html){: new_window}
  * **Option 2 :** `shell> mysqladmin -h hostname -u user password 'nouveau mot de passe'`
4. Chargez les tables de privilèges avec `shell> mysqladmin -h hostname flush-privileges` ou avec la commande SQL `mysql> FLUSH PRIVILEGES;`.


**Remarque :** Lorsque vous démarrez mysqld avec --skip-grant-tables, toutes les commandes GRANT vous renvoient le message `Unknown command` jusqu'à ce que vous exécutiez _FLUSH PRIVILEGES_.*
