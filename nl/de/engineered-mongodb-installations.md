---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Neuerungen bei technisch optimiertem MongoDB <!--installations-->

Die folgenden Änderungen wurden vorgenommen, um die Leistung optimierter {{site.data.keyword.mongodb}}-Installationen zu verbessern. Im Rahmen dieser Änderungen liefert 10gen die bestmögliche Funktionalität für optimierte Server für Benutzer. 10gen und {{site.data.keyword.cloud}} greifen dabei auf verschiedene {{site.data.keyword.baremetal_short}} zurück, um als Plattformbasis zu dienen. <!--{{site.data.keyword.baremetal_short}} provide a consistent high performance set of available resources that cannot be matched in shared resource, multi-tenant platforms.-->  

* **CentOS 6.X als bevorzugtes Betriebssystem**: Laut 10gen wird die beste Leistung und Unterstützung von {{site.data.keyword.mongodb}} unter dem CentOS-Betriebssystem erreicht. In Hinblick auf diese Empfehlung stellt {{site.data.keyword.cloud_notm}} {{site.data.keyword.mongodb}} ausschließlich auf einer CentOS 6.X-Plattform bereit.

* **Standard für SSD Read-Ahead auf 16 Blöcke setzen**: SSD-Laufwerke verfügen über eine exzellente Suchzeit; daher kann das Read-Ahead auf 16 Blöcke gesetzt werden. Da für klassische Festplatten eine leichte Pufferung erforderlich sein kann, sind für diese Platten 32 Blöcke festgelegt.

* **noatime**: Durch Hinzufügen von 'noatime' wird verhindert, dass das System Daten in das Dateisystem für Dateien schreiben muss, die gelesen werden. Dies bedeutet, dass schneller auf Dateien zugegriffen werden kann und dass es zu weniger Verschleißerscheinungen bei Platten kommt.

* **NUMA aus in BIOS**: Linux, NUMA und {{site.data.keyword.mongodb}} sind nicht miteinander kompatibel. Wenn Sie {{site.data.keyword.mongodb}} mit NUMA-Hardware ausführen, schalten Sie diese aus (Ausführung mit Speicherverschränkung). Es können verschiedene Probleme auftreten, beispielsweise eine extrem verlangsamte Verarbeitungszeit für eine bestimmte Zeit oder eine hohe System-CPU-Zeit.

* **ulimit**: Die Option 'ulimit' ist für offene Dateien auf '64000' und für Benutzerprozesse auf '32000' gesetzt. Diese Grenzwerte verhindern Ausfälle, die durch das Fehlen verfügbarer Dateikennungen oder Benutzerprozesse auftreten können.

* **EXT4**: 'Ext4' ist als Auswahl 'Ext3' vorzuziehen. Mit 'Ext3' kann die Zuordnung (oder Entfernung) von Dateien langsam und die Zugriffszeit innerhalb großer Dateien unzureichend sein.

* **Eigener Journaldatenträger**: Gemäß von Empfehlungen von 10gen verwendet {{site.data.keyword.cloud_notm}} einen eigenen SSD-Datenträger, der für das Journal angehängt wird. Dies steht auf den optimierten Servern am oberen Ende zur Verfügung und verhindert, dass die Journalfunktion Lese-/Schreiboperationen auf dem Datenmount beeinträchtigt.

* **MMS vorinstalliert**: Bei MMS handelt es sich um den Überwachungsservice von 10gen, der für alle {{site.data.keyword.mongodb}}-Instanzen kostenlos bereitgestellt wird. Alle optimierten {{site.data.keyword.cloud_notm}}-Server sind mit dem MMS-Agenten vorkonfiguriert.
