---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MongoDB - Best Practices für die Architektur

Befolgen Sie die folgenden Best Practices bei der Verwendung von {{site.data.keyword.mongodb}} in Bereitstellungen in der {{site.data.keyword.cloud}}. Wenn Sie optimierte Server ausgewählt haben, sind einige dieser Empfehlungen bereits implementiert. 

## Bereitstellungsstrategie
Bei der Planung Ihrer Bereitstellung von {{site.data.keyword.mongodb}} müssen Sie mehrere wichtige Bereiche berücksichtigen. Die wichtigsten Aspekte sind die aktuelle und die erwartete Größe Ihrer Dateien. Diese beiden Bereiche bilden das wichtigste Argument für Ihre Auswahl der Anforderungen für die einzelnen physischen Knotenressourcen und dienen als Leitfaden für Ihre Sharding-Pläne. Sie müssen zudem die Wichtigkeit Ihrer Daten einordnen und wissen, wie tolerant Sie gegenüber der Möglichkeit verlorener oder verzögerter Daten (insbesondere in replizierten Szenarios) sind. 

## Kapazitätsermittlung für Speicher
{{site.data.keyword.mongodb}} (wie viele datenbezogene Anwendungen) funktioniert am besten, wenn sich die Daten im Speicher befinden. Nichts funktioniert so gut wie eine {{site.data.keyword.mongodb}}-Instanz, die keine Platten-E/A benötigt. Wählen Sie, wo immer möglich, eine Plattform, die mehr verfügbares RAM aufweist als die Größe Ihrer Arbeitsdatei. Wenn Ihre Datei das verfügbare RAM für einen einzelnen Knoten übersteigt, sollten Sie Sharding in Betracht ziehen. Beim Sharding wird die Menge von verfügbarem RAM in einem Cluster für die Verarbeitung größerer Dateien erhöht. Dadurch maximieren Sie die Gesamtleistung Ihrer Bereitstellung. Fehlseitenbedingungen können anzeigen, dass das verfügbare RAM in Ihrer Bereitstellung überschritten wurde. Sie sollten in Betracht ziehen, das verfügbare RAM zu erhöhen.

## Plattentyp
Wenn die Geschwindigkeit kein Problem ist oder Sie über eine Datei verfügen, die größer ist, als Ihre verfügbare Speicherstrategie unterstützen kann, ist für Ihre Bereitstellung ein geeigneter Plattentyp wichtig. IOPS (E/A-Operationen pro Sekunde) ist der Schlüssel bei der Auswahl des Plattentyps. Je höher die E/A-Operationen pro Sekunde, desto besser die Leistung von {{site.data.keyword.mongodb}}. Wenn möglich, sollten lokale Festplatten verwendet werden, da Netzspeicher zu einer hohen Latenzzeit und schwachen Leistungen bei der Bereitstellung führen können. Es wird empfohlen, RAID 10 für Plattenarrays zu verwenden.

## CPU
Wenn Sie ein MapReduce-Konzept verwenden möchten, müssen die Taktgeschwindigkeit und die Anzahl der verfügbaren Prozessoren berücksichtigt werden. Wenn Sie jedoch eine {{site.data.keyword.mongodb}}-Instanz ausführen, bei der sich die meisten Daten im Speicher befinden, kann sich die Taktgeschwindigkeit auf die Leistung auswirken. Wenn Ihr System unter diesen Bedingungen ausgeführt wird und Sie die die Operationen pro Sekunden optimieren möchten, sollten Sie auf eine Bereitstellungsstrategie zurückgreifen, die eine CPU mit einer hohen Takt-/Busgeschwindigkeit aufweist.

## Replikation
Die Replikation gewährleistet eine hohe Verfügbarkeit Ihrer Daten, wenn ein Knoten in Ihrem Cluster fehlschlägt. Es wird empfohlen, die Replikation mit mindestens drei Knoten in einer {{site.data.keyword.mongodb}}-Bereitstellung durchzuführen. Die am häufigsten verwendete Konfiguration für eine Replikation mit drei Knoten ist eine 2x1-Bereitstellung, die über zwei primäre Knoten in einem einzelnen Rechenzentrum und einen Sicherungsserver in einem sekundären Rechenzentrum verfügt.


