---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Sauvegarde de MySQL sous Linux

## Copie depuis le répertoire MySQL

Par défaut, les bases de données {{site.data.keyword.mysql}} des serveurs Linux sont stockées dans le répertoire suivant :

`/var/lib/mysql/`

Si vous commencez par arrêter le service mysqld, vous pouvez copier vos bases de données dans un répertoire tel que /backup à l'aide de la commande suivante :

`cp –Rp /var/lib/mysql/*.* /backup`

Le paramètre –R de la commande cp vaut pour récursif, ce qui convient puisque chaque base de données se trouve dans un répertoire distinct. Le paramètre –p vaut pour permissions, ce qui permet de conserver les droits des éléments copiés.

En général, vous arrêtez le service mysqld avant d'utiliser la commande ci-dessus. Si une base de données est copiée alors qu'elle est en cours d'utilisation, la sauvegarde est corrompue et inutile. Si vous êtes sûr que les bases de données ne sont pas utilisées au moment de la sauvegarde, vous pouvez utiliser la commande ci-dessus.

## Commande mysqldump

La commande mysqldump permet de sauvegarder les bases de données individuelles et toutes les bases de données d'un serveur sans avoir à arrêter le service mysqld. Cette possibilité d'effectuer des sauvegardes tout en laissant les bases de données en ligne est la méthode la plus plébiscitée.

## Bases de données individuelles

L'exemple de commande suivant permet de sauvegarder une base de données nommée _'example'_ dans le répertoire /backup en étant connecté en tant qu'utilisateur root :

`mysqldump example > /backup/example_backup.sql`

Sauf s'il s'agit d'une petite base de données, compressez la sauvegarde de la base de données afin de réduire le temps nécessaire à son transfert. La commande suivante compresse la sauvegarde de l'exemple de base de données :

`tar czvf /backup/example_backup.tar.gz /backup./example_backup.sql`

## Toutes les bases de données

Si vous avez plusieurs bases de données à sauvegarder, la commande suivante sauvegarde toutes les bases de données {{site.data.keyword.mysql}} de votre serveur dans le répertoire /backup :

`mysqldump -A > /backup/databases.sql(or --all-databases)`

Le paramètre –A switch (“-all-databases” effectue la même fonction) vide toutes les bases de données du serveur.
