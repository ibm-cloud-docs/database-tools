---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Mejores prácticas de seguridad de PostgreSQL

## Visión general

Muchos usuarios de {{site.data.keyword.BluSoftlayer_full}} se basan en {{site.data.keyword.mysql}} para su solución de base de datos. Dado que las bases de datos alojan varias informaciones importantes y, a veces, confidenciales, se recomienda proteger las bases de datos {{site.data.keyword.mysql}} para proteger su información. Las prácticas de seguridad para {{site.data.keyword.mysql}} dependen de las necesidades individuales y de los requisitos empresariales. Sin embargo, hay buenas prácticas recomendadas para empezar. Asegúrese de que se alinean con los siguientes consejos para obtener una ventaja a la hora de proteger la base de datos {{site.data.keyword.mysql}}.{:shortdesc}

* Establezca la contraseña raíz de {{site.data.keyword.mysql}}.
* Suprima la cuenta y la base de datos de prueba que se crearon durante la instalación inicial de {{site.data.keyword.mysql}}.
* Asegúrese de que esté establecida cada contraseña de cuenta individual de {{site.data.keyword.mysql}}.
* Otorgue privilegios según los necesite. Evite otorgar privilegios globales innecesariamente.
* No utilice [comodines ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://en.wikipedia.org/wiki/Wildcard_character){: new_window} en el valor de nombre de host asociado con cuentas.
* Revise periódicamente los usuarios y las bases de datos {{site.data.keyword.mysql}} de una cuenta para asegurarse de que los permisos siguen siendo precisos.

## Recursos adicionales

Existen varios recursos adicionales no gestionados por {{site.data.keyword.mysql}} que podrían ser de ayuda. Estos recursos se encuentran buscando "Seguridad de {{site.data.keyword.mysql}}" utilizando cualquier motor de búsqueda. Puesto que los recursos de terceros no los mantienen los encargados de {{site.data.keyword.mysql}}, realice estas prácticas con precaución. Al igual que todos los recursos, utilice sitios de confianza y consulte la documentación oficial y los sitios de soporte siempre que sea posible.
