---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Optimización de MySQL/Información de reparación

## Cómo utiliza MySQL la memoria 
A continuación se muestran algunas de las formas en que el servidor de mysqld utiliza la memoria, y los nombres de variables de mysqld asociadas.
* [Uso de memoria de MySQL 5.0 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://dev.mysql.com/doc/refman/5.0/en/memory-use.html){: new_window}
* [Uso de memoria de MySQL 4.1 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://dev.mysql.com/doc/refman/4.1/en/memory-use.html){: new_window}

## La Optimización de MySQL cubre los siguientes elementos:
- Visión general de la optimización
- Optimización de SELECT y otras sentencias
- Problemas de bloqueo
- Optimización de la estructura de base de datos
- Optimización del servidor MySQL
- Problemas de disco

[Optimización de MySQL 5.0 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://dev.mysql.com/doc/refman/5.0/en/optimization.html){: new_window}
[Optimización de MySQL 4.1 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://dev.mysql.com/doc/refman/4.1/en/optimization.html){: new_window}

## Variables del servidor MySQL - específicas de la capa de SQL o del motor de almacenamiento.
Los enlaces siguientes enumeran algunas de las variables más comunes.
[Vaya al artículo 1 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.mysqlperformanceblog.com/2006/06/08/mysql-server-variables-sql-layer-or-storage-engine-specific/){: new_window}
[Vaya al artículo 2 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://forge.mysql.com/wiki/ServerVariables){: new_window}

## Optimización de las variables de mysqld, escrito por Ian Gilfillan
Consulte este artículo sobre la optimización de MySQL, incluidas algunas directrices sobre el establecimiento de la variable del servidor mysqld.
(key_buffer_size, Query cache variables, table_cache, sort_buffer, etc..)
[Vaya al artículo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.databasejournal.com/features/mysql/article.php/3367871){: new_window}

## Reparación de daños de la base de datos en MySQL, escrito por Ian Gilfillan
El daño de las tablas es raro al utilizar {{site.data.keyword.mysql}}. Sin embargo, ayuda a saber cómo solucionar el problema cuando se produce.
[Vaya al artículo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.databasejournal.com/features/mysql/article.php/3300511){: new_window}

## Optimización de MySQL: Consultas e índices, escrito por Ian Gilfillan
<!--The database is too slow. Queries are queuing up, backlogs growing, users being refused connection. Management is ready to spend millions on "upgrading" to some other system, when the problem is really that MySQL is simply not being used properly. Badly defined or non-existent indexes are one of the primary reasons for poor performance, and fixing these can often lead to phenomenal improvements.-->
[Vaya al artículo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.databasejournal.com/features/mysql/article.php/1382791){: new_window}

[Otros artículos de {{site.data.keyword.mysql}} de Ian Gilfillan ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.databasejournal.com/article.php/1474351){: new_window}
