---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Configuration de la mise en réseau Riak

Lorsque vous installez Riak sur un serveur {{site.data.keyword.Bluemix}} ayant fait l'objet d'une ingénierie, Riak est lié à l'[adresse IP du réseau privé ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.softlayer.com/about/datacenters/rack-architecture){: new_window}. La liaison de Riak réduit les risques de sécurité liés à la présence d'une instance Riak ouverte accessible exposée au public au moment du déploiement. L'adresse IP liée à Riak est modifiable à tout moment. **Remarque :** Riak ne doit pas être ouvertement exposé à des interfaces publiques sans avoir mis en place des mesures de sécurité supplémentaires afin de limiter les accès externes à l'instance (par exemple, pare-feux et iptables). 
{:shortdesc}

Pour configurer la mise en réseau Riak afin d'établir une liaison à une nouvelle interface, procédez comme suit.

## Liaison de Riak à une nouvelle interface

1. Accédez à la section `riak_core` du fichier `/etc/riak/app.config` dans l'installation.
2. Mettez à jour l'attribut `http{}` de la section `riak_core` afin d'y indiquer la nouvelle adresse IP à laquelle Riak est lié.<br/>`{http, [ {"127.0.0.1", 8098 } ] },`
3. Recherchez le fichier `/etc/vm.args` dans l'installation.
4. Editez l'attribut `-name` du fichier `/etc/vm.args` afin d'y indiquer la nouvelle adresse IP :<br/>`-name riak@127.0.0.1`
5. Redémarrez Riak pour valider les modifications de liaison.

## Etapes suivantes

Les modifications apportées à la liaison impactent toutes les liaisons précédentes à toutes les interfaces associées à l'instance Riak. Après redémarrage, l'adresse IP de liaison est mise à jour et fonctionne correctement. Si la liaison ne s'effectue pas correctement après redémarrage de l'instance Riak, contactez le [Support](/docs/get-support/getstarttssup.html).
