---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Reparación de tablas MySQL que no se abren

La reparación de tabla de {{site.data.keyword.mysql}} se maneja de forma individual, pero si está utilizando el tipo de tabla predeterminado {{site.data.keyword.mysql}} de MyISAM (que es el motor de almacenamiento predeterminado a menos que se haya modificado o que se haya especificado de forma distinta), tiene algunas opciones.

1. Puede ejecutar el programa de utilidad myisamchk desde una línea de mandatos para comprobar, reparar u optimizar tablas. Normalmente se ejecuta mientras la base de datos no se está ejecutando. Para obtener más información, consulte [myisamchk ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://dev.mysql.com/doc/refman/5.0/en/myisamchk.html){: new_window}.
2. mysqlcheck es similar en función a myisamchk, pero puede ejecutarse mientras la base de datos está en ejecución. Para obtener más información, consulte [mysqlcheck ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://dev.mysql.com/doc/refman/5.0/en/mysqlcheck.html){: new_window}.
3. Si inicia sesión en la base de datos, también puede ejecutar mandatos SQL que puedan solucionar el problema.

    Mandatos de ejemplo:
    *mysql> optimize table your-tablename
    *mysql> analyze table your-tablename
    *mysql> repair table your-tablename
    Para obtener más información, consulte [mantenimiento de tablas     SQL ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://dev.mysql.com/doc/refman/5.0/en/table-maintenance-sql.html){: new_window}.
4. Si está obteniendo números de errores de {{site.data.keyword.mysql}} y no está seguro de qué son, puede ejecutar el programa de utilidad perror para buscar errores desde la línea de mandatos. Para obtener más información, consulte [perror ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://dev.mysql.com/doc/refman/5.0/en/perror.html){: new_window}.

    Ejemplos:
    *shell> perror 13 64
    *Error code 13: Permission denied
    *Error code 64: Machine is not on the network
