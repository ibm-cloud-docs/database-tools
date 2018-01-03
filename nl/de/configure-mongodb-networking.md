---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MongoDB-Netz konfigurieren

## Übersicht

Für {{site.data.keyword.Bluemix}} optimierte Server, auf denen {{site.data.keyword.mongodb}} installiert ist, sind so konfiguriert, dass {{site.data.keyword.mongodb}} an die private IP-Netzadresse gebunden ist. Durch diese von 10gen empfohlene Bindung werden die Sicherheitsrisiken in Bezug auf eine offene und durch die Bereitstellung öffentlich zugängliche {{site.data.keyword.mongodb}}-Instanz minimiert. {:shortdesc}

## Gebundene Schnittstelle ändern

{{site.data.keyword.mongodb}} kann so konfiguriert werden, dass die Lösung an alle Schnittstellen gebunden werden kann, indem das Attribut `bind_ip` in der Datei `/etc/mongod.conf` in Ihrer Installation wie folgt geändert wird:

        # mongo.conf
        bind_ip = 0.0.0.0  

Durch dieses Attribut gilt die Bindung für alle Schnittstellen. Sie können aber die IP-Adresse der entsprechenden Schnittstelle in diesem Feld angegeben (die aus Ihren Bereitstellungsdetails erkennbar ist). Es ist ein Neustart der {{site.data.keyword.mongodb}}-Instanz erforderlich.

**Wichtig:** Machen Sie {{site.data.keyword.mongodb}} nicht ohne zusätzliche Sicherheitsmaßnahmen, wie Firewalls oder iptables, die den Zugriff auf die Instanz einschränken, für öffentliche Schnittstellen zugänglich.
