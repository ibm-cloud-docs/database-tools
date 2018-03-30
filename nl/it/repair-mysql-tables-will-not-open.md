---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Ripristino delle tabelle MySQL che non si aprono

Il ripristino della tabella {{site.data.keyword.mysql}} è gestito caso per caso, ma se stai utilizzando il tipo di tabella {{site.data.keyword.mysql}} predefinito di MyISAM (che è il motore di archiviazione predefinito a meno che non sia stato modificato o specificato diversamente), hai alcune opzioni.

1. Puoi eseguire il programma di utilità myisamchk da una riga di comando per controllare, ripristinare o ottimizzare le tabelle. Viene normalmente eseguito mentre il database non è in esecuzione. Per ulteriori informazioni, consulta [myisamchk ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://dev.mysql.com/doc/refman/5.0/en/myisamchk.html){: new_window}.
2. mysqlcheck funziona in modo simile a myisamchk, ma può essere eseguito mentre il database è in esecuzione. Per ulteriori informazioni, consulta [mysqlcheck ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://dev.mysql.com/doc/refman/5.0/en/mysqlcheck.html){: new_window}.
3. Se accedi al database, puoi anche utilizzare i comandi SQL che possono risolvere il tuo problema.

    Comandi di esempio
    *mysql> ottimizza la tabella your-tablename
    *mysql> analizza la tabella your-tablename
    *mysql> ripristina la tabella your-tablename
    Per ulteriori informazioni, consulta [table maintenance SQL ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://dev.mysql.com/doc/refman/5.0/en/table-maintenance-sql.html){: new_window}.
4. Se stai ricevendo i numeri di errore {{site.data.keyword.mysql}} e non sei sicuro di cosa siano, puoi eseguire il programma di utilità perror per ricercare gli errori dalla riga di comando. Per ulteriori informazioni, consulta [perror ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://dev.mysql.com/doc/refman/5.0/en/perror.html){: new_window}.

    Esempi:
    *shell> perror 13 64
    *Codice di errore 13: autorizzazione negata
    *Codice di errore 64: la macchina non è nella rete
