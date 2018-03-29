---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Informations sur l'optimisation/la réparation de MySQL

## Utilisation de la mémoire par MySQL 
Voici quelques scénarios d'utilisation de la mémoire par le serveur mysqld ainsi que les noms des variables mysqld associées.
* [Utilisation de la mémoire par MySQL 5.0 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://dev.mysql.com/doc/refman/5.0/en/memory-use.html){: new_window}
* [Utilisation de la mémoire par MySQL 4.1 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://dev.mysql.com/doc/refman/4.1/en/memory-use.html){: new_window}

## L'optimisation de MySQL couvre les éléments suivants :
- Présentation de l'optimisation
- Optimisation de SELECT et autres instructions
- Problèmes liés au verrouillage
- Optimisation de la structure de base de données
- Optimisation du serveur MySQL
- Problèmes liés aux disques

[Optimisation de MySQL 5.0 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://dev.mysql.com/doc/refman/5.0/en/optimization.html){: new_window} [Optimisation de MySQL 4.1 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://dev.mysql.com/doc/refman/4.1/en/optimization.html){: new_window}

## Variables du serveur MySQL - propres à la couche SQL ou au moteur de stockage.
Les liens suivants répertorient certaines des variables les plus courantes.
[Voir l'article 1 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.mysqlperformanceblog.com/2006/06/08/mysql-server-variables-sql-layer-or-storage-engine-specific/){: new_window} [Voir l'article 2 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://forge.mysql.com/wiki/ServerVariables){: new_window}

## Optimisation des variables mysqld par Ian Gilfillan
Lisez cet article sur l'optimisation de MySQL, qui fournit également quelques directives concernant la configuration de la variable du serveur mysqld.
(key_buffer_size, Query cache variables, table_cache, sort_buffer, etc..)
[Voir l'article ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.databasejournal.com/features/mysql/article.php/3367871){: new_window}

## Réparation suite à une altération de la base de données dans MySQL par Ian Gilfillan
Les altérations de table sont rares lorsque vous utilisez {{site.data.keyword.mysql}}. Mais il est toujours utile de savoir comment corriger un problème s'il se produit.
[Voir l'article ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.databasejournal.com/features/mysql/article.php/3300511){: new_window}

## Optimisation de MySQL : Requêtes et index par Ian Gilfillan
<!--The database is too slow. Queries are queuing up, backlogs growing, users being refused connection. Management is ready to spend millions on "upgrading" to some other system, when the problem is really that MySQL is simply not being used properly. Badly defined or non-existent indexes are one of the primary reasons for poor performance, and fixing these can often lead to phenomenal improvements.-->
[Voir l'article ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.databasejournal.com/features/mysql/article.php/1382791){: new_window}

[Autres articles {{site.data.keyword.mysql}} par Ian Gilfillan ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.databasejournal.com/article.php/1474351){: new_window}
