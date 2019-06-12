---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Informações de otimização/reparo do MySQL

## Como o MySQL usa memória 
A seguir estão algumas das maneiras que o servidor mysqld usa memória e os nomes de variáveis do mysqld associados.
* [Uso de memória do MySQL 5.0 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://dev.mysql.com/doc/refman/5.0/en/memory-use.html){: new_window}
* [Uso de memória do MySQL 4.1 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://dev.mysql.com/doc/refman/4.1/en/memory-use.html){: new_window}

## A otimização do MySQL abrange os itens a seguir:
- Visão geral de otimização
- Otimizando SELECT e outras instruções
- Problemas de bloqueio
- Otimizando a estrutura do banco de dados
- Otimizando o servidor MySQL
- Problemas de disco

[Otimização do MySQL 5.0 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://dev.mysql.com/doc/refman/5.0/en/optimization.html){: new_window}
[Otimização do MySQL 4.1 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://dev.mysql.com/doc/refman/4.1/en/optimization.html){: new_window}

## Variáveis do servidor MySQL - camada SQL ou específicas do Mecanismo de armazenamento.
Os links a seguir listam algumas das variáveis mais comuns.
[Acessar o artigo 1 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.mysqlperformanceblog.com/2006/06/08/mysql-server-variables-sql-layer-or-storage-engine-specific/){: new_window}
[Acessar o artigo 2 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://forge.mysql.com/wiki/ServerVariables){: new_window}

## Otimizando as variáveis do mysqld por Ian Gilfillan
Veja este artigo sobre otimização do MySQL, incluindo algumas diretrizes sobre a configuração da variável do servidor mysqld.
(key_buffer_size, variáveis de cache de Consulta, table_cache, sort_buffer etc.)
[Acessar o artigo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.databasejournal.com/features/mysql/article.php/3367871){: new_window}

## Reparando o dano ao banco de dados no MySQL por Ian Gilfillan
O dano a tabelas é raro quando você usa o {{site.data.keyword.mysql}}. No entanto, isso ajuda a saber como corrigir o problema quando ele ocorre.
[Acessar o artigo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.databasejournal.com/features/mysql/article.php/3300511){: new_window}

## Otimizando o MySQL: consultas e índices por Ian Gilfillan
<!--The database is too slow. Queries are queuing up, backlogs growing, users being refused connection. Management is ready to spend millions on "upgrading" to some other system, when the problem is really that MySQL is simply not being used properly. Badly defined or non-existent indexes are one of the primary reasons for poor performance, and fixing these can often lead to phenomenal improvements.-->
[Acessar o artigo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.databasejournal.com/features/mysql/article.php/1382791){: new_window}

[Outros artigos do {{site.data.keyword.mysql}} de Ian Gilfillan ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.databasejournal.com/article.php/1474351){: new_window}
