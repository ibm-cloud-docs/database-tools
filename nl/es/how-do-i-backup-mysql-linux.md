---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Copia de seguridad de MySQL en Linux

## Copiar desde el directorio de MySQL

De forma predeterminada, las bases de datos de {{site.data.keyword.mysql}} en servidores Linux se almacenan en el directorio siguiente:

`/var/lib/mysql/`

Si cerró el servicio de mysqld en primer lugar, puede copiar las bases de datos a un directorio /backup de ejemplo utilizando el mandato siguiente:

`cp –Rp /var/lib/mysql/*.* /backup`

El conmutador –R para el mandato cp significa recurrente, lo cual desea utilizar porque cada base de datos se encuentra en un directorio independiente. El conmutador –p es para permisos, lo que mantiene los permisos de lo que se ha copiado.

Por lo general, cerrará el servicio de mysqld antes de utilizar el método anterior. Si una base de datos se copia mientras se está utilizando, la copia de seguridad se dañará y se quedará sin valor. Si está seguro de que no se está utilizando ninguna de las bases de datos a la vez, puede utilizar el mandato anterior.

## El mandato mysqldump

Utilice el mandato mysqldump para realizar copia de seguridad de las bases de datos individuales y todas las bases de datos del servidor sin tener que cerrar el servicio de mysqld. Este método es el preferido, debido a esta capacidad para realizar copias de seguridad mientras sigue manteniendo las bases de datos en línea.

## Bases de datos individuales

A continuación se muestra un mandato de ejemplo que puede utilizar para realizar copia de seguridad de una base de datos denominada _'example'_ en el directorio /backup mientras ha iniciado sesión como root:

`mysqldump example > /backup/example_backup.sql`

A menos que sea una base de datos pequeña, comprima la copia de seguridad de la base de datos para reducir la cantidad de tiempo de transferencia de la copia. El mandato siguiente comprime la copia de seguridad de la base de datos de ejemplo:

`tar czvf /backup/example_backup.tar.gz /backup./example_backup.sql`

## Todas las bases de datos

Si tiene varias bases de datos de las que hacer copia de seguridad, el mandato siguiente realiza copia de seguridad de todas las bases de datos de {{site.data.keyword.mysql}} del servidor en el directorio /backup:

`mysqldump -A > /backup/databases.sql(or --all-databases)`

El conmutador –A (“-all-databases” realiza la misma función) vuelca todas las bases de datos en el servidor.
