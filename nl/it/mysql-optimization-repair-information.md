---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Ottimizzazione/Informazioni di ripristino MySQL

## Come MySQL utilizza la memoria 
I seguenti sono alcuni dei modi in cui il server mysqld utilizza la memoria e i nomi delle variabili mysqld associate.
* [Memory Use MySQL 5.0 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://dev.mysql.com/doc/refman/5.0/en/memory-use.html){: new_window}
* [Memory Use MySQL 4.1 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://dev.mysql.com/doc/refman/4.1/en/memory-use.html){: new_window}

## L'ottimizzaizone di MySQL copre i seguenti elementi:
- Panoramica sull'ottimizzazione
- Ottimizzazione di SELECT e altre istruzioni
- Problemi di blocco
- Ottimizzazione della struttura del database
- Ottimizzazione del server MySQL
- Problemi disco

[Optimization MySQL 5.0 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://dev.mysql.com/doc/refman/5.0/en/optimization.html){: new_window}
[Optimization MySQL 4.1 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://dev.mysql.com/doc/refman/4.1/en/optimization.html){: new_window}

## Variabili server MySQL - A livello SQL o specifiche per il motore di archiviazione.
I seguenti link elencano alcune della variabili più comuni.
[Go to article 1 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.mysqlperformanceblog.com/2006/06/08/mysql-server-variables-sql-layer-or-storage-engine-specific/){: new_window}
[Go to article 2 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://forge.mysql.com/wiki/ServerVariables){: new_window}

## Ottimizzazione delle variabili mysqld di Ian Gilfillan
Consulta questo articolo sull'ottimizzazione di MySQL, incluse alcune linee guida sull'impostazione della variabile del server mysqld.
(key_buffer_size, variabili cache query, table_cache, sort_buffer, etc..)
[Go to article ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.databasejournal.com/features/mysql/article.php/3367871){: new_window}

## Ripristino del danneggiamento del database in MySQL di Ian Gilfillan
Il danneggiamento della tabella è rara quando utilizzi {{site.data.keyword.mysql}}. Tuttavia, è utile sapere come risolvere il problema quando si verifica.
[Go to article ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.databasejournal.com/features/mysql/article.php/3300511){: new_window}

## Ottimizzazione di MySQL: query e indici di Ian Gilfillan
<!--The database is too slow. Queries are queuing up, backlogs growing, users being refused connection. Management is ready to spend millions on "upgrading" to some other system, when the problem is really that MySQL is simply not being used properly. Badly defined or non-existent indexes are one of the primary reasons for poor performance, and fixing these can often lead to phenomenal improvements.-->
[Go to article ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.databasejournal.com/features/mysql/article.php/1382791){: new_window}

[Altri articoli {{site.data.keyword.mysql}} di Ian Gilfillan ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.databasejournal.com/article.php/1474351){: new_window}