## Sharding
Wenn Sie eine große Datei erwarten, wird empfohlen, dass Sie {{site.data.keyword.mongodb}} mit Sharding bereitstellen. Mit Sharding können Sie Ihre Dateien über mehrere Knoten hinweg aufteilen. {{site.data.keyword.mongodb}} kann die Daten automatisch auf die Knoten im Cluster verteilen. Sie können auch einen Shardschlüssel definieren und bereichsbasiertes Sharding für diesen Schlüssel erstellen. Das Sharding kann die Schreibleistung unterstützen; es ist daher möglich, selbst bei kleinen Dateien, die allerdings viele Aktualisierungen oder Einfügungen benötigen, ein Sharding durchzuführen. Wenn Sie eine Datei bereitstellen, für die ein Sharding durchgeführt wurde, benötigt {{site.data.keyword.mongodb}} nur drei Konfigurationsserverinstanzen, die spezialisierte Mongo-Laufzeiten sind, um die aktuelle Shardkonfiguration zu überwachen. Der Verlust einer dieser Knoten führt dazu, dass der Cluster nur für diese Konfiguration in den schreibgeschützten Modus wechselt und alle Knoten wieder online gebracht werden müssen, bevor Konfigurationsänderungen vorgenommen werden können.

## Schreibsicherheit
Es gibt mehrere Modi für die Schreibsicherheit, die regeln, wie {{site.data.keyword.mongodb}} die persistente Speicherung der Daten auf der Platte gehandhabt wird. Es muss unbedingt überlegt werden, welche Strategie sowohl Ihren Anforderungen an die Datenintegrität als auch an die Leistung am besten entspricht. Es stehen die folgenden Schreibsicherheitsmodi zur Verfügung:

* **Kein**: Stellt eine verzögerte Schreibstrategie bereit, die nicht blockierend ist und sich so positiv auf die Leistung auswirkt. Es besteht jedoch eine geringe Möglichkeit von Knotenfehlern und somit auch von Datenverlust. Außerdem kann es sein, dass Daten, die auf einen Knoten in einem Cluster geschrieben werden, nicht sofort auf allen Knoten in diesem Cluster für konsistentes Lesen verfügbar sind. Der Modus 'Kein' bietet keinen Datenschutz bei Netzausfällen. Dieser Modus ist extrem störanfällig und wird nur verwendet, wenn die Leistung Priorität hat und die Datenintegrität zweitranging ist.
* **Normal**: Ist der Standard für {{site.data.keyword.mongodb}}. Dieser Modus ist eine nicht blockierende verzögerte Schreibstrategie.  
* **Sicher**: Blockiert, bis {{site.data.keyword.mongodb}} den Empfang der Schreibanforderung bestätigt und der Schreibvorgang durchgeführt wird. Dieser Modus stellt eine bessere Ebene der Datenintegrität und Lesekonsistenz in einem Cluster bereit.
* **Sicheres Journal**: Stellt eine Wiederherstellungsoption für {{site.data.keyword.mongodb}} bereit. In diesem Modus wird sichergestellt, dass die Daten bestätigt werden und vor der Rückgabe das Journal aktualisiert wird.
* **Fsync**: Bietet die höchste Ebene der Datenintegrität und blockiert, bis ein physischer Schreibvorgang der Daten durchgeführt wird. Die Verwendung dieses Modus führt jedoch zu einer Verschlechterung der Leistung. Sie sollten ihn daher nur verwenden, wenn die Datenintegrität oberste Priorität für Ihre Anwendung hat.

## Bereitstellung testen
10gen bietet mehrere Tools, mit denen Sie einen Belastungstest für Ihre Bereitstellung durchführen können. Mit dem Konsolentool 'benchrun' können Operationen im Rahmen der JavaScript-Fehlersimulation durchgeführt werden. Das Tool gibt Informationen zu Operationen sowie Latenzzahlen zu den einzelnen Operationen zurück. Wenn detailliertere Informationen zu der {{site.data.keyword.mongodb}}-Instanz benötigt werden, führen Sie den Befehl `mongostat` oder MMS aus, um Ihre Bereitstellung während des Tests zu überwachen. Weitere Informationen zu diesen Tools liefern die folgenden Referenzen:

