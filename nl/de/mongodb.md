---
copyright:
  years: 1994, 2017
lastupdated: "2017-06-08"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MongoDB

Bei MongoDB handelt es sich um einen umfassend ausgestatteten NoSQL-Server, der horizontal skalierbar ist, um die Anforderungen Ihres auf Unternehmen abgestimmten Datenbankservice zu erfüllen. MongoDB kann kostenfrei bestellt oder im Rahmen eines erneuten Ladens des Betriebssystems angefordert werden. Momentan werden die folgenden Betriebssysteme unterstützt:

* CentOS 6.x
* RHEL 6.x
* Ubuntu 12.04
* Debian 6.x

Nachfolgend finden Sie einige Aspekte, die Sie bei der Bereitstellung einer SL-MongoDB-Installation berücksichtigen sollten:

* Standardmäßig wird Mongod (der MongoDB-Service) nur an Ihre private Netzschnittstelle gebunden. MongoDB wird mit einem vorkonfigurierten Benutzer mit Verwaltungsaufgaben bereitgestellt. Der Benutzername lautet 'admin' und das Kennwort entspricht dem Rootkennwort des Servers.
* Wenn Sie eine MongoDB-Lösung bestellen, beispielsweise einen Replikatgruppencluster, wird das Administratorkennwort am Ende der Clusterkonfiguration auf allen MongoDB-Servern in der Lösung festgelegt.

Weitere Informationen zu MongoDB finden Sie unter den folgenden Links:

* [MongoDB-Dokumentbibliothek](http://www.mongodb.org/display/DOCS/Home)
* [MongoDB-Foren und Open-Source-Unterstützung](https://groups.google.com/forum/?fromgroups#!forum/mongodb-user)
* [Das kleine MongoDB-Buch von Karl Seguin (PDF)](http://openmymind.net/mongodb.pdf)

## Informationen zur Vorgehensweise

* [MongoDB-Netz konfigurieren](configure-mongodb-networking.html)
* [MongoDB Monitoring Service (MMS) für eine MongoDB-Lösung einrichten](set-mongodb-monitoring-service-mms-mongodb-solution.html)
