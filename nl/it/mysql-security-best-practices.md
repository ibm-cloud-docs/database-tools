---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Procedure consigliate per la sicurezza di MySQL

Molti utenti {{site.data.keyword.BluSoftlayer_full}} si affidano a {{site.data.keyword.mysql}} per la loro soluzione database. Poiché i database conservano informazioni importanti e a volte sensibili, assicurati di proteggere i database {{site.data.keyword.mysql}} per proteggere le tue informazioni. Le pratiche di sicurezza per {{site.data.keyword.mysql}} dipendono dai requisiti di business e dai bisogni individuali; tuttavia, ci sono alcune procedure con cui consigliamo di iniziare. Assicurati di allinearti con i seguenti suggerimenti per iniziare a proteggere il tuo database {{site.data.keyword.mysql}}.

* Imposta la password {{site.data.keyword.mysql}} root.
* Elimina il database e l'account di test creato durante l'installazione iniziale di {{site.data.keyword.mysql}}.
* Assicurati che sia impostata ogni password dell'account {{site.data.keyword.mysql}} individuale.
* Concedi i privilegi in base alle esigenze. Evita di concedere i privilegi globali inutilmente.
* Non utilizzare caratteri jolly nel valore del nome host associato agli account.
* Esamina periodicamente i database e gli utenti {{site.data.keyword.mysql}} dell'account per assicurarti che le autorizzazioni rimangano accurate.
* Non utilizzare le password nella riga di comando con il comando `shell>mysql -u root - password=somepassword mysql`

**Nota:** utilizza il seguente comando per concedere l'accesso alla riga di comando ad altri utenti per eseguire il pull della password con il comando `shell>ps`. Utilizza il comando `shell>mysql -u root -p mysql` per richiedere invece l'inserimento della password. Questo protegge la tua password.

## Risorse aggiuntive

Esistono molte risorse che forniscono ulteriori dettagli sulla protezione del tuo database {{site.data.keyword.mysql}}. Inizia con le linee guide sulla sicurezza di {{site.data.keyword.mysql}} che si basano sulla versione di {{site.data.keyword.mysql}} sul tuo dispositivo:

* [{{site.data.keyword.mysql}} Version 5.7 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://dev.mysql.com/doc/refman/5.7/en/security.html){: new_window}

Esistono molte altre risorse non gestite da {{site.data.keyword.mysql}} che possono essere d'aiuto. Queste risorse si trovano ricercando "{{site.data.keyword.mysql}} Security" con un qualsiasi motore di ricerca. Poiché le risorse di terze parti non vengono conservate dai creatori di {{site.data.keyword.mysql}}, esegui queste procedure con cautela. Come per tutte le risorse, utilizza siti attendibili e fai riferimento ai siti di supporto e della documentazione ufficiale se possibile.
