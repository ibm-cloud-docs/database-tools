---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MongoDB - mejores prácticas arquitectónicas

Utilice las siguientes mejores prácticas para utilizar {{site.data.keyword.mongodb}} en los despliegues de {{site.data.keyword.cloud}}. Si ha seleccionado servidores diseñados, varias de estas recomendaciones ya estarán implementadas. 

## Estrategia de despliegue
Al planificar el despliegue de {{site.data.keyword.mongodb}}, debe considerar varias áreas clave. La más importante es el tamaño del conjunto de datos actual y anticipado. Estas dos áreas son el controlador primario para su elección de necesidades de recursos de nodos físicos individuales y guía sus planes de fragmentación. También tiene que considerar la importancia de los datos y la tolerancia que tiene sobre la posibilidad de que los datos se pierdan o se retrasen (especialmente en casos de ejemplo replicados). 

## Tamaño de memoria
{{site.data.keyword.mongodb}} (como muchas aplicaciones orientadas a datos) funciona mejor cuando el conjunto de datos reside en la memoria. Nada funciona mejor que una instancia de {{site.data.keyword.mongodb}} que no necesita E/S de disco. Siempre que sea posible, seleccione una plataforma que tenga más RAM disponible que el tamaño del conjunto de datos de trabajo. Si el conjunto de datos supera la RAM disponible para un único nodo, considere la posibilidad de aprovechar su fragmentación. Fragmentación aumenta la cantidad de RAM disponible en un clúster para acomodar el conjunto de datos más grande. Así, maximiza el rendimiento general del despliegue. Los errores de página pueden indicar que puede estar superando la RAM disponible en su despliegue. Debe considerar aumentar la RAM disponible.

## Tipo de disco
Si la velocidad no es un problema, o si tiene un conjunto de datos mayor que la que puede soportar la estrategia de memoria disponible, es importante un tipo de disco apropiado para el despliegue. IOPS es clave en la selección del tipo de disco. Cuando mayor sea IOPS, mejor será el rendimiento de {{site.data.keyword.mongodb}}. Los discos locales deben utilizarse, si es posible, porque el almacenamiento en red puede causar una latencia alta y un rendimiento deficiente para el despliegue. Se aconseja que utilice RAID 10 para matrices de discos.

## CPU
La velocidad de reloj y el número de procesadores disponibles se convierte en un tema en el que pensar si desea utilizar map-reduce. Sin embargo, al ejecutar una instancia de {{site.data.keyword.mongodb}} con la mayoría de los datos en memoria, la velocidad de reloj puede repercutir en el rendimiento. Si el sistema se ejecuta en estas circunstancias y desea maximizar sus operaciones por segundo, considere la posibilidad de una estrategia de despliegue que incluya una CPU con una alta velocidad de reloj/bus.

## Réplica
La réplica proporciona alta disponibilidad de los datos si falla un nodo en el clúster. Se recomienda que replique con al menos tres nodos en cualquier despliegue de {{site.data.keyword.mongodb}}. La configuración más común para la réplica con tres nodos es un despliegue 2x1 que tenga dos nodos primarios en un único centro de datos con un servidor de seguridad en un centro de datos secundario.


## Fragmentación
Si anticipa un conjunto de datos grande, se recomienda desplegar un despliegue fragmentado de {{site.data.keyword.mongodb}}. Puede utilizar la fragmentación para particionar el conjunto de datos en varios nodos. {{site.data.keyword.mongodb}} puede distribuir automáticamente los datos en los nodos del clúster. O bien, puede definir una clave fragmentada y crear la fragmentación basada en rango para dicha clave. La fragmentación puede ayudar a escribir el rendimiento, por lo que es posible que pueda fragmentar incluso si el conjunto de datos es pequeño pero necesita un número alto de actualizaciones o inserciones. Al desplegar un conjunto fragmentado, {{site.data.keyword.mongodb}} solo requiere tres instancias de servidor de configuración que sean tiempos de ejecución de Mongo especializados para realizar el seguimiento de la configuración fragmentada actual. La pérdida de uno de estos nodos hace que el clúster entre en una modalidad de solo lectura solo para la configuración y requiere que todos los nodos vuelvan a estar en línea antes de que se pueda realizar ningún cambio de configuración.

## Modalidad de grabación segura
Hay varias modalidades de seguridad de escritura que rigen cómo gestiona {{site.data.keyword.mongodb}} la persistencia de los datos en disco. Es importante considerar qué estrategia se adapta mejor a sus necesidades para la integridad de datos y su rendimiento. Tiene disponibles las siguientes modalidades de seguridad de escritura:

* **Ninguno**: Proporciona una estrategia diferida por escrito no de bloqueo que ayuda con el alto rendimiento. Sin embargo, hay una pequeña posibilidad de error de nodo y de pérdida de datos. También está la posibilidad de que los datos que se escriben en un nodo en un clúster no estén disponibles de forma inmediata en todos los nodos del clúster para la coherencia de lectura. La modalidad Ninguno no proporciona ninguna protección de datos para los errores de red. Esta modalidad no es en absoluto fiable y solo se utiliza cuando el rendimiento es una prioridad y la integridad de datos no es un problema.
* **Normal**: Es el valor predeterminado para {{site.data.keyword.mongodb}}. La modalidad Normal también es una estrategia de escritura diferida sin bloqueos.  
* **Seguro**: Bloquea hasta que {{site.data.keyword.mongodb}} reconoce que ha recibido la solicitud de escritura, pero bloquea hasta que se realiza la escritura. La modalidad Seguro proporciona un mejor nivel de integridad de datos y de coherencia de lectura dentro de un clúster.
* **Diario seguro**: Proporciona una opción de recuperación para {{site.data.keyword.mongodb}}. La modalidad Diario seguro se asegura de que se reconozcan los datos y de que se realice la actualización de un Diario antes de regresar.
* **Fsync**: Proporciona el nivel más alto de integridad de datos y bloquea hasta que se produce una escritura física de los datos. El uso de Fsync viene con una degradación en el rendimiento y solo lo utiliza si la integridad de datos es el problema principal para su aplicación.

