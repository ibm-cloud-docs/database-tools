---
copyright: years: 1994, 2017 lastupdated: "2017-11-15"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Fazendo backup do MySQL no Linux

## Copiar do diretório mysql

Por padrão, os bancos de dados {{site.data.keyword.mysql}} em servidores Linux são armazenados no diretório a seguir:

`/var/lib/mysql/`

Se você encerrar o serviço mysqld primeiro, será possível copiar seus bancos de dados para um diretório /backup de exemplo usando o comando a seguir:

`cp –Rp /var/lib/mysql/*.* /backup`

O comutador -R para o comando cp significa recursivo, que você deseja usar porque cada banco de dados está em um diretório separado. O comutador -p é para permissões, que mantém as permissões do que é copiado.

Geralmente, você encerra o serviço mysqld antes de usar o método precedente. Se um banco de dados é copiado enquanto ele está sendo usado, o backup é corrompido e é considerado inútil. Se você tiver certeza de que nenhum dos bancos de dados está sendo usado no momento, será possível usar o comando precedente.

## O comando mysqldump

Você usa o comando mysqldump para fazer backup de bancos de dados individuais e de todos os bancos de dados em um servidor sem precisar encerrar o serviço mysqld. Devido a essa capacidade de fazer backups enquanto ainda mantém os bancos de dados on-line, esse método é preferencial.

## Bancos de dados individuais

A seguir está um exemplo de comando que você usa para fazer backup de um banco de dados denominado _'example'_ para o diretório /backup enquanto está com login efetuado como raiz:

`mysqldump example > /backup/example_backup.sql`

A menos que seja um banco de dados pequeno, recomenda-se compactar o backup de banco de dados para reduzir a quantia de tempo para transferir o backup. O comando a seguir compacta o backup do banco de dados de exemplo:

`tar czvf /backup/example_backup.tar.gz /backup./example_backup.sql`

## Todos os bancos de dados

Se você tem vários bancos de dados para backup, o comando a seguir faz backup de todos os bancos de dados {{site.data.keyword.mysql}} em seu servidor para o diretório /backup:

`mysqldump -A > /backup/databases.sql(or --all-databases)`

O comutador –A (“-all-databases” executa a mesma função) faz dump de todos os bancos de dados no servidor.
