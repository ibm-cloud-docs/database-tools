---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Reconfigurando a senha de usuário raiz do MySQL

Conclua as etapas a seguir se você precisar reconfigurar a senha de usuário raiz do {{site.data.keyword.mysql}}:

1. Encerre o servidor mysqld enviando uma kill (não kill -9) para o servidor mysqld. O PID é armazenado em um arquivo .pid, que está normalmente no diretório do banco de dados {{site.data.keyword.mysql}}:
  * Exemplo: `shell> kill cat /your-mysql-data-directory/hostname.pid`
  * No Red Hat, também é possível parar o banco de dados:
    * Exemplo: `shell> service mysqld stop`
    * Deve-se ser o usuário raiz do Unix ou o mesmo usuário com o qual o servidor é executado para parar o banco de dados.
2. Reinicie o mysqld com a opção --skip-grant-tables.
3. Conecte-se ao servidor mysqld:
  * **Opção 1:** mysql -h hostname mysql e mude a senha com um comando GRANT.
    * Para obter mais informações sobre comandos GRANT, veja [Documentação do {{site.data.keyword.mysql}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.mysql.com/doc/G/R/GRANT.html){: new_window}
  * **Opção 2:** `shell> mysqladmin -h hostname -u user password 'new password'`
4. Carregue as tabelas de privilégios usando `shell> mysqladmin -h hostname flush-privileges` ou com o comando SQL `mysql> FLUSH PRIVILEGES;`.


**Nota:** depois de iniciar o mysqld com --skip-grant-tables, qualquer uso de comandos GRANT fornece um erro `Unknown command` até que você execute _FLUSH PRIVILEGES_.*