## Probar el despliegue
10gen tiene varias herramientas para ayudarle a cargar la prueba del despliegue. Una herramienta de consola, ‘benchrun’, puede ejecutar operaciones desde dentro de un arnés de pruebas de JavaScript. Benchrun devuelve información de operaciones y números de latencia para cada operación. Si se necesita información más detallada sobre la instancia de {{site.data.keyword.mongodb}}, considere la posibilidad de ejecutar el mandato `mongostat` o MMS para supervisar el despliegue durante la prueba. Para obtener más información sobre estas herramientas, consulte las referencias siguientes:

[Visión general de MongoStat ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://docs.mongodb.org/manual/reference/mongostat/){: new_window}

[Servicio de supervisión de {{site.data.keyword.mongodb}} de 10gen ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.10gen.com/products/mongodb-monitoring-service){: new_window}

## Instalación
Tiene varias consideraciones al instalar {{site.data.keyword.mongodb}} que pueden ayudarle a crear una solución estable y orientada al rendimiento. 10gen le recomienda que utilice CentOS (64 bits) si es posible. Evite desplegar en sistemas operativos de 32 bits y en sistemas operativos Windows. Estos sistemas proporcionan una plataforma de despliegue deficiente. Los sistemas operativos de 32 bits tienen límites de tamaño de archivos que provocan problemas y Windows puede provocar problemas de rendimiento si la memoria virtual la utiliza el sistema operativo para compensar la falta de RAM en el despliegue. De forma predeterminada, {{site.data.keyword.cloud_notm}} proporciona sistemas operativos CentOS de 64 bits para todos los despliegues de servidor diseñados.

Además, asegúrese de hacer la siguiente modificación a la instalación del sistema operativo base para maximizar el rendimiento:
* **Establezca los valores predeterminados de lectura anticipada de SSD en 16 bloques**: Las unidades SSD tienen tiempos de búsqueda excelentes que permiten reducir la Lectura anticipada a 16 bloques. Los discos giratorios pueden requerir un ligero almacenamiento intermedio, por lo que estos discos se establecen en 32 bloques.
* **noatime**: Noatime elimina la necesidad de que el sistema escriba en el sistema de archivos para los archivos que se van a leer. Esto significa que tiene acceso más rápido a archivos y menos desgaste de disco.
* **Desactive NUMA en BIOS**: Linux, NUMA, y {{site.data.keyword.mongodb}} generalmente no funcionan juntos. Si está ejecutando {{site.data.keyword.mongodb}} en hardware NUMA, se recomienda que lo desactive (en ejecución con una política de memoria de intercalación). Si no lo hace, se pueden dar problemas como ralentizaciones masivas o tiempo de CPU de sistema alto.
* **Establezca ulimit**: El ulimit se establece en 64000 para archivos abiertos y 32000 para procesos de usuario. Estos ulimits evitan anomalías debido a una pérdida de descriptores de archivos o de procesos de usuarios disponibles. 
* **Utilice ext4**: Ext3 es lento en la asignación de archivos (o en su eliminación). Además, el acceso dentro de los archivos grandes es deficiente con ext3.

**Nota:** De forma predeterminada, estas alteraciones se establecen en todos los servidores de {{site.data.keyword.cloud_notm}}.

También se recomienda que los volúmenes de Diario y de Datos sean volúmenes físicos distintos. Si los directorios de Diario y de Datos residen en un único volumen físico, los vaciados del Diario interrumpen el acceso de los datos y proporcionan picos de alta latencia dentro del despliegue de {{site.data.keyword.mongodb}}.

## Operaciones
Una vez que un despliegue de {{site.data.keyword.mongodb}} se promueva a la producción, hay algunas recomendaciones para la optimización de la supervisión y del rendimiento. 
* Asegúrese de que tenga el agente MMS en ejecución en todas las instancias de {{site.data.keyword.mongodb}}. Esto ayuda a supervisar el estado y el rendimiento del despliegue. El agente MMS proporciona datos de depuración útiles a 10gen durante las interacciones de soporte. 
* El mandato `mongostat` también proporciona información de tiempo de ejecución sobre el rendimiento de un nodo {{site.data.keyword.mongodb}}.

Si cualquiera de estas herramientas descubre problemas de rendimiento, la fragmentación o el indexado puede ayudar a corregir estos problemas. 

* Índices: Cree índices para un despliegue de {{site.data.keyword.mongodb}} si las herramientas de supervisión indican que las consultas basadas en campos están funcionando deficientemente. Para ayudar a mejorar el rendimiento, utilice siempre índices al consultar datos basados en campos distintos.
* Fragmentación: Utilice la fragmentación cuando el rendimiento global del nodo sufra debido a un gran conjunto de datos operativos. Asegúrese de fragmentar antes de llegar al color rojo. El sistema divide bloques solo para fragmentar al insertar o al actualizar. Si espera demasiado tiempo para fragmentar, puede tener una distribución desigual. 


