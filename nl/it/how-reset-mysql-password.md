---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Reimpostazione della password utente root MySQL

Completa la seguente procedura se devi reimpostare la tua password utente root {{site.data.keyword.mysql}}:

1. Arresta il server mysqld inviando un comando kill (non kill -9) al server mysqld. Il pid viene archiviato in un file .pid, che generalmente di trova nella directory del database {{site.data.keyword.mysql}}:
  * Esempio: `shell> kill cat /your-mysql-data-directory/hostname.pid`
  * In Red Hat puoi anche arrestare il database:
    * Esempio: `shell> service mysqld stop`
    * Devi essere l'utente root Unix o lo stesso utente che esegue il server per arrestare il database.
2. Riavvia mysqld con l'opzione --skip-grant-tables.
3. Collegati al server mysqld:
  * **Opzione 1:** mysql -h hostname mysql e modifica la password con un comando GRANT.
    * Per ulteriori informazioni sui comandi GRANT, consulta [{{site.data.keyword.mysql}} Documentation ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.mysql.com/doc/G/R/GRANT.html){: new_window}
  * **Opzione 2:** `shell> mysqladmin -h hostname -u user password 'new password'`
4. Carica le tabelle dei privilegi utilizzando `shell> mysqladmin -h hostname flush-privileges` o con il comando SQL `mysql> FLUSH PRIVILEGES;`.


**Nota:** dopo aver avviato mysqld con --skip-grant-tables, qualsiasi utilizzo dei comandi GRANT comporta un errore `Unknown command` finché non esegui _FLUSH PRIVILEGES_.*
