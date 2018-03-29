---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Configuración de redes Riak

Cuando se instala Riak en un servidor de ingeniería de {{site.data.keyword.Bluemix}}, Riak se vincula a la [dirección IP de red privada ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.softlayer.com/about/datacenters/rack-architecture){: new_window}. Enlazar Riak minimiza los riesgos de seguridad de tener una instancia abierta y accesible de Riak expuesta públicamente en el despliegue. En cualquier momento, la dirección IP vinculada a Riak puede modificarse. **Nota:** Riak no debe exponerse abiertamente en interfaces públicas sin otras medidas de seguridad en lugar de limitar el acceso externo a la instancia (por ejemplo, cortafuegos e iptables). 
{:shortdesc}

Complete los pasos siguientes para configurar la red de Riak para enlazar a una nueva interfaz.

## Enlace de Riak a una nueva interfaz

1. Vaya a la sección `riak_core` del archivo `/etc/riak/app.config` en la instalación.
2. Actualice el atributo `http{}` de la sección `riak_core` para reflejar la nueva dirección IP a la que se enlaza Riak.<br/>`{http, [ {"127.0.0.1", 8098 } ] },`
3. Localice el archivo `/etc/vm.args` en la instalación.
4. Edite el atributo `-name` en el archivo `/etc/vm.args` para reflejar la nueva dirección IP:<br/>`-name riak@127.0.0.1`
5. Reinicie Riak para completar los cambios de enlaces.

## Pasos siguientes

Los cambios realizados al enlace afectan a todos los enlaces anteriores a cualquier interfaz asociada con la instancia de Riak. Tras el reinicio, la dirección IP enlazada se actualizará y funcionará correctamente. Si reinicia la instancia de Riak y no resulta en un enlace satisfactorio, póngase en contacto con [Soporte](/docs/get-support/getstarttssup.html).
