---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MongoDB Monitoring Service (MMS) einrichten

## Übersicht

Nachdem Sie Ihre {{site.data.keyword.mongodb}}-Lösung vollständig eingerichtet haben, können die Hosts in der Replikatgruppe so konfiguriert werden, dass sie mit dem kostenlosen {{site.data.keyword.mongodb}} Monitoring Service (MMS) von 10gen verwendet werden können. Mit diesem Überwachungsservice können Sie detaillierte technische Analysen der replizierten Datenbank anzeigen. Als Erstes benötigen Sie den API-Schlüssel und den geheimen Schlüssel für MMS, die durch die Registrierung eines Kontos auf der [10gen-Website für die MMS-Registrierung ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.10gen.com/mongodb-monitoring-service){: new_window} abgerufen werden können.
{:shortdesc}

**Hinweis:** Diese MMS-Berechtigungsnachweise können bereits für Sie konfiguriert sein, wenn Sie Ihre MMS-Schlüssel oder die Informationen zu Ihrem neuen MMS-Konto bereits bei der Bestellung der {{site.data.keyword.mongodb}}-Lösung eingegeben haben.

Den API-Schlüssel und den geheime Schlüssel von MMS für ein Konto finden Sie auf der [10gen-Website für MMS ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://mms.10gen.com/){: new_window}. Melden Sie sich mit den bereitgestellten Berechtigungsnachweisen an und wählen Sie **Einstellungen** aus, um den Gruppen-**-API-Schlüssel** und den **geheimen Schlüssel** von MMS anzuzeigen.

## Hostkonfiguration

Vor der Konfiguration von MMS müssen Sie den API-Schlüssel und den geheimen Schlüssel auf dem Host aktualisieren. **Hinweis:** Diese Schritte müssen nur auf einem einzigen Host in der Gruppe durchgeführt werden. Dieselben Schritte können auch für mehrere Hosts ausgeführt werden, um MMS-Agenten für Failover-Backups zu aktivieren. Nur ein Agent in einer Gruppe gibt Informationen an den MMS-Service weiter.

1. SSH zu einem der Hosts in der Lösung (Netzadresse und Berechtigungsnachweise) befindet sich im {{site.data.keyword.slportal_full}}.
2. Führen Sie den folgenden Befehl aus und ersetzen Sie dabei die entsprechenden API- und geheimen Schlüssel.

    `# /opt/local/bin/mongoConfigureAuthentication.sh -a -s`

    `Updating the /opt/local/10gen/mms-agent/settings.py file with the`
    `MMS API/secret keys...`

    `Restarting MMS agent...`

    `Shutting down MMS-agent:                                   [  OK  ]`

    `Starting MMS-agent:                                        [  OK  ]`


## MMS-Gruppe konfigurieren

Nachdem die Hosts konfiguriert und die MMS-Agenten erneut gestartet wurden, müssen Sie die MMS-Gruppe auf der 10gen-Website für MMS erneut starten.

1. Melden Sie sich bei der [10gen-Website für MMS ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://mms.10gen.com/){: new_window} an.
2. Wählen Sie **Hosts > Agenten** aus.
3. Stellen Sie sicher, dass sich die konfigurierten Agenten in der Liste befinden. Ein Agent wird für jede Gruppe aufgeführt, die konfiguriert und erneut gestartet wurde.
4. Um einen Host zur Liste hinzuzufügen, wählen Sie **Hosts** aus und klicken Sie auf das **Pluszeichen (+)**.
5. Geben Sie die *private IP-Adresse* des Hosts und die Portnummer für {{site.data.keyword.mongodb}} ein. Die Standardportnummer für MongoDB-Lösungen von SoftLayer ist '27018'.
6. Geben Sie den Benutzernamen 'admin' für die Datenbank und das entsprechende Kennwort ein, das Sie unter **Kennwörter** für die entsprechende Einheit im {{site.data.keyword.slportal}} finden, und wählen Sie dann **Hinzufügen** aus.
  * **Wichtig:** Diese Berechtigungsnachweise sind obligatorisch.

**Hinweis:** Es kann bis zu 30 Minuten dauern, bis die Daten in MMS angezeigt werden.
