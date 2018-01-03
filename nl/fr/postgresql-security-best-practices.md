---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Meilleures pratiques en matière de sécurité PostgreSQL

## Présentation

Bon nombre d'utilisateurs d'{{site.data.keyword.BluSoftlayer_full}} s'appuient sur {{site.data.keyword.mysql}} pour leur solution de base de données. Etant données que les bases de données abritent diverses informations importantes et, parfois, sensibles, nous vous recommandons de sécuriser vos bases de données {{site.data.keyword.mysql}} afin de protéger vos informations. Les pratiques en matière de sécurité pour {{site.data.keyword.mysql}} dépendent des besoins individuels et des impératifs métier. Il existe toutefois des pratiques à privilégier pour démarrer. Assurez-vous de respecter les conseils suivants pour prendre une longueur d'avance s'agissant de la sécurité de votre base de données {{site.data.keyword.mysql}}.{:shortdesc}

* Définissez le mot de passe root {{site.data.keyword.mysql}}.
* Supprimez la base de données et le compte de test créés au moment de l'installation initiale de {{site.data.keyword.mysql}}.
* Vérifiez que chaque mot de passe de compte {{site.data.keyword.mysql}} individuel est défini.
* Accordez des privilèges en fonction des besoins. Evitez d'accorder inutilement des privilèges globaux.
* N'utilisez pas de [caractères génériques ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://en.wikipedia.org/wiki/Wildcard_character){: new_window} dans la valeur de nom d'hôte associée aux comptes.
* Vérifiez régulièrement les bases de données et les utilisateurs {{site.data.keyword.mysql}} d'un compte pour vous assurer que les droits accordés sont toujours pertinents.

## Ressources supplémentaires

Il existe plusieurs ressources supplémentaires non gérées par {{site.data.keyword.mysql}} qui peuvent également vous aider. Ces ressources sont accessibles en recherchant "Sécurité {{site.data.keyword.mysql}}" à l'aide d'un moteur de recherche. Les ressources de tiers n'étant pas gérées par les développeurs de {{site.data.keyword.mysql}}, mettez en oeuvre ces pratiques avec prudence. Comme pour toutes les ressources, passez par des sites dignes de confiance et reportez-vous à la documentation officielle et aux sites de support chaque fois que possible.
