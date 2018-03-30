---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# FAQ: MySQL

## Come posso monitorare il mio server MySQL?

_mytop_, un'applicazione Linux, è un monitoraggio quasi in tempo reale (simile al programma di utilità UNIX 'top') che controlla specificatamente cosa il server {{site.data.keyword.mysql}} stia facendo. _mytop_ si aggiorna ogni pochi secondi in modo che puoi avere un'idea ragionevole delle tue prestazioni SQL. _mytop_ è anche in grado di visualizzare una grande quantità di informazioni. Inoltre presume che ti stai collegando al server {{site.data.keyword.mysql}} su un localhost con l'utente root e senza password. Le credenziali possono essere modificate nello script stesso o nella riga di comando.

## Quale è la mia password root per MySQL?

* Se è stato eseguito il provisioning automatico del server con {{site.data.keyword.mysql}}, la password root è la stessa della password root del server.
* Se è stato eseguito il provisioning automatico di Plesk nel tuo server server, utilizza "admin" e la password admin di Plesk.
* Se hai installato {{site.data.keyword.mysql}} tramite source, RPM o up2date, le password dell'account root iniziali sono vuote. Chiunque può collegarsi al server {{site.data.keyword.mysql}} come root senza una password e gli vengono concessi tutti i privilegi, a meno che non imposti la password root durante o dopo l'installazione di {{site.data.keyword.mysql}}.

## Quale è la migliore risorsa online per avere informazioni su MySQL?

Il sito web [{{site.data.keyword.mysql}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://dev.mysql.com/doc/){: new_window} dispone di un manuale di riferimento completo a tutte le funzionalità di ricerca disponibili.

La documentazione copre ogni cosa, dall'installazione di base, la sintassi SQL, all'utilizzo avanzato come il clustering e la replica. Inoltre, sono presenti traduzioni del manuale di riferimento in tedesco, francese, giapponese, portoghese e russo.
