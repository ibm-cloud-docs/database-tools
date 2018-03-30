---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Backup di MySQL in Linux

## Copia dalla directory MySQL

Per impostazione predefinita, i database {{site.data.keyword.mysql}} sui server Linux sono archiviati nella seguente directory:

`/var/lib/mysql/`

Se prima hai chiuso il servizio mysqld, puoi copiare i tuoi database in una directory /backup di esempio utilizzando il seguente comando:

`cp –Rp /var/lib/mysql/*.* /backup`

Lo switch –R per il comando cp significa ricorsivo, che puoi voler utilizzare perché ogni database è in una directory separata. Lo switch –p è per le autorizzazioni, che conserva le autorizzazioni di ciò che viene copiato.

Generalmente, arresti il servizio mysqld prima di utilizzare il precedente metodo. Se un database viene copiato mentre sta venendo utilizzato, il backup viene corrotto ed è inutile. Se sei certo che nessuno dei database sta venendo utilizzato al momento, puoi utilizzare il precedente comando.

## Il comando mysqldump

Utilizzi il comando mysqldump per eseguire il backup di database individuali o di tutti i database su un server senza dover arrestare il servizio mysqld. Per via di questa capacità di effettuare i backup mentre mantiene ancora i database sono online, questo metodo è consigliato.

## Database individuali

Il seguente è un comando di esempio che utilizzi per eseguire il backup di un database denominato _'example'_ nella directory /backup mentre sei collegato come root:

`mysqldump example > /backup/example_backup.sql`

A meno che il database sia piccolo, comprimi il backup del database per ridurre la quantità di tempo per trasferire il backup. Il seguente comando comprime il backup del database di esempio:

`tar czvf /backup/example_backup.tar.gz /backup./example_backup.sql`

## Tutti i database

Se hai molti database di cui eseguire il backup, il seguente comando esegue il backup di tutti i database {{site.data.keyword.mysql}} nel tuo server nella directory /backup:

`mysqldump -A > /backup/databases.sql(or --all-databases)`

Lo switch –A (“-all-databases” esegue la stessa funzione) esegue il dump di tutti i database sul server.
