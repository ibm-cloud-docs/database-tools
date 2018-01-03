---
copyright:
  years: 1994, 2017
lastupdated: "2017-06-08"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MongoDB

MongoDB es un servidor NoSQL muy completo escalable horizontalmente para satisfacer sus necesidades de servicio de base de datos de clase empresarial. MongoDB se puede pedir de forma gratuita o con una recarga del sistema operativo. Se admiten los siguientes sistemas operativos:

* CentOS 6.x
* RHEL 6.x
* Ubuntu 12.04
* Debian 6.x

Algunos elementos de nota cuando suministra una instalación de SL-MongoDB:

* De forma predeterminada, Mongod (el servicio de MongoDB) está enlazado sólo a la interfaz de red privada. MongoDB se suministra con un usuario administrativo preconfigurado. El nombre de usuario es 'admin' y la contraseña es la misma que la contraseña raíz del servidor.
* Si está pidiendo una Solución de MongoDB, como un clúster de conjunto de réplicas, la contraseña de administrador se establecerá en todo el servidor de MongoDB de la solución al final del proceso de configuración del clúster.

Para obtener más información sobre MongoDB, consulte los enlaces siguientes:

* [Biblioteca de documentos de MongoDB](http://www.mongodb.org/display/DOCS/Home)
* [Foros de MongoDB y soporte de código abierto](https://groups.google.com/forum/?fromgroups#!forum/mongodb-user)
* [The Little Mongo DB Book de Karl Seguin (PDF)](http://openmymind.net/mongodb.pdf)

## ¿Cómo puedo?

* [Configurar la red de MongoDB](configure-mongodb-networking.html)
* [Configurar MongoDB Monitoring Service (MMS) para una Solución de MongoDB](set-mongodb-monitoring-service-mms-mongodb-solution.html)
