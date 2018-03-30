---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Modifica della directory di dati MySQL in un ambiente simile a Unix

Attieniti alla seguente procedura per modificare la tua directory di dati {{site.data.keyword.mysql}}:

1. Accedi al server utilizzando [PuTTY ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html){: new_window} o il tuo client preferito.

  **Nota:** se stai utilizzando una partizione dedicata per la directory dei dati, assicurati di montare la nuova partizione al posto della directory dei dati originale dopo aver copiato i dati. Il montaggio di una nuova partizione salva le modifiche di configurazione non standard che potrebbero non funzionare per alcune applicazioni.

2. Arresta mysqld ({{site.data.keyword.mysql}} daemon/server). Il processo di avvio e arresto del daemon può essere diverso tra distribuzioni e sistemi operativi differenti.

  **Nota:** {{site.data.keyword.mysql}} deve essere arrestato durante ogni processo che influenza direttamente i file non elaborati.

  `/etc/init.d/mysql stop`
  O
  `/etc/init.d/mysqld, /etc/init.d/mysql-server, /usr/loca/etc/init.d/mysql, /opt/lamp…`

3. Esegui il backup del tuo database prima di effettuare una qualsiasi modifica. Assicurati che il daemon {{site.data.keyword.mysql}} non sia in esecuzione quando effettui copie dirette dei file del database non elaborati. <!--(or be good at flushing and locking)-->

  Se utilizzi cPanel nel server, arrestalo (TailWatch/chkservd primarily) prima del riavvio del daemon. Puoi creare un file temporaneo `/etc/chkserv.d/mysqlisevil` per arrestare 'chkservd' dal riavvio del servizio. Se non hai familiarità con rsync, puoi utilizzare un qualsiasi altro strumento per creare il tuo backup (come ad esempio cp, cpio o tar).

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql.'date +%s'`

4. Crea la directory dei dati e fornisci l'appartenenza all'utente {{site.data.keyword.mysql}} (o a qualsiasi utente specificato nel tuo file delle opzioni globali 'my.cnf'). In questo esempio, viene utilizzata l'ubicazione `/var/lib/mysql-data`, ma puoi utilizzare qualsiasi ubicazione desideri. Se stai aggiungendo un dispositivo disco/logico specificatamente per questo scopo, dovrai anche aggiungere la voce in `/etc/fstab` e montare la directory prima di procedere.

  `chown mysql:mysql /var/lib/mysql-data`

5. Fai una copia finale della directory originale nella nuova directory dei dati {{site.data.keyword.mysql}} (assicurati di mantenere il / di coda alla fine della prima directory):

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql-data`

6. Assicurati che la nuova directory dei dati abbia l'appartenenza corretta, il gruppo/utente {{site.data.keyword.mysql}} predefinito o l'utente specificato nel tuo file delle opzioni globali 'my.cnf'. Se non sei sicuro, puoi utilizzare il seguente comando per l'appartenenza ricorrente della gerarchia completa al gruppo o all'utente {{site.data.keyword.mysql}}.

  `chown -R mysql:mysql /var/lib/mysql-data`

  **Nota:** l'utente {{site.data.keyword.mysql}} deve disporre dell'autorizzazione completa (rwx) alle cartelle del database e dell'autorizzazione di scrittura/lettura ai file log, bin, data, index e form.<br/>
Normalmente, le cartelle del database dispongono di un'autorizzazione di 700 (drwx------) e sono di proprietà di mysql:mysql quando sono in un ambiente host condiviso. L'autorizzazione può essere configurata più liberamente con 755 (drwxr-xr-x) in un ambiente dedicato.

7. Aggiorna il tuo file di configurazione '/etc/my.cnf' in modo che punti alla nuova directory dei dati. 
  **Importante:** esegui il backup di tutto prima di effettuare una qualsiasi modifica al file di configurazione.

  `cp -vp /etc/my.cnf /etc/my.cnf.'date +%s'`<br/>
  `vi /etc/my.cnf`

8. Sostituisci ogni istanza di '/var/lib/mysql' con '/var/lib/mysql-data'. Se non hai una voce datadir, posizionala all'interno della stanza [mysqld].

  `[mysqld]`<br/>
  `user = mysql`<br/>
  `datadir = /var/lib/mysql-data`<br/>
  `socket =  /var/lib/mysql-datal/mysql.sock`<br/>

9. Alcune applicazioni dispongono di configurazione personalizzata e questo documento non può coprirle. È risaputo che alcuni script riscontrano un errore se la directory dei dati non è /var/lib/mysql. Per cui, viene utilizzato un link simbolico per puntare alla nuova ubicazione. <!--(first, moving the old data directory out of the way)-->

  `mv -v /var/lib/mysql /var/lib/mysql.orig`<br/>
  `ln -s /var/lib/mysql-data /var/lib/mysql`<br/>

  Se non desideri creare il link, assicurati di modificare 'mysql.default'_socket e 'mysqli.default'_socket in 'php.ini', arrestare completamente e avviare apache.

10. Avvia il daemon {{site.data.keyword.mysql}}.

  `/etc/init.d/mysql start`

11. Verifica che {{site.data.keyword.mysql}} stia funzionando. Se {{site.data.keyword.mysql}} non risponde, controlla i log degli errori. Ripristina le modifiche se necessario.

  `mysqladmin ping`
