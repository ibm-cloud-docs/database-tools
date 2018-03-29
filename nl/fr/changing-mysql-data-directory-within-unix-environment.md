---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Modification du répertoire de données MySQL dans un environnement de type Unix

Pour modifier votre répertoire de données {{site.data.keyword.mysql}}, procédez comme suit :

1. Connectez-vous au serveur à l'aide de [PuTTY ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html){: new_window} ou de votre client préféré.

  **Remarque :** si vous utilisez une partition dédiée, veillez à monter la nouvelle partition à la place du répertoire de données d'origine après avoir copié les données dans cette partition. Le montage d'une nouvelle partition préserve des modifications de configuration non standard avec lesquelles certaines applications peuvent ne pas fonctionner.

2. Arrêtez mysqld (démon/serveur {{site.data.keyword.mysql}}). Le processus de démarrage et d'arrêt du démon peut varier selon les distributions et systèmes d'exploitation.

  **Remarque :** {{site.data.keyword.mysql}} doit être arrêté pendant la durée de tout processus qui affecte directement des fichiers bruts.

  `/etc/init.d/mysql stop`
  Ou
  `/etc/init.d/mysqld, /etc/init.d/mysql-server, /usr/loca/etc/init.d/mysql, /opt/lamp…`

3. Sauvegardez votre base de données avant d'apporter des modifications. Assurez-vous que le démon {{site.data.keyword.mysql}} n'est pas en cours d'exécution pendant que vous effectuez des copies directes des fichiers de base de données bruts. <!--(or be good at flushing and locking)-->

  Si vous utilisez cPanel sur le serveur, arrêtez cPanel (TailWatch/chkservd primarily) avant redémarrage du démon. Vous pouvez créer un fichier temporaire `/etc/chkserv.d/mysqlisevil` pour empêcher 'chkservd' de redémarrer le service. Si vous n'avez pas l'habitude de rsync, vous pouvez utiliser n'importe quel autre outil pour créer votre sauvegarde (par exemple, cp, cpio ou tar).

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql.'date +%s'`

4. Créez le répertoire de données et indiquez l'utilisateur propriétaire {{site.data.keyword.mysql}} (ou tout autre utilisateur spécifié dans le fichier d'options globales 'my.cnf'). Dans cet exemple, l'emplacement `/var/lib/mysql-data` est utilisé, mais vous pouvez employer tout emplacement qui vous convient. Si vous ajoutez une unité de disque/logique spécialement dans ce but, vous devez également ajouter l'entrée dans `/etc/fstab` et monter le répertoire avant de poursuivre.

  `chown mysql:mysql /var/lib/mysql-data`

5. Effectuez une copie finale du répertoire d'origine dans le nouveau répertoire de données {{site.data.keyword.mysql}} (assurez-vous de conserver les / qui se trouvent à la fin du premier répertoire) :

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql-data`

6. Vérifiez que le nouveau répertoire de données est associé au propriétaire adéquat, à savoir l'utilisateur/groupe {{site.data.keyword.mysql}} par défaut ou l'utilisateur indiqué dans votre fichier d'options globales 'my.cnf'. Si vous ne savez pas, vous pouvez utiliser la commande suivante pour attribuer de manière récursive l'intégralité de la hiérarchie à l'utilisateur et au groupe {{site.data.keyword.mysql}}.

  `chown -R mysql:mysql /var/lib/mysql-data`

  **Remarque :** l'utilisateur {{site.data.keyword.mysql}} doit détenir les droits complets (rwx) sur les dossiers de base de données et les droits de lecture/écriture sur les fichiers bin et les fichiers de journaux, de données, d'index et de formulaire.<br/>
En général, les dossiers de base de données ont le droit 700 (drwx------) et appartiennent à mysql:mysql lorsqu'ils se trouvent dans un environnement d'hébergement partagé. Le droit peut être configuré de manière plus libérale avec 755 (drwxr-xr-x) dans un environnement dédié.

7. Mettez à jour votre fichier de configuration '/etc/my.cnf' de sorte qu'il pointe sur le nouveau répertoire de données. 
  **Important :** Sauvegardez tous les éléments avant d'éditer le fichier de configuration.

  `cp -vp /etc/my.cnf /etc/my.cnf.'date +%s'`<br/>
  `vi /etc/my.cnf`

8. Remplacez toutes les instances de '/var/lib/mysql' par '/var/lib/mysql-data'. Si vous n'avez pas d'entrée datadir, placez-en une dans la section [mysqld].

  `[mysqld]`<br/>
  `user = mysql`<br/>
  `datadir = /var/lib/mysql-data`<br/>
  `socket =  /var/lib/mysql-datal/mysql.sock`<br/>

9. Certaines applications disposent d'une configuration personnalisée et ce document ne les couvre pas. Certains scripts échouent si le répertoire de données n'est pas /var/lib/mysql. Un lien symbolique est donc utilisé pour pointer sur le nouvel emplacement. <!--(first, moving the old data directory out of the way)-->

  `mv -v /var/lib/mysql /var/lib/mysql.orig`<br/>
  `ln -s /var/lib/mysql-data /var/lib/mysql`<br/>

  Si vous ne voulez pas créer le lien, veillez à modifier le socket 'mysql.default'_ et le socket 'mysqli.default'_ dans 'php.ini' et à complètement arrêter er redémarrer Apache.

10. Démarrez le démon {{site.data.keyword.mysql}}.

  `/etc/init.d/mysql start`

11. Vérifiez que {{site.data.keyword.mysql}} fonctionne. Si {{site.data.keyword.mysql}} ne répond pas, consultez le journal des erreurs. Au besoin, annulez les modifications.

  `mysqladmin ping`
