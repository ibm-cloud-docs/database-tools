---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Häufige Fragen: MySQL

## Wie kann der MySQL-Server überwacht werden?

Mit der Linux-Anwendung _mytop_ kann eine echtzeitnahe Überwachung (ähnlich wie beim UNIX-Dienstprogramm 'top') durchgeführt werden, die sich insbesondere auf das Verhalten des {{site.data.keyword.mysql}}-Servers konzentriert. _mytop_ wird alle paar Sekunden aktualisiert, sodass Sie einen angemessenen Überblick über die SQL-Leistung erhalten. Mit _mytop_ können auch umfangreiche Informationen angezeigt werden. Bei der Verwendung der Anwendung wird zudem angenommen, dass Sie eine Verbindung zum {{site.data.keyword.mysql}}-Server über 'localhost' als Rootbenutzer ohne Kennwort herstellen. Berechtigungsnachweise können entweder direkt im Script oder in der Befehlszeile geändert werden.

## Wie lautet mein Rootkennwort für MySQL?

* Wenn der Server automatisch mit {{site.data.keyword.mysql}} bereitgestellt wurde, entspricht das Rootkennwort dem Rootkennwort des Servers.
* Wenn Plesk automatisch auf dem Server bereitstellt wird, verwenden Sie 'admin' und das Administratorkennwort für Plesk.
* Wenn Sie {{site.data.keyword.mysql}} über Quellcode, RPM oder 'up2date' installiert haben, sind die ursprünglichen Kennwörter für die Benutzerkonten mit Rootberechtigung leer. Somit kann jeder auf den {{site.data.keyword.mysql}}-Server ohne Kennwort als Rootbenutzer zugreifen und erhält alle Berechtigungen, es sei denn, Sie legen das Rootkennwort während oder nach der Installation von {{site.data.keyword.mysql}} fest.

## Was ist die beste Onlineressource mit Informationen zu MySQL?

Auf der [{{site.data.keyword.mysql}}-Website ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://dev.mysql.com/doc/){: new_window} finden Sie umfassende Referenzhandbücher mit Suchfunktionalität.

Die Dokumentation umfasst alle Themen von der Basisinstallation über die SQL-Syntax bis zu komplexeren Funktionen wie Replikation und Clustering. Darüber hinaus stehen Übersetzungen der Referenzhandbücher in Deutsch, Französisch, Japanisch, Portugiesisch und Russisch zur Verfügung.
