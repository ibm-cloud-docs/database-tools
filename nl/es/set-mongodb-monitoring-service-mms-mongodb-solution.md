---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Configuración de MongoDB Monitoring Service (MMS)

## Visión general

Una vez que complete la solución de {{site.data.keyword.mongodb}}, los hosts del conjunto de réplicas se pueden configurar para que trabajen con {{site.data.keyword.mongodb}} Monitoring Service (MMS) libre de 10gen. Puede utilizar este servicio de supervisión para ver un análisis técnico detallado de la base de datos replicada. Necesita la clave API MMS y la Clave secreta para empezar, que se obtiene registrando una cuenta en el [sitio web de registro de MMS de 10gen ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.10gen.com/mongodb-monitoring-service){: new_window}.
{:shortdesc}

**Nota:** Estas credenciales de MMS ya pueden estar configuradas si se han especificado las claves MMS o la nueva información de cuenta de MMS cuando ordenara la solución de {{site.data.keyword.mongodb}}.

La clave API MMS y la Clave secreta para una cuenta se pueden encontrar en el [sitio web de MMS 10gen ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://mms.10gen.com/){: new_window}. Inicie sesión utilizando las credenciales proporcionadas y seleccione **Valores** para revelar la **Clave de API** y la **Clave secreta** del grupo de MMS.

## Configuración de hosts

Antes de configurar MMS, debe actualizar la clave API y la Clave secreta en los hosts. **Nota:** Estos pasos sólo deben realizarse en un único host el conjunto. Sin embargo, los mismos pasos pueden realizarse en varios hosts para habilitar los agentes MMS de copia de seguridad de migración tras error. Solo un agente de un conjunto comunicará la información al servicio MMS.

1. SSH para uno de los hosts de la solución (la dirección de red y las credenciales se pueden encontrar en {{site.data.keyword.slportal_full}}).
2. Ejecute el siguiente mandato, sustituyendo la API y la Clave secreta apropiadas.

    `# /opt/local/bin/mongoConfigureAuthentication.sh -a -s`

    `Actualización del archivo /opt/local/10gen/mms-agent/settings.py con`
    `MMS API/secret keys...`

    `Restarting MMS agent...`

    `Shutting down MMS-agent:                                   [  OK  ]`

    `Starting MMS-agent:                                        [  OK  ]`


## Configuración del Grupo MMS

Después de configurar los hosts y de que se reinicien los agentes de MMS, debe reiniciar el Grupo MMS en el sitio web MMS 10gen.

1. Inicie sesión en el [sitio web MMS 10gen ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://mms.10gen.com/){: new_window}.
2. Seleccione **Hosts > Agentes**.
3. Verifique que los agentes configurados estén en la lista. Un agente está listado para cada uno que se haya configurado y reiniciado.
4. Para añadir un host a la lista, seleccione **Hosts** y pulse **más (+)**.
5. Especifique la *dirección IP privada* del host y el número de puerto para {{site.data.keyword.mongodb}}. El número de puerto predeterminado para las soluciones de SoftLayer MongoDB es 27018.
6. Especifique el nombre de usuario y la contraseña de administrador de base de datos, que se pueden encontrar en **Contraseñas** para un dispositivo en el {{site.data.keyword.slportal}} y seleccione **Añadir**.
  * **Importante:** Estas credenciales son obligatorias.

**Nota:** Pueden pasar hasta 30 minutos antes de que los datos se muestren en MMS.