[MongoStat - Übersicht ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://docs.mongodb.org/manual/reference/mongostat/){: new_window}

[{{site.data.keyword.mongodb}}Monitoring Service von 10gen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.10gen.com/products/mongodb-monitoring-service){: new_window}

## Installation
Bei der Installation von {{site.data.keyword.mongodb}} können Ihnen einige Überlegungen dabei helfen, eine stabile und leistungsorientierte Lösung zu erstellen. 10gen empfiehlt, wenn möglich, die Verwendung von CentOS (64 Bit). Vermeiden Sie eine Bereitstellung unter einem 32-Bit-Betriebssystem und unter Windows-Betriebssystemen. Diese Systeme sind als Plattform nicht für diese Bereitstellung geeignet. 32-Bit-Betriebssysteme haben Dateigrößenbegrenzungen, die Probleme bereiten können, und unter Windows kann es zu Leistungsproblemen kommen, wenn virtueller Speicher vom Betriebssystem als Ersatz für fehlendes RAM in Ihrer Bereitstellung verwendet wird. Standardmäßig bietet {{site.data.keyword.cloud_notm}} CentOS 64-Bit-Betriebssysteme für alle optimierten Serverbereitstellungen.

Stellen Sie außerdem sicher, dass Sie die folgenden Änderungen an der Basisinstallation des Betriebssystem vornehmen, um die Leistung zu maximieren:
* **Standard für SSD Read-Ahead auf 16 Blöcke setzen**: SSD-Laufwerke verfügen über eine exzellente Suchzeit; daher kann das Read-Ahead auf 16 Blöcke gesetzt werden. Da für klassische Festplatten eine leichte Pufferung erforderlich sein kann, sind für diese Platten 32 Blöcke festgelegt.
* **noatime**: Durch Hinzufügen von 'noatime' wird verhindert, dass das System Daten in das Dateisystem für Dateien schreiben muss, die gelesen werden. Dies bedeutet, dass schneller auf Dateien zugegriffen werden kann und dass es zu weniger Verschleißerscheinungen bei Platten kommt.
* **NUMA aus in BIOS**: Linux, NUMA und {{site.data.keyword.mongodb}} sind nicht miteinander kompatibel. Wenn Sie {{site.data.keyword.mongodb}} mit NUMA-Hardware ausführen, sollten Sie diese ausschalten (Ausführung mit Speicherverschränkung). Ansonsten kann es zu Problemen wie einer extreme Verlangsamung bei der Verarbeitungszeit oder einer hohen System-CPU-Zeit kommen.
* **ulimit**: Die Option 'ulimit' ist für offene Dateien auf '64000' und für Benutzerprozesse auf '32000' gesetzt. Diese Grenzwerte verhindern Ausfälle, die durch das Fehlen verfügbarer Dateikennungen oder Benutzerprozesse auftreten können. 
* **ext4 verwenden**: Mit 'Ext3' kann die Zuordnung (oder Entfernung) von Dateien langsam und die Zugriffszeit innerhalb großer Dateien unzureichend sein.

**Hinweis:** Standardmäßig werden diese Änderungen auf allen {{site.data.keyword.cloud_notm}}-Servern angegeben.

Es wird zudem empfohlen, dass es sich bei den Journaldatenträgern und Datenträgern um verschiedene physische Datenträger handelt. Wenn sich die Journal- und Datenverzeichnisse auf einem einzelnen physischen Datenträger befinden, wird durch für das Journal ausgeführte Flushoperationen der Zugriff auf die Daten unterbrochen und es kommt zu Spitzen mit hoher Latenz in Ihrer {{site.data.keyword.mongodb}}-Bereitstellung.

## Operationen
Nachdem eine {{site.data.keyword.mongodb}}-Bereitstellung für die Produktion hochgestuft wurde, gibt es einige Empfehlungen für die Überwachung und Leistungsoptimierung. 
* Stellen Sie sicher, dass der MMS-Agent auf allen Instanzen von {{site.data.keyword.mongodb}} ausgeführt wird. So kann der Allgemeinzustand und die Leistung der Bereitstellung überwacht werden. Der MMS-Agent liefert 10gen während Supportinteraktionen hilfreiche Debugdaten. 
* Mit dem Befehl `mongostat` werden außerdem Laufzeitinformationen zur Leistung eines {{site.data.keyword.mongodb}}-Knotens bereitgestellt.

Wenn eines dieser Tools Leistungsprobleme erkennt, können mithilfe von Sharding oder Indexierung diese Probleme behoben werden. 

* Indizes: Erstellen Sie Indizes für eine {{site.data.keyword.mongodb}}-Bereitstellung, wenn durch die Überwachungstools angegeben wird, dass feldbasierte Abfragen unzureichend funktionieren. Um die Leistung zu verbessern, verwenden Sie beim Abfragen von Daten, die auf bestimmten Feldern basieren, immer Indizes.
* Sharding: Verwenden Sie Sharding, wenn die Gesamtleistung des Knotens aufgrund einer umfangreichen aktiven Datei eingeschränkt ist. Stellen Sie sicher, dass Sie das Sharding durchführen, bevor es zu starken Leistungseinbußen kommt. Das System nimmt nur eine Unterteilung in Blöcke für das Sharding bei Einfügungs- oder Aktualisierungsoperationen vor. Wenn Sie zu lange warten, bis Sie das Sharding durchführen, kann es zu einer ungleichmäßigen Verteilung kommen. 


