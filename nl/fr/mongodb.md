---
copyright:
  years: 1994, 2017
lastupdated: "2017-06-08"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MongoDB

MongoDB est un serveur NoSQL, évolutif horizontalement, doté de l'intégralité des fonctions permettant de répondre aux besoins des services de base de données de niveau entreprise. MongoDB peut être commandé gratuitement ou demandé avec un rechargement de système d'exploitation. Les systèmes d'exploitation suivants sont pris en charge :

* CentOS 6.x
* RHEL 6.x
* Ubuntu 12.04
* Debian 6.x

Quelques remarques concernant la mise à disposition d'une installation SL-MongoDB :

* Par défaut, Mongod (service MongoDB) n'est lié qu'à votre interface de réseau privé. MongoDB est mis à disposition avec un administrateur préconfiguré. Son nom d'utilisateur est 'admin' et son mot de passe est le mot de passe root du serveur.
* Si vous commandez une solution MongoDB, tel un cluster de jeux de répliques, votre mot de passe d'administrateur est défini sur tous les serveurs MongoDB de la solution à la fin du processus de configuration du cluster.

Pour plus d'informations sur MongoDB voir les liens suivants :

* [Bibliothèque de documents MongoDB](http://www.mongodb.org/display/DOCS/Home)
* [Forums MongoDB et support Open Source](https://groups.google.com/forum/?fromgroups#!forum/mongodb-user)
* [Ouvrage de Karl Seguin "The Little Mongo DB Book" (PDF)](http://openmymind.net/mongodb.pdf)

## Comment

* [Configurer la mise en réseau MongoDB](configure-mongodb-networking.html)
* [Configurer le service MMS (MongoDB Monitoring Service) pour une solution MongoDB](set-mongodb-monitoring-service-mms-mongodb-solution.html)
