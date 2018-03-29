---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL-Rootbenutzerkennwort zurücksetzen

Führen Sie die folgenden Schritte aus, wenn Sie Ihr {{site.data.keyword.mysql}}-Rootbenutzerkennwort zurücksetzen müssen:

1. Inaktivieren Sie den mysqld-Server, indem Sie den Befehl 'kill' (nicht 'kill -9') an den mysqld-Server senden. Die persistente ID wird in einer PID-Datei gespeichert, die sich für gewöhnlich im {{site.data.keyword.mysql}}-Datenbankverzeichnis befindet:
  * Beispiel: `shell> kill cat /ihr_mysql-datenverzeichnis/hostname.pid`
  * In Red Hat können Sie die Datenbank auch stoppen:
    * Beispiel: `shell> service mysqld stop`
    * Sie müssen entweder ein UNIX-Rootbenutzer oder derselbe Benutzer sein, unter dem der Server ausgeführt wird, um die Datenbank zu stoppen.
2. Starten Sie den mysqld-Server mit der Option '--skip-grant-tables'.
3. Stellen Sie eine Verbindung zum mysqld-Server her:
  * **Option 1:** 'mysql -h hostname mysql' und das Kennwort mit einem GRANT-Befehl ändern.
    * Weitere Informationen zu GRANT-Befehlen finden Sie in der [{{site.data.keyword.mysql}}-Dokumentation ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.mysql.com/doc/G/R/GRANT.html){: new_window}.
  * **Option 2:** `shell> mysqladmin -h hostname -u user password 'neues Kennwort'`.
4. Laden Sie die Berechtigungstabellen mit `shell> mysqladmin -h hostname flush-privileges` oder mit dem SQL-Befehl `mysql> FLUSH PRIVILEGES;`.


**Hinweis:** Nachdem Sie den mysqld-Server mit '--skip-grant-tables' gestartet haben, erhalten Sie bei der Verwendung von GRANT-Befehlen solange einen Fehler des Typs `Unknown command` (Unbekannter Befehl), bis Sie _FLUSH PRIVILEGES_ ausführen.*
