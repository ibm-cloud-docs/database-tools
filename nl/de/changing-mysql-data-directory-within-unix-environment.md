---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL-Datenverzeichnis in einer UNIX-ähnlichen Umgebung ändern

Führen Sie die folgenden Schritte durch, um das {{site.data.keyword.mysql}}-Datenverzeichnis zu ändern:

1. Melden Sie sich beim Server mithilfe von [PuTTY ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html){: new_window} oder Ihrem bevorzugten Client an.

  **Hinweis:** Wenn Sie eine dedizierte Partition für das Datenverzeichnis verwenden, stellen Sie sicher, dass Sie die neue Partition über eine Mountoperation anstelle des ursprünglichen Datenverzeichnisses bereitstellen, nachdem Sie die Daten hinüber kopiert haben. Durch diese Mountoperation werden vom Standard abweichende Konfigurationsänderungen vermieden, die bei einigen Anwendungen zu Problemen führen könnten.

2. Beenden Sie 'mysqld' ({{site.data.keyword.mysql}}-Dämon/Server). Der Prozess zum Starten und Stoppen des Dämons kann je nach Betriebssystem und Verteilung anders sein.

  **Hinweis:** {{site.data.keyword.mysql}} muss während Prozessen, die sich direkt auf die unformatierten Dateien auswirken, gestoppt werden.

  `/etc/init.d/mysql stop`
  Oder
  `/etc/init.d/mysqld, /etc/init.d/mysql-server, /usr/loca/etc/init.d/mysql, /opt/lamp…`

3. Bevor Sie Änderungen vornehmen, führen Sie ein Backup für die Datenbank durch. Stellen Sie sicher, dass der {{site.data.keyword.mysql}}-Dämon nicht ausgeführt wird, wenn Sie Kopien der unformatierten Datenbankdateien machen. <!--(or be good at flushing and locking)-->

  Wenn Sie cPanel auf dem Server ausführen, stoppen Sie cPanel (primär 'TailWatch'/'chkservd'), bevor der Dämon erneut gestartet wird. Sie können eine temporäre Datei `/etc/chkserv.d/mysqlisevil` erstellen, um zu verhindern, dass 'chkservd' den Service erneut startet. Wenn Sie nicht mit 'rsync' vertraut sind, können Sie das Backup mit einem anderen Tool (wie 'cp', 'cpio' oder 'tar') erstellen.

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql.'date +%s'`

4. Erstellen Sie das Datenverzeichnis und geben Sie das Eigentumsrecht des {{site.data.keyword.mysql}}-Benutzers (bzw. des Benutzers, der in der Datei 'my.cnf' mit globalen Optionen definiert ist) an. In diesem Beispiel wird die Speicherposition `/var/lib/mysql-data` verwendet; Sie können jedoch jede beliebige Position verwenden. Wenn Sie speziell für diesen Zweck eine Platte/eine logische Einheit hinzufügen, dann müssen Sie den entsprechenden Eintrag auch in `/etc/fstab` einfügen und für das Verzeichnis eine Mountoperation durchführen, bevor Sie fortfahren.

  `chown mysql:mysql /var/lib/mysql-data`

5. Erstellen Sie eine endgültige Kopie des Ursprungsverzeichnisses im neuen {{site.data.keyword.mysql}}-Datenverzeichnis (stellen Sie sicher, dass Sie den abschließenden / am Ende des ersten Verzeichnisses beibehalten):

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql-data`

6. Stellen Sie sicher, dass das neue Datenverzeichnis das korrekte Eigentumsrecht aufweist, also entweder den {{site.data.keyword.mysql}}-Standardbenutzer bzw. die Standardgruppe oder den Benutzer, der in der Datei 'my.cnf' mit den globalen Optionen angegeben ist. Wenn Sie unsicher sind, können Sie den folgenden Befehl verwenden, um rekursiv der Eigner für die gesamte Hierarchie des {{site.data.keyword.mysql}}-Benutzers bzw. der Gruppe zu sein.

  `chown -R mysql:mysql /var/lib/mysql-data`

  **Hinweis:** Der {{site.data.keyword.mysql}}-Benutzer muss die vollständige Berechtigung (rwx) für die Datenbankordner haben und über Lese-/Schreibberechtigungen für Protokoll-, Bin-, Daten-, Index- und Formulardateien verfügen.<br/>
In der Regel ist für Datenbankordner die Berechtigung '700' (drwx------) erforderlich und sie müssen in einer gemeinsam genutzten Hosting-Umgebung 'mysql:mysql' angehören. In einer dedizierten Umgebung kann diese Berechtigung etwas liberaler mit '755' (drwxr-xr-x) konfiguriert werden.

7. Aktualisieren Sie die Konfigurationsdatei '/etc/my.cnf' so, dass sie auf das neue Datenverzeichnis verweist. 
  **Wichtig:** Führen Sie ein umfassendes Backup durch, bevor Sie Änderungen an der Konfigurationsdatei vornehmen.

  `cp -vp /etc/my.cnf /etc/my.cnf.'date +%s'`<br/>
  `vi /etc/my.cnf`

8. Ersetzen Sie alle Instanzen von '/var/lib/mysql' durch '/var/lib/mysql-data'. Wenn Sie über keinen Eintrag für das Datenverzeichnis ('datadir') verfügen, platzieren Sie ihn in der Zeilengruppe [mysqld].

  `[mysqld]`<br/>
  `user = mysql`<br/>
  `datadir = /var/lib/mysql-data`<br/>
  `socket =  /var/lib/mysql-datal/mysql.sock`<br/>

9. Einige Anwendungen verfügen über eine angepasste Konfiguration. Nähere Informationen dazu würden jedoch den Rahmen dieses Dokuments sprengen. Für einige Scripts ist bekannt, dass sie fehlschlagen, wenn das Datenverzeichnis nicht '/var/lib/mysql' lautet. Daher wird ein symbolischer Link verwendet, um auf die neue Speicherposition zu verweisen. <!--(first, moving the old data directory out of the way)-->

  `mv -v /var/lib/mysql /var/lib/mysql.orig`<br/>
  `ln -s /var/lib/mysql-data /var/lib/mysql`<br/>

  Wenn Sie den Link nicht erstellen möchten, stellen Sie sicher, dass Sie das 'mysql.default'_-Socket und das 'mysqli.default'_-Socket in 'php.ini' ändern und Apache vollständig stoppen und erneut starten.

10. Starten Sie den {{site.data.keyword.mysql}}-Dämon.

  `/etc/init.d/mysql start`

11. Stellen Sie sicher, dass {{site.data.keyword.mysql}} ordnungsgemäß ausgeführt wird. Wenn {{site.data.keyword.mysql}} nicht reagiert, überprüfen Sie die entsprechenden Fehlerprotokolle. Falls erforderlich, heben Sie die Änderungen wieder auf.

  `mysqladmin ping`
