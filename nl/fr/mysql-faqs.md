---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Foire aux questions : MySQL

## Comment puis-je surveiller mon serveur MySQL ?

_mytop_, petite application Linux très pratique, est un outil de surveillance en temps quasi réel (semblable à l'utilitaire 'top' d'UNIX) qui observe plus particulièrement le fonctionnement du serveur {{site.data.keyword.mysql}}. _mytop_ s'actualise à intervalles de quelques secondes afin de vous procurer un aperçu pertinent de vos performances SQL. _mytop_ est également capable d'afficher une quantité considérable d'informations. Cet outil suppose également que vous vous connectez au serveur {{site.data.keyword.mysql}} sur le système hôte local avec l'utilisateur root et sans mot de passe. Les données d'identification peuvent être modifiées dans le script lui-même ou sur la ligne de commande.

## Quel est mon mot de passe root pour MySQL ?

* Si le serveur a été mis à disposition automatiquement avec {{site.data.keyword.mysql}}, le mot de passe root est le mot de passe root du serveur.
* Si Plesk est mis à disposition automatiquement sur votre serveur, utilisez le nom d'utilisateur "admin" et le mot de passe d'administrateur de Plesk.
* Si vous avez installé {{site.data.keyword.mysql}} via la source, RPM ou up2date, les mots de passe de compte root initiaux sont vides. Tout le monde peut se connecter au serveur {{site.data.keyword.mysql}} en tant qu'utilisateur root sans mot de passe et bénéficier de tous les privilèges, sauf si vous définissez le mot de passe root pendant ou après l'installation de {{site.data.keyword.mysql}}.

## Quelle est la meilleure ressource en ligne pour obtenir des informations sur MySQL ?

Le [site Web {{site.data.keyword.mysql}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://dev.mysql.com/doc/){: new_window} propose un manuel de référence complet accompagné de fonctionnalités de recherche.

La documentation couvre tous les domaines, de l'installation de base, en passant par la syntaxe SQL, jusqu'aux utilisations avancées telles que la réplication et la mise en cluster. De plus, il existe des traductions du manuel de référence en allemand, français, japonais, portugais et russe.
