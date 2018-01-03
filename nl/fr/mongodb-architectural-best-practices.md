---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MongoDB - Meilleures pratiques en matière d'architecture

Lors de l'utilisation de {{site.data.keyword.mongodb}} dans des déploiements sur {{site.data.keyword.cloud}} appliquez les meilleures pratiques décrites ci-après. Si vous avez sélectionné des serveurs ayant fait l'objet d'une ingénierie, plusieurs de ces préconisations sont déjà implémentées. 

## Stratégie de déploiement

Lorsque vous planifiez le déploiement de {{site.data.keyword.mongodb}}, vous devez tenir compte de plusieurs éléments essentiels. Le plus important concerne la taille actuelle et prévisible de votre jeu de données. Ces deux éléments sont les principaux facteurs qui guident vos choix en matière de besoins en ressources de noeud individuelles et orientent vos plans de fragmentation. Vous devez également tenir compte de l'importance de vos données et de votre degré de tolérance concernant la perte ou le décalage de données acceptable (particulièrement dans les scénarios répliqués). 
## Dimensionnement de la mémoire

{{site.data.keyword.mongodb}} (comme bon nombre d'applications orientées données) est plus performant lorsque le jeu de données réside en mémoire. Rien n'est plus efficace qu'une instance {{site.data.keyword.mongodb}} qui ne nécessite pas d'entrées-sorties de disque. Chaque fois que vous le pouvez, sélectionnez une plateforme disposant de plus de mémoire RAM disponible que la taille de votre jeu de données de travail. Si votre jeu de données dépasse la capacité de mémoire RAM disponible pour un seul noeud, envisagez de bénéficier des avantages de la fragmentation. La fragmentation augmente la quantité de mémoire RAM disponible dans un cluster afin de l'adapter au jeu de données le plus grand. Les performances globales de votre déploiement sont ainsi optimisées. Des défauts de page peuvent être le signe que vous avez dépassé la capacité de mémoire RAM disponible dans votre déploiement. Vous devez envisager d'augmenter la mémoire RAM disponible.

## Type de disque

Si la vitesse n'est pas un souci ou si la taille de votre jeu de données est supérieure à celle que votre stratégie de mémoire disponible est capable de prendre en charge, il est important de choisir un type de disque adapté à votre déploiement. L'E-S/s (opérations d'entrée-sortie par seconde) est un élément clé pour la sélection du type de disque. Plus la valeur d'E-S/s est élevée, meilleures sont les performances de {{site.data.keyword.mongodb}}. Les disques locaux à utiliser si possible en tant que stockage réseau peuvent provoquer d'importants temps d'attente et nuire aux performances de votre déploiement. Il est conseillé d'utiliser des grappes de disques de type RAID 10.

## Unité centrale

La fréquence d'horloge et le nombre de processeurs disponibles sont des éléments à prendre en considération si vous voulez utiliser MapReduce. Cependant, lorsque exécutez une instance {{site.data.keyword.mongodb}} avec la plupart des données en mémoire, la fréquence d'horloge peut avoir des répercussions sur les performances. Si votre système s'exécute dans ces circonstances et que vous voulez optimiser le nombre d'opérations par seconde, prévoyez une stratégie de déploiement qui inclut une unité centrale ayant une fréquence d'horloge/de bus élevée.

## Réplication

La réplication garantit une haute disponibilité de vos données en cas de défaillance d'un noeud de votre cluster. Il est recommandé de répliquer avec au moins trois noeuds dans chaque déploiement {{site.data.keyword.mongodb}}. La configuration la plus courante pour la réplication avec trois noeuds est un déploiement 2x1 contenant deux noeuds principaux dans un même centre de données et un serveur de sauvegarde dans un centre de données secondaire.


## Fragmentation 

Si vous prévoyez un jeu de données volumineux, il est conseillé d'utiliser un déploiement {{site.data.keyword.mongodb}} fragmenté. Vous pouvez utiliser la fragmentation pour partitionner votre jeu de données entre plusieurs noeuds. {{site.data.keyword.mongodb}} peut distribuer automatiquement les données aux divers noeuds du cluster. Sinon, vous pouvez définir une clé de fragment et créer pour cette clé une fragmentation basée sur une plage. La fragmentation améliorant les performances d'écriture, il est envisageable de l'appliquer même avec un petit jeu de données, mais elle nécessite un grand nombre de mises à jour et d'insertions. Lorsque vous déployez un jeu fragmenté, {{site.data.keyword.mongodb}} n'a besoin que de trois instances de serveur de configuration qui sont des contextes d'exécution Mongo spécialisés pour le suivi de la configuration fragmentée. La perte de l'un de ces noeuds provoque le passage du cluster en mode lecture seule uniquement pour la configuration et nécessite que tous les noeuds soient remis en ligne avant toute modification de la configuration.

## Mode sécurité d'écriture

Il existe plusieurs modes de sécurité d'écriture régissant la manière dont {{site.data.keyword.mongodb}} gère la persistance des données sur disque. Il est important de déterminer la stratégie la mieux adaptée à vos besoins en matière d'intégrité des données et de performances. Les modes de sécurité d'écriture disponibles sont les suivants :

* **None** – offre une stratégie d'écriture différée non bloquante favorable à la haute disponibilité. Toutefois, un léger risque de défaillance de noeud et de perte de données subsiste. Il est également possible que des données écrites sur un noeud d'un cluster ne soient pas immédiatement disponibles sur tous les noeuds de ce cluster pour des raisons de cohérence de lecture. Le mode None n'offre aucune protection des données en cas de défaillance du réseau. Ce mode est très peu fiable et il est utilisé uniquement lorsque les performances sont une priorité et que l'intégrité des données n'est pas un facteur essentiel.
* **Normal** – mode par défaut pour {{site.data.keyword.mongodb}}. Le mode Normal est également une stratégie d'écriture différée non bloquante.  
* **Safe** – bloque jusqu'à ce que {{site.data.keyword.mongodb}} accuse réception de la demande d'écriture, mais ne bloque pas jusqu'à écriture effective. Le mode Safe offre un meilleur niveau d'intégrité des données et de cohérence de lecture dans un cluster.
* **Journal Safe** – offre une option de reprise pour {{site.data.keyword.mongodb}}. Le mode Journal Safe garantit que la réception des données est confirmée et qu'une mise à jour du journal est effectuée avant renvoi.
* **Fsync** – offre le niveau d'intégrité des données le plus élevé et bloque jusqu'à écriture physique des données. Le mode Fsync induit une dégradation des performances et ne doit être utilisé que si l'intégrité des données est primordiale pour votre application.

## Test du déploiement

10gen propose plusieurs outils pour vous aider à effectuer un test de charge de votre déploiement. Un outil de console, ‘benchrun’, qui peut exécuter des opérations à partir d'une routine de test JavaScript. Benchrun renvoie des informations sur les opérations ainsi que le temps d'attente de chaque opération. Pour des informations plus détaillées sur l'instance {{site.data.keyword.mongodb}}, exécutez la commande `mongostat` ou MMS afin de surveiller votre déploiement pendant le test. Pour plus d'informations sur ces outils, voir les références suivantes :

[Présentation de MongoStat](http://docs.mongodb.org/manual/reference/mongostat/)

[Service de surveillance {{site.data.keyword.mongodb}} de 10gen](http://www.10gen.com/products/mongodb-monitoring-service)

## Installation

Lorsque vous installez {{site.data.keyword.mongodb}}, plusieurs éléments sont à prendre en compte pour créer une solution stable et orientée sur les performances. 10gen recommande d'utiliser si possible CentOS (64 bits). Evitez les déploiements sur des systèmes d'exploitation on 32 bits et sur les systèmes d'exploitation Windows. Ces systèmes offrent une plateforme de déploiement médiocre. Les limites de taille de fichier associées aux systèmes d'exploitation 32 bits engendrent des problèmes et Windows peut entraîner des problèmes de performances si le système d'exploitation utilise de la mémoire virtuelle pour compenser un manque de mémoire RAM dans votre déploiement. Par défaut, {{site.data.keyword.cloud_notm}} fournit des systèmes d'exploitation CentOS 64 bits pour tous les déploiements de serveur ayant fait l'objet d'une ingénierie.

De plus, veillez à apporter les modifications suivantes à l'installation du système d'exploitation de base afin d'optimiser les performances :
* **Set SSD Read Ahead Defaults to 16 Blocks** – les unités SSD ont des temps de recherche excellents qui permettent de réduire la lecture anticipée à 16 blocs. Les disques rotatifs nécessitant une légère mise en mémoire tampon, ils sont définis sur 32 blocs.
* **noatime** – ce paramètre évite au système d'avoir à écrire dans le système de fichiers les fichiers lus. Ainsi, l'accès aux fichiers est plus rapide et l'usure des disques est moindre.
* **Turn NUMA Off in BIOS** – Linux, NUMA et {{site.data.keyword.mongodb}} ne fonctionnent généralement pas ensemble. Si vous exécutez {{site.data.keyword.mongodb}} sur un matériel NUMA, il est recommandé de désactiver NUMA (exécution avec une stratégie de mémoire imbriquée). Dans le cas contraire, des problème, tels que des ralentissements importants ou des temps d'unité centrale élevés, peuvent se produire.
* **Set ulimit** – ulimit est défini sur 64000 pour les fichiers ouverts et 32000 pour les processus utilisateur. Ces valeurs ulimit protègent des échecs dus à une perte de processus utilisateur ou de descripteurs de fichier disponibles. 
* **Use ext4** – Ext3 est lent à allouer des fichiers (ou à en supprimer). De plus, l'accès aux gros fichiers n'est pas performant avec ext3.

**Remarque :** par défaut, ces modifications sont appliquées sur tous les serveurs {{site.data.keyword.cloud_notm}}.

Il est également recommandé que les volumes Journal et Data soient deux volumes physiques distincts. Lorsque les répertoires Journal et Data résident dans le même volume physique, les vidages de Journal bloquent l'accès aux données et génèrent des pointes de temps d'attente élevés dans votre déploiement {{site.data.keyword.mongodb}}.

## Opérations

Une fois qu'un déploiement {{site.data.keyword.mongodb}} est promu en production, certaines recommandations sont à respecter afin d'optimiser les performances et la surveillance. 
* Vérifiez que l'agent MMS s'exécute sur toutes les instances de {{site.data.keyword.mongodb}}. Il vous aide à surveiller l'état de santé et les performances du déploiement. L'agent MMS fournit à 10gen des données de débogage utiles pendant les interactions du support. 
* La commande `mongostat` fournit également des informations d'exécution relatives aux performances d'un noeud MongoDB.

Si l'un de ces outils détecte des problèmes de performance, la segmentation ou l'indexation peuvent aider à résoudre ces problèmes. 

* Index -  Créez des index pour un déploiement MongoDB si les outils de surveillance signalent que des demandes basées sur des zones affichent de médiocres performances. Pour améliorer les performances, utilisez toujours des index lorsque vous demandez des données basées sur des zones distinctes.
* Segmentation -  Utilisez la segmentation lorsque les performances globales du noeud sont dégradées en raison de l'exploitation d'un jeu de données volumineux. Veillez à segmenter avant qu'il ne soit trop tard. Le système ne divise les blocs que pour la segmentation sur insertion ou mise à jour. Si vous attendez trop pour segmenter, vous risquez d'avoir une distribution non uniforme. 

## Conclusion

Ces meilleures pratiques ne couvrent pas tous les scénarios possibles que vous pourriez rencontrer. Il est toujours préférable d'utiliser l'abonnement 10gen pour accéder directement au support depuis 10gen ou d'utiliser la documentation du site Web MongoDB pour vous aider concernant des problèmes et préoccupations spécifiques.
