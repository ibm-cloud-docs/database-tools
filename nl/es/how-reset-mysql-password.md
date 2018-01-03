---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Restablecimiento de contraseña de usuario root de MySQL

Complete los pasos siguientes si necesita restablecer la contraseña del usuario root de {{site.data.keyword.mysql}}:

1. Anote el servidor mysqld enviando un kill (not kill -9) al servidor mysqld. El pid se almacena en un archivo .pid, que normalmente se encuentra en el directorio de bases de datos de {{site.data.keyword.mysql}}:
  * Ejemplo: `shell> kill cat /your-mysql-data-directory/hostname.pid`
  * En Red Hat, también puede detener la base de datos:
    * Ejemplo: `shell> service mysqld stop`
    * Debe ser el usuario root de Unix o el mismo usuario que ejecuta el servidor para detener la base de datos.
2. Reinicie mysqld con la opción --skip-grant-tables.
3. Conéctese al servidor de mysqld:
  * **Opción 1:** mysql -h hostname mysql y cambie la contraseña con un mandato GRANT.
    * Para obtener más información sobre mandatos GRANT, consulte la Documentación de [{{site.data.keyword.mysql}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.mysql.com/doc/G/R/GRANT.html){: new_window}
  * **Opción 2:** `shell> mysqladmin -h hostname -u user password 'new password'`
4. Cargue las tablas de privilegios utilizando `shell> mysqladmin -h hostname flush-privileges` o con el mandato SQL `mysql> FLUSH PRIVILEGES;`.


**Nota:** Después de iniciar mysqld con --skip-grant-tables, cualquier uso de mandatos GRANT dará un error `Mandato desconocido` hasta que ejecute _FLUSH PRIVILEGES_.*
