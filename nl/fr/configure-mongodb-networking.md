---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Configuration de la mise en réseau MongoDB

## Présentation

Les serveurs {{site.data.keyword.Bluemix}} ayant fait l'objet d'une ingénierie sur lesquels {{site.data.keyword.mongodb}} est installé sont configurés de manière à lier {{site.data.keyword.mongodb}} à l'adresse IP du réseau privé. Cette configuration répond à la recommandation 10gen et permet de réduire les risques de sécurité liés à la présence d'une instance {{site.data.keyword.mongodb}} ouverte accessible exposée au public au moment du déploiement.
{:shortdesc}

## Modification de l'interface liée

{{site.data.keyword.mongodb}} peut être configuré de manière à être lié à n'importe quelle interface en modifiant l'attribut `‘bind_ip’` du fichier `/etc/mongod.conf` dans votre installation, comme illustré ci-dessous :

        # mongo.conf
        bind_ip = 0.0.0.0  

Cet attribut définit la liaison à toutes les interfaces, mais vous pouvez entrer dans cette zone l'adresse IP d'une interface spécifique (disponible dans les détails de votre déploiement). Un redémarrage de l'instance {{site.data.keyword.mongodb}} est nécessaire.

**Important :** N'exposez pas {{site.data.keyword.mongodb}} ouvertement à des interfaces publiques sans avoir mis en place des mesures de sécurité supplémentaires afin de limiter les accès à l'instance (par exemple, pare-feux et iptables).
