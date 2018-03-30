---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Novità con MongoDB compilato <!--installations-->

Sono state effettuate le seguenti modifiche per migliorare le prestazioni delle installazioni {{site.data.keyword.mongodb}} compilate. Queste modifiche utilizzano 10gen per fornire l'esperienza utente il migliore possibile con i server compilati. 10gen e {{site.data.keyword.cloud}} utilizzano vari {{site.data.keyword.baremetal_short}} da utilizzare come base della piattaforma. <!--{{site.data.keyword.baremetal_short}} provide a consistent high performance set of available resources that cannot be matched in shared resource, multi-tenant platforms.-->  

* **CentOS 6.X come SO preferito** – 10gen indica che hanno trovato la migliore capacità e le migliori prestazioni per supportare {{site.data.keyword.mongodb}} nel sistema operativo CentOS. In questa raccomandazione, {{site.data.keyword.cloud_notm}} distribuisce esclusivamente {{site.data.keyword.mongodb}} in una piattaforma CentOS 6.X.

* **Read-Ahead SSD impostato in modo predefinito su 16 blocchi** - Le unità SSD hanno tempi di ricerca eccellenti, per cui Read-Ahead può essere impostato su 16 blocchi. Lo spinning dei dischi può richiedere poco buffer, per cui lo spinning dei dischi è impostato su 32 blocchi.

* **Noatime** - Aggiungendo noatime si elimina il bisogno per il sistema di scrivere nel file system i file che sono in lettura, il che comporta un accesso più veloce ai file e una minore usura del disco.

* **NUMA disattivato nel BIOS** - Linux, NUMA e {{site.data.keyword.mongodb}} tendono a non funzionare insieme. Se esegui {{site.data.keyword.mongodb}} su hardware NUMA, disattivalo (eseguendo con una politica di memoria di interfoliazione). I problemi possono manifestarsi in modi strani, come un rallentamento significativo per lunghi periodi di tempo o un tempo CPU del sistema elevato.

* **Ulimit** – ulimit è impostato su 64.000 per i file aperti e su 32.000 per i processi utente. Questi limiti aiutano a prevenire malfunzionamenti dovuti a una perdita di processi utente e di gestioni file disponibili.

* **EXT4** – Ext4 viene selezionato invece di Ext3. Ext3 può essere lento nell'assegnare i file (o rimuoverli) e anche l'accesso a file grandi non è buono.

* **Volume journal separato** – Nell'avviso di 10gen, {{site.data.keyword.cloud_notm}} utilizza un volume SSD separato montato per il journal. Questo è disponibile sui server compilati più elevati e impedisce al journaling di interferire con le operazioni di lettura/scrittura nel montaggio dei dati.

* **MMS pre-installato** -  MMS è un servizio di monitoraggio 10gen fornito gratuitamente per tutte le istanze {{site.data.keyword.mongodb}}. Tutti i server compilati {{site.data.keyword.cloud_notm}} sono pre-configurati con l'agent MMS.
