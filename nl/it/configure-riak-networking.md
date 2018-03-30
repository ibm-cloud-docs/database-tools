---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Configurazione della rete Riak

Quando installi Riak su un server compilato di {{site.data.keyword.Bluemix}}, Riak viene associato all'[indirizzo IP di rete privato ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.softlayer.com/about/datacenters/rack-architecture){: new_window}. Il bind a Riak minimizza i rischi di sicurezza ad avere un'istanza Riak accessibile e aperta esposta pubblicamente alla distribuzione. In qualsiasi momento, l'indirizzo IP associato a Riak può essere modificato. **Nota:** Riak non dovrebbe essere esposto in modo aperto alle interfacce pubbliche senza altre misure di sicurezza in atto per limitare l'accesso esterno all'istanza (ad esempio firewall e tabelle IP). 
{:shortdesc}

Completa la seguente procedura per configurare la rete Riak per eseguire il bind alla nuova interfaccia.

## Bind di Riak a una nuova interfaccia

1. Passa alla sezione `riak_core` del file `/etc/riak/app.config` nell'installazione.
2. Aggiorna l'attributo `http{}` nella sezione `riak_core` per riflettere il nuovo indirizzo IP a cui è associato Riak.<br/>`{http, [ {"127.0.0.1", 8098 } ] },`
3. Individua il file `/etc/vm.args` nell'installazione.
4. Modifica l'attributo `-name` nel file `/etc/vm.args` per riflettere il nuovo indirizzo IP:<br/>`-name riak@127.0.0.1`
5. Riavvia Riak per completare le modifiche al bind.

## Passi successivi

Le modifiche effettuate al bind influenzano tutti i bind precedenti a tutte le interfacce associate all'istanza Riak. Dopo il riavvio, l'indirizzo IP viene associato e funziona correttamente. Se riavvii l'istanza Riak ma si verifica un bind corretto, contatta il [Supporto](/docs/get-support/getstarttssup.html).
