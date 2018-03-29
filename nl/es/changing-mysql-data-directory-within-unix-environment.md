---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Cambio del directorio de datos de MySQL en un entorno similar a Unix

Siga estos pasos para cambiar el directorio de datos de {{site.data.keyword.mysql}}:

1. Inicie sesión en el servidor mediante [PuTTY ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html){: new_window}, o su cliente preferido.

  **Nota:** Si está utilizando una partición dedicada para el directorio de datos, asegúrese de montar la nueva partición en lugar del directorio de datos original después de copiar los datos de nuevo. El montaje de una nueva partición guarda cambios de configuración no estándares con las que no funcionarían algunas aplicaciones.

2. Cierre mysqld (el daemon/servidor de {{site.data.keyword.mysql}}). El proceso para iniciar y detener el daemon puede variar entre diferentes sistemas operativos y distribuciones.

  **Nota:** {{site.data.keyword.mysql}} debe detenerse durante cualquier proceso que afecte directamente a los archivos sin formato.

  `/etc/init.d/mysql stop`
  O
  `/etc/init.d/mysqld, /etc/init.d/mysql-server, /usr/loca/etc/init.d/mysql, /opt/lamp…`

3. Realice una copia de la base de datos antes de realizar ningún cambio. Asegúrese de que el daemon {{site.data.keyword.mysql}} no se esté ejecutando cuando se realizan copias directas de los archivos de base de datos en bruto. <!--(or be good at flushing and locking)-->

  Si utiliza cPanel en el servidor, detenga cPanel (principalmente TailWatch/chkservd) antes de que se reinicie el daemon. Puede crear un archivo temporal `/etc/chkserv.d/mysqlisevil` para detener que 'chkservd' reinicie el servicio. Si no está familiarizado con rsync, puede utilizar cualquier otra herramienta para crear la copia de seguridad (como por ejemplo cp, cpio, o tar).

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql.'date +%s'`

4. Cree el directorio de datos y proporcione la propiedad del usuario de {{site.data.keyword.mysql}} (o cualquier usuario que se especifique en el archivo de opción global 'my.cnf'). En este ejemplo, se utilizará la ubicación `/var/lib/mysql-data`, pero puede utilizar cualquier ubicación que desee. Si está añadiendo un dispositivo de disco/lógico específicamente para este fin, también debe añadir la entrada en `/etc/fstab` y montar el directorio antes de continuar.

  `chown mysql:mysql /var/lib/mysql-data`

5. Realice una copia final del directorio original en el nuevo directorio de datos {{site.data.keyword.mysql}} (asegúrese de mantener la / final al final del primer directorio):

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql-data`

6. Asegúrese de que el nuevo directorio de datos tenga la propiedad correcta, ya sea el usuario/grupo {{site.data.keyword.mysql}} predeterminado o el usuario que ha especificado en el archivo de opción global 'my.cnf'. Si no está seguro, puede utilizar el mandato siguiente para tener de forma recursiva toda la jerarquía en el usuario y grupo de {{site.data.keyword.mysql}}.

  `chown -R mysql:mysql /var/lib/mysql-data`

  **Nota:** El usuario {{site.data.keyword.mysql}} debe tener permiso completo (rwx) a las carpetas de la base de datos y permiso de lectura/escritura en los archivos log, bin, data, index, y form.<br/>
Normalmente, las carpetas de base de datos tienen un permiso de 700 (drwx------) y pueden ser de la propiedad de mysql:mysql, mientras se encuentren en un entorno de alojamiento compartido. El permiso puede configurarse más ampliamente, con 755 (drwxr-xr-x) en un entorno dedicado.

7. Actualice el archivo de configuración '/etc/my.cnf' para que apunte al nuevo directorio de datos. 
  **Importante:** Realice una copia de seguridad de todo antes de realizar ediciones en el archivo de configuración.

  `cp -vp /etc/my.cnf /etc/my.cnf.'date +%s'`<br/>
  `vi /etc/my.cnf`

8. Sustituya cualquier instancia de '/var/lib/mysql' por '/var/lib/mysql-data'. Si no tiene una entrada datadir, colóquela en la stanza [mysqld].

  `[mysqld]`<br/>
  `user = mysql`<br/>
  `datadir = /var/lib/mysql-data`<br/>
  `socket =  /var/lib/mysql-datal/mysql.sock`<br/>

9. Algunas aplicaciones tienen configuración personalizada y este documento no lo puede tratar. Algunos scripts son conocidos por fallar si el directorio de datos no es /var/lib/mysql. Así, un enlace simbólico se utiliza para apuntar a la nueva ubicación. <!--(first, moving the old data directory out of the way)-->

  `mv -v /var/lib/mysql /var/lib/mysql.orig`<br/>
  `ln -s /var/lib/mysql-data /var/lib/mysql`<br/>

  Si no desea crear el enlace, asegúrese de cambiar el socket_'mysql.default' y el socket_'mysqli.default' en 'php.ini' y de detener completamente y de iniciar apache.

10. Inicie el daemon de {{site.data.keyword.mysql}}.

  `/etc/init.d/mysql start`

11. Verifique que {{site.data.keyword.mysql}} funciona. Si {{site.data.keyword.mysql}} no responde, revise los registros de error. Revierta los cambios si es necesario.

  `mysqladmin ping`
