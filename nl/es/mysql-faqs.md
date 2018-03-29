---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Preguntas frecuentes: MySQL

## ¿Cómo puedo supervisar mi servidor MySQL?

_mytop_, una aplicación de Linux, es un supervisor casi en tiempo real (similar al programa de utilidad 'top' de UNIX) que busca específicamente en lo que el servidor de {{site.data.keyword.mysql}} está haciendo. _mytop_ se actualiza cada pocos segundos, por lo que puede obtener un aspecto razonable en el rendimiento de SQL. _mytop_ también puede mostrar una gran cantidad de información. También se presupone que se está conectando al servidor de {{site.data.keyword.mysql}} en el host local con el usuario root y sin contraseña. Las credenciales se pueden cambiar, ya sea en el propio script o en la línea de mandatos.

## ¿Cuál es mi contraseña raíz de MySQL?

* Si el servidor se ha suministrado automáticamente con {{site.data.keyword.mysql}}, la contraseña raíz será la misma que la contraseña raíz del servidor.
* Si Plesk se suministra automáticamente en el servidor, utilice "admin" y la contraseña de administrador para Plesk.
* Si ha instalado {{site.data.keyword.mysql}} a través de origen, RPM, o up2date, las contraseñas de la cuenta raíz inicial estarán vacías. Cualquiera puede conectarse al servidor de {{site.data.keyword.mysql}} como usuario root sin una contraseña y otorgarse todos los privilegios, a menos que establezca la contraseña de usuario root durante o después de la instalación de {{site.data.keyword.mysql}}.

## ¿Cuál es el mejor recurso en línea para obtener información sobre MySQL?

El sitio web de [{{site.data.keyword.mysql}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://dev.mysql.com/doc/){: new_window} tiene un manual de referencia completo con prestaciones de búsqueda disponibles.

La documentación abarca todo, desde la instalación básica, la sintaxis SQL, hasta el uso avanzado como la réplica y la agrupación en clúster. Además, hay traducciones del manual de referencia en alemán, francés, japonés, portugués y ruso.
