---
copyright:
  years: 1994, 2017
lastupdated: "2017-10-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Novedades con <!--installations--> MongoDB diseñado

Los siguientes cambios se realizaron para mejorar el rendimiento de las instalaciones de {{site.data.keyword.mongodb}} diseñadas. Estos cambios utilizan 10gen para dar la mejor experiencia de usuario posible con los servidores diseñados. 10gen y {{site.data.keyword.cloud}} utilizan varios {{site.data.keyword.baremetal_short}} para que sirvan como base de la plataforma. <!--{{site.data.keyword.baremetal_short}} provide a consistent high performance set of available resources that cannot be matched in shared resource, multi-tenant platforms.-->  

* **CentOS 6.X como el sistema operativo preferido**: 10gen indica que ha encontrado el mejor rendimiento y capacidad para apoyar {{site.data.keyword.mongodb}} que se encuentra en el sistema operativo CentOS. Con esta recomendación, {{site.data.keyword.cloud_notm}} despliega exclusivamente {{site.data.keyword.mongodb}} en una plataforma CentOS 6.X.

* **La lectura anticipada de SSD establece de forma predeterminada 16 bloques**: Las unidades SSD tienen tiempos de búsqueda excelentes, por lo que la Lectura anticipada se puede establecer en 16 bloques. Los discos giratorios pueden requerir un almacenamiento intermedio ligero, por lo que los discos giratorios se establecen en 32 bloques.

* **Noatime**: La adición del noatime elimina la necesidad del sistema de escribir en el sistema de archivos archivos que se lean, lo que significa un acceso a archivos más rápido y menos desgaste de disco.

* **NUMA desactivado en BIOS**: Linux, NUMA, y {{site.data.keyword.mongodb}} tienden a no funcionar juntos. Si ejecuta {{site.data.keyword.mongodb}} en hardware NUMA, se recomienda que lo desactive (ejecutando con una política de memoria de intercalación). Los problemas pueden manifestarse de formas extrañas, como caídas masivas para períodos de tiempo o tiempo de CPU del sistema alto.

* **Ulimit**: El ulimit se establece en 64000 para archivos abiertos y 32000 para procesos de usuario. Estos límites ayudan a evitar anomalías debido a una pérdida de descriptores de archivos disponibles o procesos de usuario.

* **EXT4**: Ext4 está seleccionado en ext3. Ext3 puede ser lento al asignar archivos (o al eliminarlos) y el acceso a archivos grandes también lo es.

* **Separate Journal Volume**: Bajo la recomendación de 10gen, {{site.data.keyword.cloud_notm}} utiliza un volumen SSD separado que está montado para el diario. Esto está disponible en los servidores diseñados de extremo superior e impide que el registro por diario interfiera con las operaciones de lectura/escritura en el montaje de datos.

* **MMS preinstalado**: MMS es el servicio de supervisión de 10gen que se proporciona de forma gratuita para todas las instancias de {{site.data.keyword.mongodb}}. Todos los servidores diseñados de {{site.data.keyword.cloud_notm}} estarán preconfigurados con el agente de MMS.
