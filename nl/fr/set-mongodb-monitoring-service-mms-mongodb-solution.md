---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Configuration du service de surveillance MongoDB (MMS)

Une fois la solution {{site.data.keyword.mongodb}} terminée, les hôtes du jeu de répliques peuvent être configurés de manière à fonctionner avec le service {{site.data.keyword.mongodb}} Monitoring Service (MMS) gratuit de 10gen. Vous pouvez utiliser ce service de surveillance pour obtenir une analyse technique détaillée de la base de données répliquée. Pour démarrer, vous avez besoin de la clé secrète et de la clé d'API MMS, que vous obtenez en enregistrant un compte sur le site Web d'enregistrement de [10gen MMS ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.10gen.com/mongodb-monitoring-service){: new_window}.
{:shortdesc}

**Remarque :** ces données d'identification MMS sont peut-être déjà configurées si vous avez entré vos clés MMS ou vos nouvelles informations de compte MMS lorsque vous avez commandé la solution {{site.data.keyword.mongodb}}.

La clé secrète et la clé d'API MMS d'un compte sont indiquées sur le site Web de [10gen MMS ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://mms.10gen.com/){: new_window}. Connectez-vous à l'aide des données d'identification fournies et sélectionnez **Paramètres** pour afficher la **clé d'API** et la **clé secrète** du groupe MMS.

## Configuration des hôtes

Avant de configurer MMS, vous devez mettre à jour la clé d'API et la clé secrète sur les hôtes. **Remarque :** cette procédure n'est à effectuer que sur un seul hôte de l'ensemble. La même procédure peut toutefois être effectuée sur plusieurs hôtes pour activer les agents MMS de sauvegarde sur reprise après incident. Un seul agent d'un ensemble communique des informations au service MMS.

1. Utilisez SSH pour accéder à l'un des hôtes de la solution (l'adresse réseau et les données d'identification figurent dans le portail {{site.data.keyword.slportal_full}}.
2. Exécutez la commande suivante, en y insérant les clés d'API et secrète appropriées.

    `# /opt/local/bin/mongoConfigureAuthentication.sh -a -s`

    `Updating the /opt/local/10gen/mms-agent/settings.py file with the`
    `MMS API/secret keys...`

    `Restarting MMS agent...`

    `Shutting down MMS-agent:                                   [  OK  ]`

    `Starting MMS-agent:                                        [  OK  ]`


## Configuration du groupe MMS

Une fois vos hôtes configurés et les agents MMS redémarrés, vous devez redémarrer le groupe MMS sur le site Web 10gen MMS.

1. Connectez-vous au [site Web 10gen MMS ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://mms.10gen.com/){: new_window}.
2. Sélectionnez**Hôtes > Agents**.
3. Vérifiez que les agents configurés figurent dans la liste. Chaque agent configuré et redémarré doit figurer dans la liste.
4. Pour ajouter un hôte à la liste, sélectionnez **Hôtes**, puis cliquez sur le signe **plus (+)** .
5. Entrez l'*adresse IP privée* de l'hôte et le numéro de port pour {{site.data.keyword.mongodb}}. Le numéro de port par défaut des solutions SoftLayer MongoDB est 27018.
6. Entrez le nom d'utilisateur et le mot de passe de l'administrateur de la base de données, qui figurent dans la zone **Passwords** d'un périphérique dans le portail {{site.data.keyword.slportal}}, et sélectionnez **Add**.
  * **Important :** ces données d'identification sont obligatoires.

**Remarque :** jusqu'à 30 minutes peuvent s'écouler avant que des données s'affichent dans MMS.
