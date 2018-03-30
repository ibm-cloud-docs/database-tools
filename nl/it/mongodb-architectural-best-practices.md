---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MongoDB - procedure consigliate per l'architettura

Utilizza le seguenti procedure consigliate per utilizzare {{site.data.keyword.mongodb}} nelle distribuzioni in {{site.data.keyword.cloud}}. Se hai selezionato i server compilati, molte di queste raccomandazioni sono già implementate. 

## Strategia di distribuzione
Quando pianifichi la tua distribuzione di {{site.data.keyword.mongodb}}, devi considerare diverse aree chiave. La più importante è la tua dimensione del dataset prevista e corrente. Queste due aree sono il driver primario per la tua scelta della risorsa del nodo fisica individuale necessaria e che guida i tuoi piani di frammentazione. Devi anche considerare l'importanza dei tuoi dati e quanto sei tollerante della possibilità di perdita e ritardo dei dati (specialmente negli scenari replicati). 

## Dimensionamento della memoria
{{site.data.keyword.mongodb}} (come molte altre applicazioni orientate sui dati) funziona in modo migliore quando il dataset risiede nella memoria. Nulla funziona meglio di un'istanza {{site.data.keyword.mongodb}} che non richiede I/O del disco. Quando possibile, seleziona una piattaforma con più RAM disponibile rispetto alla dimensione del dataset di lavoro. Se il tuo dataset supera la RAM disponibile per un solo nodo, considera di sfruttare la frammentazione. La frammentazione aumenta la quantità di RAM disponibile in un cluster per ospitare il dataset più grande. Pertanto, ottimizza le prestazioni generali della tua distribuzione. Gli errori pagina possono indicare che potresti stare per superare la RAM disponibile nella tua distribuzione. Devi considerare di incrementare la tua RAM disponibile.

## Tipo di disco
Se la velocità non è un problema o se disponi di un dataset più grande rispetto a quello che la tua strategia di memoria può supportare, un tipo di disco appropriato per la tua distribuzione è importante. IOPS è la chiave per selezionare il tuo tipo di disco. Più alto è IOPS, migliori sono le prestazioni di {{site.data.keyword.mongodb}}. Se possibile devono essere utilizzati i dischi locali poiché l'archivio di rete può causare elevata latenza e prestazioni scarse per la tua distribuzione. Si consiglia di utilizzare RAID 10 per gli array del disco.

## CPU
La velocità di clock e il numero di processori disponibili diventa una considerazione se desideri utilizzare un map-reduce. Tuttavia, quando esegui un'istanza {{site.data.keyword.mongodb}} con la maggior parte dei dati in memoria, la velocità di clock può influire sulle prestazioni. Se il tuo sistema è in esecuzione in queste circostanze e desideri ottimizzare le tue operazioni al secondo, prendi in considerazione una strategia di distribuzione che includa una CPU con un'elevata velocità clock/bus.

## Replica
La replica fornisce l'elevata disponibilità dei tuoi dati se un nodo ha un malfunzionamento nel cluster. Si consiglia di effettuare la replica con almeno tre nodi in ogni distribuzione {{site.data.keyword.mongodb}}. La configurazione più comune per la replica con tre nodi è una distribuzione 2x1 che ha due nodi primari in un solo datacenter con un server di backup in un datacenter secondario.


## Frammentazione
Se prevedi che il dataset sia molto grande, ti consigliamo di distribuire una distribuzione {{site.data.keyword.mongodb}} frammentata. Puoi utilizzare la frammentazione per suddividere i tuoi dataset in più nodi. {{site.data.keyword.mongodb}} può automaticamente distribuire i dati tra i nodi nel cluster. Oppure puoi definire una chiave di partizione e creare una frammentazione basata sull'intervallo per tale chiave. La frammentazione può essere utile nello scrivere le prestazioni, per cui è possibile che puoi eseguire la frammentazione anche se il tuo dataset è piccolo ma richiede un numero elevato di aggiornamenti o di inserimenti. Quando distribuisci una serie frammentata, {{site.data.keyword.mongodb}} richiede solo tre istanze del server di configurazione specializzate nei runtime Mongo per tracciare la configurazione di partizione corrente. La perdita di uno di questi nodi comporta che il cluster vada in una modalità di sola lettura solo per la configurazione e richiede che tutti i nodi vengano riportati online prima che possa essere effettuata una qualsiasi modifica alla configurazione.

## Modalità di protezione di scrittura
Esistono diverse modalità di protezione di scrittura che controllano come {{site.data.keyword.mongodb}} gestisce la persistenza dei dati sul disco. È importante considerare quale strategia meglio soddisfi i propri bisogni per le prestazioni e per l'integrità dei dati. Sono disponibili le seguenti modalità di protezione di scrittura:

* **None** – Fornisce una strategia di scrittura deferita che non è bloccante e che aiuta con prestazioni elevate. Tuttavia, c'è una piccola possibilità di errore del nodo e che i dati vengano persi. C'è anche la possibilità che i dati siano scritti in un nodo in un cluster non immediatamente disponibile per tutti i nodi in tale cluster per la consistenza di lettura. La modalità None non fornisce alcuna protezione dei dati in caso di errori di rete. Questa modalità è altamente inaffidabile e viene utilizzata solo quando le prestazioni sono una priorità e l'integrità dei dati non è un problema.
* **Normal** – È il valore predefinito per {{site.data.keyword.mongodb}}. Anche la modalità Normal è una strategia di scrittura deferita non bloccante.  
* **Safe** – Blocca finché {{site.data.keyword.mongodb}} riconosce di aver ricevuto la richiesta di scrittura, ma blocca finché viene eseguita la scrittura. La modalità Safe fornisce un livello maggiore di integrità dei dati e di consistenza di lettura in un cluster.
* **Journal Safe** – Fornisce un'opzione di ripristino per {{site.data.keyword.mongodb}}. La modalità Journal Safe garantisce che i dati vengano riconosciuti e che sia eseguito un aggiornamento journal prima della restituzione.
* **Fsync** – Fornisce il livello di integrità dei dati più elevato e blocca finché non si verifica una scrittura fisica dei dati. L'utilizzo di Fsync crea un calo delle prestazioni e utilizzala solo se l'integrità dei dati è la preoccupazione primaria per la tua applicazione.

