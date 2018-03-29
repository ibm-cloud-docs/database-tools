---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Configuración de redes MongoDB

Los servidores diseñados de {{site.data.keyword.Bluemix}} con {{site.data.keyword.mongodb}} instalado se configuran para que {{site.data.keyword.mongodb}} esté enlazado a la dirección IP de red privada. Esto se debe a la recomendación de 10gen, y sirve para minimizar los riesgos de seguridad de tener una instancia accesible y abierta de {{site.data.keyword.mongodb}} expuesta públicamente en el despliegue. 
{:shortdesc}

## Cambiar la interfaz enlazada

{{site.data.keyword.mongodb}} puede configurarse para enlazarse a cualquier interfaz cambiando el atributo `‘bind_ip’` del archivo `/etc/mongod.conf` en la instalación como se muestra:

        # mongo.conf
        bind_ip = 0.0.0.0  

Este atributo cambia el enlace para estar en todas las interfaces, o puede establecer la dirección IP específica de la interfaz en este campo (disponible desde los detalles del despliegue). Se necesita reiniciar la instancia de {{site.data.keyword.mongodb}}.

**Importante:** No exponga {{site.data.keyword.mongodb}} abiertamente en las interfaces públicas sin alguna otra medida de seguridad, como cortafuegos o iptables que limiten el acceso a la instancia.
