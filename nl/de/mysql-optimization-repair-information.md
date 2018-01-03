---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL - Informationen zur Optimierung/Reparatur

## Belegung von Speicher durch MySQL 
Unter den nachfolgenden Links finden Sie einige Informationen darüber, wie der mysqld-Server verwendet wird, sowie Informationen zu zugehörigen mysqld-Variablennamen.
* [Speicherbelegung in MySQL 5.0 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://dev.mysql.com/doc/refman/5.0/en/memory-use.html){: new_window}
* [Speicherbelegung in MySQL 4.1 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://dev.mysql.com/doc/refman/4.1/en/memory-use.html){: new_window}

## Die Informationen zur MySQL-Optimierung umfassen die folgenden Bereiche:
- Übersicht über die Optimierung
- Optimierung von SELECT- und anderen Anweisungen
- Sperrungsprobleme
- Optimierung der Datenbankstruktur
- Optimierung des MySQL-Servers
- Plattenprobleme

[Optimierung in MySQL 5.0 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://dev.mysql.com/doc/refman/5.0/en/optimization.html){: new_window}
[Optimierung in MySQL 4.1 ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link")](http://dev.mysql.com/doc/refman/4.1/en/optimization.html){: new_window}

## MySQL-Servervariablen für bestimmte SQL-Schichten oder Speicherengines
Unter den folgenden Links sind einige der am häufigsten verwendeten Variablen aufgeführt.
[Gehe zu Artikel 1 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.mysqlperformanceblog.com/2006/06/08/mysql-server-variables-sql-layer-or-storage-engine-specific/){: new_window}
[Gehe zu Artikel 2 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://forge.mysql.com/wiki/ServerVariables){: new_window}

## 'Optimierung der mysqld-Variablen' von Ian Gilfillan
Dieser Artikel enthält Informationen zur MySQL-Optimierung, darunter einige Richtlinien zum Festlegen von mysqld-Servervariablen
(key_buffer_size, Variablen für den Abfragecache, table_cache, sort_buffer usw.).
[Gehe zu Artikel ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.databasejournal.com/features/mysql/article.php/3367871){: new_window}

## 'Reparatur beschädigter Datenbanken in MySQL' von Ian Gilfillan
Bei der Verwendung von {{site.data.keyword.mysql}} kommt es in seltenen Fällen zu Beschädigungen von Tabellen. Es ist jedoch hilfreich zu wissen, wie mögliche Probleme behoben werden können.
[Gehe zu Artikel ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.databasejournal.com/features/mysql/article.php/3300511){: new_window}

## 'Optimierung von MySQL: Abfragen und Indizes' von Ian Gilfillan
<!--The database is too slow. Queries are queuing up, backlogs growing, users being refused connection. Management is ready to spend millions on "upgrading" to some other system, when the problem is really that MySQL is simply not being used properly. Badly defined or non-existent indexes are one of the primary reasons for poor performance, and fixing these can often lead to phenomenal improvements.-->
[Gehe zu Artikel ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.databasejournal.com/features/mysql/article.php/1382791){: new_window}

[Weitere {{site.data.keyword.mysql}} Artikel von Ian Gilfillan ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.databasejournal.com/article.php/1474351){: new_window}