## Verifica della distribuzione
10gen dispone di diversi strumenti per aiutarti a caricare il test della tua distribuzione. Uno strumento console, ‘benchrun’, può eseguire le operazioni dall'interno di un controllo di test JavaScript. Benchrun restituisce le informazioni sull'operazione e i numeri di latenza di ogni operazione. Se sono necessarie informazioni più dettagliate sull'istanza {{site.data.keyword.mongodb}}, prendi in considerazione di eseguire il comando `mongostat` o MMS per monitorare la tua distribuzione durante la verifica. Per ulteriori informazioni su questi strumenti, consulta i seguenti riferimenti:

[Panoramica di MongoStat ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://docs.mongodb.org/manual/reference/mongostat/){: new_window}

[Servizio di monitoraggio {{site.data.keyword.mongodb}} di 10gen ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.10gen.com/products/mongodb-monitoring-service){: new_window}

## Installazione
Hai diverse considerazione quando installi {{site.data.keyword.mongodb}} che possono aiutarti a creare una soluzione orientata alle prestazioni e stabile. 10gen consiglia di utilizzare CentOS (64-bit) se possibile. Evita la distribuzione su sistemi operativi a 32-bit e Windows. Questi sistemi forniscono una piattaforma di distribuzione scarsa. I sistemi operativi a 32-bit hanno limiti nella dimensione del file che crea problemi e Windows può causare problemi di prestazioni se la memoria virtuale viene utilizzata dal SO per compensare la mancanza di RAM nella tua distribuzione. Per impostazione predefinita, {{site.data.keyword.cloud_notm}} fornisce sistemi operativi a 64-bit CentOS per tutte le distribuzioni del server compilato.

Inoltre, assicurati di effettuare le seguenti modifiche all'installazione del SO di base per ottimizzare le prestazioni:
* **Imposta Read-Ahead SSD in modo predefinito su 16 blocchi** – Le unità SSD hanno tempi di ricerca eccellenti che consentono la riduzione di Read-Ahead in 16 blocchi. Lo spinning dei dischi può richiedere poco buffer, per cui per questi dischi è impostato su 32 blocchi.
* **noatime** – noatime elimina il bisogno per il sistema di scrivere nel file system i file che sono in lettura. Questo comporta un accesso più veloce ai file e una minore usura del disco.
* **Disattiva NUMA nel BIOS** – Linux, NUMA e {{site.data.keyword.mongodb}} generalmente non funzionano insieme. Se stai eseguendo {{site.data.keyword.mongodb}} su hardware NUMA, si consiglia di disattivarlo (eseguendo con una politica di memoria di interfoliazione). In caso contrario, possono manifestarsi problemi come un rallentamento significativo o o un tempo CPU del sistema elevato.
* **Imposta ulimit** – ulimit è impostato su 64000 per i file aperti e su 32000 per i processi utente. Questi unlimit aiutano a prevenire malfunzionamenti dovuti a una perdita di processi utente e di gestioni file disponibili. 
* **Utilizza ext4** – Ext3 è lento nell'assegnare i file (o rimuoverli). Inoltre, l'accesso a file grandi non è buono con ext3.

**Nota:** per impostazione predefinita, queste modifiche sono impostate su tutti i server {{site.data.keyword.cloud_notm}}.

Si consiglia inoltre che i volumi journal e dati siano volumi fisici distinti. Se le directory journal e dati risiedono su un solo volume fisico, lo svuotamento di journal interrompe l'accesso ai dati e fornisce picchi di elevata latenza nella tua distribuzione {{site.data.keyword.mongodb}}.

## Operazioni
Dopo che una distribuzione {{site.data.keyword.mongodb}} è stata promossa alla produzione, ci sono alcune raccomandazioni per ottimizzare le prestazioni e il monitoraggio. 
* Assicurati che l'agent MMS sia in esecuzione in tutte le istanze di {{site.data.keyword.mongodb}}. Questo aiuta a monitorare l'integrità e le prestazioni della distribuzione. L'agent MMS fornisce dati di debug utili a 10gen durante le interazioni di supporto. 
* Il comando `mongostat` fornisce inoltre le informazioni di runtime sulle prestazione di un nodo {{site.data.keyword.mongodb}}.

Se questi strumenti rilevano dei problemi, la frammentazione o l'indicizzazione possono aiutare a correggere questi problemi di prestazione. 

* Indici -  Crea gli indici per una distribuzione {{site.data.keyword.mongodb}} se gli strumenti di monitoraggio indicano che le query basate sul campo stanno funzionando in modo non ottimale. Per migliorare le prestazioni, utilizza sempre gli indici quando esegui la query dei dati che si basano su campi distinti.
* Frammentazione - Utilizza la frammentazione quando le prestazioni generali del nodo risentono di un dataset operativo molto grande. Assicurati di eseguire la frammentazione prima che l'indicatore sia rosso. Il sistema suddivide in parti solo per la frammentazione nell'inserimento o aggiornamento. Se attendi troppo a lungo a frammentare, puoi avere una distribuzione irregolare. 


