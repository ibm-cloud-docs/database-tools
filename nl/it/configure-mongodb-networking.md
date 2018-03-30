---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Configurazione della rete MongoDB

I server compilati da {{site.data.keyword.Bluemix}} con {{site.data.keyword.mongodb}} sono configurati per avere {{site.data.keyword.mongodb}} associato all'indirizzo IP di rete privato. Questo come da raccomandazione di 10gen e serve a minimizzare i rischi di sicurezza ad avere un'istanza {{site.data.keyword.mongodb}} accessibile e aperta esposta pubblicamente alla distribuzione. 
{:shortdesc}

## Modifica dell'interfaccia associata

{{site.data.keyword.mongodb}} può essere configurato per essere associato a una qualsiasi interfaccia modificando l'attributo `‘bind_ip’` nel file `/etc/mongod.conf` nella tua installazione nel seguente modo:

        # mongo.conf
        bind_ip = 0.0.0.0  

Questo attributo modifica il bind in modo che sia disponibile per tutte le interfacce oppure puoi configurare l'indirizzo IP dell'interfaccia specifica in questo campo (disponibile dai tuoi dettagli della distribuzione). È obbligatorio un riavvio dell'istanza {{site.data.keyword.mongodb}}.

**Importante:** non esporre {{site.data.keyword.mongodb}} in modo aperto alle interfacce pubbliche senza alcune altre misure di sicurezza in atto, come firewall o tabelle IP che limitano l'accesso all'interfaccia.
