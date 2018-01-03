---
copyright: years: 1994, 2017 lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Mudando o diretório de dados do MySQL em um ambiente como o UNIX

Siga estas etapas para mudar seu diretório de dados do MySQL:

1. Efetue login no servidor usando [PuTTY ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html){: new_window} ou seu cliente preferencial.

  **Nota:** se você estiver usando uma partição dedicada para o diretório de dados, certifique-se de montar a nova partição no local do diretório de dados original depois de copiar os dados. Montar uma nova partição salva as mudanças de configuração não padrão com as quais alguns aplicativos podem não funcionar.

2. Encerre o mysqld (daemon/servidor mysql). O processo para iniciar e parar o daemon podem diferir entre os diferentes sistemas operacionais e distribuições.
  **Nota:** o MySQL deve ser interrompido durante qualquer processo que afeta diretamente os arquivos brutos.

  `/etc/init.d/mysql stop`
  Ou
  `/etc/init.d/mysqld, /etc/init.d/mysql-server, /usr/loca/etc/init.d/mysql, /opt/lamp…`

3. Faça backup de seu banco de dados antes de fazer quaisquer mudanças. Certifique-se de que o daemon do MySQL não esteja em execução quando você fizer cópias diretas dos arquivos de banco de dados brutos. <!--(or be good at flushing and locking)-->

  Se você usar o cPanel no servidor, pare o cPanel (principalmente TailWatch/chkservd) antes de o daemon ser reiniciado. É possível criar um arquivo temporário `/etc/chkserv.d/mysqlisevil` para que 'chkservd' pare de reiniciar o serviço. Se você não estiver familiarizado com rsync, será possível usar qualquer ferramenta para criar seu backup (como cp, cpio ou tar).

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql.'date +%s'`

4. Crie o diretório de dados e forneça a propriedade do usuário mysql (ou qualquer usuário especificado em seu arquivo de opções globais 'my.cnf'). Neste exemplo, o local `/var/lib/mysql-data` é usado, mas é possível usar qualquer local desejado. Se você estiver incluindo um disco/dispositivo lógico especificamente para este propósito, também será necessário incluir a entrada em `/etc/fstab` e montar o diretório antes de continuar.

  `chown mysql:mysql /var/lib/mysql-data`

5. Faça uma cópia final do diretório original para o novo diretório de dados mysql (certifique-se de manter o / à direita no final do primeiro diretório):

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql-data`

6. Certifique-se de que o novo diretório de dados tenha a propriedade correta, o usuário/grupo mysql padrão ou o usuário que está especificado em seu arquivo de opções globais 'my.cnf'. Se você não tiver certeza, será possível usar o comando a seguir para possuir recursivamente a hierarquia inteira para o usuário e grupo mysql.

  `chown -R mysql:mysql /var/lib/mysql-data`

  **Nota:** o usuário mysql precisa ter permissão completa (rwx) para as pastas de banco de dados e permissão de leitura/gravação para os arquivos de log, compartimento, dados, índice e formulário.<br/>
Geralmente, as pastas do banco de dados têm uma permissão de 700 (drwx------) e estão sob a propriedade de mysql:mysql enquanto em um ambiente de hospedagem compartilhado. A permissão pode ser mais amplamente configurada com 755 (drwxr-xr-x) em um ambiente dedicado.

7. Atualize seu arquivo de configuração '/etc/my.cnf' para apontá-lo para o novo diretório de dados.
  **Importante:** faça backup de tudo antes de fazer quaisquer edições no arquivo de configuração.

  `cp -vp /etc/my.cnf /etc/my.cnf.'date +%s'`<br/>
  `vi /etc/my.cnf`

8. Substitua qualquer instância de '/var/lib/mysql' por '/var/lib/mysql-data'. Se você não tiver uma entrada datadir, coloque-a dentro da sub-rotina [mysqld].

  `[mysqld]`<br/>
  `user = mysql`<br/>
  `datadir = /var/lib/mysql-data`<br/>
  `socket =  /var/lib/mysql-datal/mysql.sock`<br/>

9. Alguns aplicativos têm configuração customizada e este documento não os abrange. Alguns scripts são conhecidos por falhar se o diretório de dados não é /var/lib/mysql. Portanto, um link simbólico é usado para apontar para o novo local. <!--(first, moving the old data directory out of the way)-->

  `mv -v /var/lib/mysql /var/lib/mysql.orig`<br/>
  `ln -s /var/lib/mysql-data /var/lib/mysql`<br/>

  Se você não desejar criar o link, certifique-se de mudar o soquete 'mysql.default' _e o soquete 'mysqli.default'_ em 'php.ini' e parar e iniciar completamente o Apache.

10. Inicie o daemon do MySQL.

  `/etc/init.d/mysql start`

11. Verifique se mysql está funcionando. Se mysql não responder, revise seus logs de erro. Reverta as mudanças se necessário.

  `mysqladmin ping`
