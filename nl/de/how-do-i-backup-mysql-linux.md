---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-15"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Sicherungskopie für MySQL unter Linux erstellen

## Aus dem Verzeichnis 'mysql' kopieren

Standardmäßig werden {{site.data.keyword.mysql}}-Datenbanken auf Linux-Servern im folgenden Verzeichnis gespeichert:

`/var/lib/mysql/`

Wenn Sie den mysqld-Service zuerst beenden, können Sie die Datenbank mithilfe des folgenden Befehls in ein Beispielverzeichnis '/backup' kopieren:

`cp –Rp /var/lib/mysql/*.* /backup`

Der Switch '–R' für den Befehl 'cp' steht für rekursiv. Sie sollten diesen Switch verwenden, da sich jede Datenbank in einem eigenen Verzeichnis befindet. Der Switch '–p' steht für Berechtigungen, wobei die Berechtigungen für das Kopierte verwaltet werden.

In der Regel beenden Sie den mysqld-Service, bevor Sie die oben dargestellte Methode verwenden. Wenn eine Datenbank kopiert wird, während sie aktiv ist, wird das Backup beschädigt und kann nicht mehr verwendet werden. Wenn Sie sicher sind, dass keine der Datenbanken aktuell verwendet wird, können Sie den obigen Befehl verwenden.

## Befehl 'mysqldump'

Mit dem Befehl 'mysqldump' führen Sie ein Backup sowohl von einzelnen Datenbanken als auch von allen Datenbanken auf einem Server durch, ohne dass der mysqld-Service beendet werden muss. Aufgrund der Möglichkeit, Backups durchzuführen, während die Datenbanken weiterhin online sind, ist dies die bevorzugte Methode.

## Einzelne Datenbanken

Nachfolgend finden Sie ein Beispielbefehl, mit dem Sie ein Backup für eine Datenbank namens _'example'_ im Verzeichnis '/backup' durchführen können, während Sie als Benutzer mit Rootberechtigung angemeldet sind:

`mysqldump example > /backup/example_backup.sql`

Wenn es sich nicht um eine kleine Datenbank handelt, wird empfohlen, dass Sie das Datenbankbackup komprimieren, um die Übertragungszeit für das Backup zu reduzieren. Mit dem folgenden Befehl kann das Backup der Beispieldatenbank komprimiert werden:

`tar czvf /backup/example_backup.tar.gz /backup./example_backup.sql`

## Alle Datenbanken

Wenn Sie mehrere Datenbanken sichern möchten, können Sie mit dem folgenden Befehl alle {{site.data.keyword.mysql}}-Datenbanken im Verzeichnis '/backup' des Servers sichern.

`mysqldump -A > /backup/databases.sql(oder --all-databases)`

Mit dem Parameter –A switch ('-all-databases' führt dieselbe Funktion aus) wird für alle Datenbanken ein Speicherauszug auf dem Server erstellt.
