---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Configurazione di MMS (MongoDB Monitoring Service)

Dopo aver completato la tua soluzione {{site.data.keyword.mongodb}}, gli host nella serie di repliche possono essere configurati per utilizzare {{site.data.keyword.mongodb}} Monitoring Service (MMS) gratuito di 10gen. Puoi utilizzare questo servizio di monitoraggio per visualizzare un'analisi tecnica dettagliata del database replicato. Per iniziare hai bisogno della chiave API MMS e della chiave del segreto per iniziare, che si ottengono registrando un account in [10gen MMS registration website ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.10gen.com/mongodb-monitoring-service){: new_window}.
{:shortdesc}

**Nota:** queste credenziali MMS potrebbero già essere impostate se hai immesso le tue chiavi MMS nelle informazioni del tuo nuovo account MMS quando hai ordinato la tua soluzione {{site.data.keyword.mongodb}}.

La chiave API MMS e la chiave del segreto per un account possono essere trovate in [10gen MMS website ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://mms.10gen.com/){: new_window}. Accedi utilizzando le credenziali fornite e seleziona **Settings** per mostrare **API Key** e **Secret Key** del gruppo MMS.

## Configurazione degli host

Prima di configurare MMS, devi aggiornare la chiave API e del segreto negli host. **Nota:** questa procedura deve essere eseguita solo per un host nella serie. Tuttavia, la stessa procedura può essere eseguita su più host per abilitare gli agent MMS di backup di failover. Soltanto un agent in una serie non comunica mai le informazioni al servizio MMS.

1. Utilizza SSH per collegarti a uno degli host nella soluzione (le credenziali e l'indirizzo di rete possono essere trovati in {{site.data.keyword.slportal_full}}.
2. Immetti il seguente comando, sostituendo le chiavi del segreto e API appropriate.

    `# /opt/local/bin/mongoConfigureAuthentication.sh -a -s`

    `Updating the /opt/local/10gen/mms-agent/settings.py file with the`
    `MMS API/secret keys...`

    `Restarting MMS agent...`

    `Shutting down MMS-agent:                                   [  OK  ]`

    `Starting MMS-agent:                                        [  OK  ]`


## Configurazione del gruppo MMS

Dopo aver configurato i tuoi host e aver riavviato gli agent MMS, devi riavviare il gruppo MMS nel sito web MMS 10gen.

1. Accedi a [10gen MMS website ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://mms.10gen.com/){: new_window}.
2. Seleziona **Hosts > Agents**.
3. Verifica che gli agent configurati siano nell'elenco. Viene elencato un agent per ognuno che è stato configurato e riavviato.
4. Per aggiungere un host a un elenco, seleziona **Hosts** e fai clic su **plus (+)** .
5. Immetti l'*indirizzo IP privato* dell'host e il numero di porta di {{site.data.keyword.mongodb}}. Il numero di porta predefinito per le soluzioni SoftLayer MongoDB è 27018.
6. Immetti la password e il nome utente admin del database, che possono essere trovati in **Passwords** per un dispositivo in {{site.data.keyword.slportal}} e seleziona **Add**.
  * **Importante:** queste credenziali sono obbligatorie.

**Nota:** ci possono volere fino a 30 minuti prima che i dati vengano visualizzati in MMS.
