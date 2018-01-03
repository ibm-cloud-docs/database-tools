---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 在类似 Unix 的环境中更改 MySQL 数据目录

要更改 MySQL 数据目录，请执行以下步骤：

1. 使用 [PuTTY ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html){: new_window} 或您的首选客户机登录到服务器。

  **注：**如果要将专用分区用于数据目录，请确保在复制原始数据目录的数据后，安装新分区来取代原始数据目录。通过装入新分区，可保存某些应用程序可能不会使用的非标准配置更改。

2. 关闭 mysqld (mysql daemon/server)。用于启动和停止守护程序的进程可能因操作系统和分发版的不同而有所不同。
  **注：**在执行任何会直接影响原始文件的进程期间，必须停止 MySQL。

  `/etc/init.d/mysql stop`
  或
  `/etc/init.d/mysqld, /etc/init.d/mysql-server, /usr/loca/etc/init.d/mysql, /opt/lamp…`

3. 在进行任何更改之前，请先备份数据库。直接复制原始数据库文件<!--(or be good at flushing and locking)-->时，确保 MySQL 守护程序未在运行。

  如果在服务器上使用 cPanel，请先停止 cPanel（主要是 TailWatch/chkservd），然后再重新启动守护程序。可以创建临时文件 `/etc/chkserv.d/mysqlisevil` 来阻止“chkservd”重新启动服务。如果对 rsync 不熟悉，可以使用其他任何工具来创建备份（例如，cp、cpio 或 tar）。

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql.'date +%s'`

4. 创建数据目录并提供 mysql 用户（或者在“my.cnf”全局选项文件中指定的任何用户）所有权。在本例中，使用了位置 `/var/lib/mysql-data`，但您可以使用所需的任何位置。如果要添加专用于此目的的磁盘/逻辑设备，那么还需要将该条目添加到 `/etc/fstab` 中并安装目录，然后再继续。

  `chown mysql:mysql /var/lib/mysql-data`

5. 生成原始目录数据的最终副本并保存到新的 mysql 目录中（确保在第一个目录末尾保留尾部 /）：

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql-data`

6. 确保新的数据目录拥有正确的所有权：缺省 mysql 用户/组或“my.cnf”全局选项文件中指定的用户。如果不确定，可以使用以下命令以递归方式使整个层次结构归 mysql 用户和组所拥有。

  `chown -R mysql:mysql /var/lib/mysql-data`

  **注：**用户 mysql 需要具有对数据库文件夹的完全许可权 (rwx) 以及对日志、二进制、数据、索引和表单文件的读/写许可权。<br/>
通常，在共享托管环境中，数据库文件夹具有许可权 700 (drwx------)，并且由 mysql:mysql 所拥有。在专用环境中，该许可权可以更自由地配置为 755 (drwxr-xr-x)。

7. 更新“/etc/my.cnf”配置文件，使其指向新的数据目录。
  **重要信息：**在对配置文件进行任何编辑之前，请先备份该文件的所有内容。

  `cp -vp /etc/my.cnf /etc/my.cnf.'date +%s'`<br/>
  `vi /etc/my.cnf`

8. 将“/var/lib/mysql”的所有实例替换为“var/lib/mysql-data”。如果没有 datadir 条目，请将其放入 [mysqld] 节中。

  `[mysqld]`<br/>
  `user = mysql`<br/>
  `datadir = /var/lib/mysql-data`<br/>
  `socket =  /var/lib/mysql-datal/mysql.sock`<br/>

9. 某些应用程序具有定制配置，但本文档中未涵盖这些配置。如果数据目录不是 /var/lib/mysql，某些脚本已知会失败。所以，使用了符号链接来指向新位置。<!--(first, moving the old data directory out of the way)-->

  `mv -v /var/lib/mysql /var/lib/mysql.orig`<br/>
  `ln -s /var/lib/mysql-data /var/lib/mysql`<br/>

  如果不想创建链接，请确保更改“php.ini”中的“mysql.default”_套接字和“mysqli.default”_套接字，然后完全停止并启动 Apache。

10. 启动 MySQL 守护程序。

  `/etc/init.d/mysql start`

11. 验证 mysql 是否在运行。如果 mysql 未响应，请查看错误日志。如果需要，可还原更改。

  `mysqladmin ping`
