---
copyright:
  years: 1994, 2017
lastupdated: "2017-10-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Nouveautés de MongoDB ayant fait l'objet d'une ingénierie <!--installations-->

Les modifications suivantes ont été apportées afin d'améliorer les performances des installations {{site.data.keyword.mongodb}} ayant fait l'objet d'une ingénierie. Ces modifications font appel à 10gen pour offrir la meilleure expérience utilisateur possible avec les serveurs ayant fait l'objet d'une ingénierie. 10gen et {{site.data.keyword.cloud}} utilisent divers serveurs Bare Metal comme base de plateforme. <!--{{site.data.keyword.baremetal_short}} provide a consistent high performance set of available resources that cannot be matched in shared resource, multi-tenant platforms.-->  

* **CentOS 6.X as the preferred OS** – 10gen indique que le système d'exploitation CentOS est celui qui offre les meilleures performances et capacités de prise en charge de {{site.data.keyword.mongodb}}. Selon cette recommandation, {{site.data.keyword.cloud_notm}} déploie {{site.data.keyword.mongodb}} exclusivement sur une plateforme CentOS 6.X.

* **SSD read ahead defaults set to 16 blocks** - les unités SSD ayant des temps de recherche excellents, la lecture anticipée peut être définie sur 16 blocs. Les disques rotatifs pouvant nécessiter une légère mise en mémoire tampon, ils sont définis sur 32 blocs.

* **Noatime** - l'ajout de ce paramètre évite au système d'avoir à écrire dans le système de fichiers les fichiers lus, de sorte que l'accès aux fichier est plus rapide et l'usure des disques est moindre.

* **NUMA off in BIOS** - Linux, NUMA et {{site.data.keyword.mongodb}} ne fonctionnent généralement pas ensemble. Si vous exécutez {{site.data.keyword.mongodb}} sur un matériel NUMA, il est recommandé de désactiver NUMA (exécution avec une stratégie de mémoire imbriquée). Des problèmes étranges peuvent se produire, par exemple, des ralentissements importants sur certaines périodes de temps ou un temps UC extrêmement élevé.

* **Ulimit** – ce paramètre est défini sur 64000 pour les fichiers ouverts et 32000 pour les processus utilisateur. Ces valeurs ulimit protègent des échecs dus à une perte de processus utilisateur ou de descripteurs de fichier disponibles.

* **EXT4** – Ext4 est préféré à ext3. Ext3 peut être lent à allouer des fichiers (ou à en supprimer) et l'accès aux gros fichiers est également peu performant.

* **Separate Journal Volume** – selon les préconisation de 10gen, {{site.data.keyword.cloud_notm}} utilise un volume SSD distinct monté pour le journal. Cette option est disponible pour les serveurs des toutes dernières versions ayant fait l'objet d'une ingénierie et évite que la journalisation interfère avec les opérations de lecture/écriture sur le montage de données.

* **MMS Preinstalled** -  MMS est le service de surveillance 10gen fourni gratuitement pour toutes les instances {{site.data.keyword.mongodb}}. Tous les serveurs {{site.data.keyword.cloud_notm}} ayant fait l'objet d'une ingénierie sont préconfigurés avec l'agent MMS.
