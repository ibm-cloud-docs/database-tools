---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Réparation des tables MySQL qui ne s'ouvrent pas

La réparation des tables {{site.data.keyword.mysql}} est gérée au cas par cas, mis si vous utilisez le type de table {{site.data.keyword.mysql}} par défaut, MyISAM, (qui est le moteur de stockage par défaut sauf modification ou spécification différente), plusieurs options s'offrent à vous.

1. Vous pouvez exécuter l'utilitaire myisamchk à partir d'une ligne de commande pour vérifier, réparer ou optimiser des tables. Cet utilitaire s'exécute normalement tandis que la base de données n'est pas en cours d'exécution. Pour plus d'informations, voir [myisamchk ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://dev.mysql.com/doc/refman/5.0/en/myisamchk.html){: new_window}.
2. mysqlcheck fonctionne sensiblement comme myisamchk, mais il peut s'exécuter alors que la base de données est en cours d'exécution. Pour plus d'informations, voir [mysqlcheck ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://dev.mysql.com/doc/refman/5.0/en/mysqlcheck.html){: new_window}.
3. Si vous vous connectez à la base de données, vous pouvez étalement exécuter des commandes SQL à même de corriger votre problème.

    Exemples de commande :
    *mysql> optimize table your-tablename
    *mysql> analyze table your-tablename
    *mysql> repair table your-tablename
    For more information, see [table maintenance SQL ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://dev.mysql.com/doc/refman/5.0/en/table-maintenance-sql.html){: new_window}.
4. Si vous obtenez des numéros d'erreur {{site.data.keyword.mysql}} dont vous n'êtes pas sûr de la signification, vous pouvez exécuter l'utilitaire perror à partir de la ligne de commande pour rechercher ces erreurs. Pour plus d'informations, voir [perror ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://dev.mysql.com/doc/refman/5.0/en/perror.html){: new_window}.

    Exemples :
    *shell> perror 13 64
    *Error code 13: Permission denied
    *Error code 64: Machine is not on the network
