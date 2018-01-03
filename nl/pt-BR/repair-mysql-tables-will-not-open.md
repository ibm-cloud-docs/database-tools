---
copyright: years: 1994, 2017 lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Reparando tabelas do MySQL que não abrem

O reparo de tabela do {{site.data.keyword.mysql}} é manipulado em uma base caso a caso, mas se estiver usando o tipo de tabela padrão do {{site.data.keyword.mysql}} de MyISAM (que é o mecanismo de armazenamento padrão, a menos que mudado ou especificado de forma diferente), você terá algumas opções.

1. É possível executar o utilitário myisamchk em uma linha de comandos para verificar, reparar ou otimizar tabelas. Ele é normalmente executado enquanto o banco de dados não está em execução. Para obter mais informações, veja [myisamchk ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://dev.mysql.com/doc/refman/5.0/en/myisamchk.html){: new_window}.
2. O mysqlcheck é semelhante em função ao myisamchk, mas ele pode ser executado enquanto o banco de dados está em execução. Para obter mais informações, veja [mysqlcheck ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://dev.mysql.com/doc/refman/5.0/en/mysqlcheck.html){: new_window}.
3. Se você efetuar login no banco de dados, também será possível executar comandos SQL que podem corrigir seu problema.

    Exemplos de comandos:
    *mysql> optimize table your-tablename
    *mysql> analyze table your-tablename
    *mysql> repair table your-tablename
    Para obter mais informações, veja [SQL de manutenção de tabela ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://dev.mysql.com/doc/refman/5.0/en/table-maintenance-sql.html){: new_window}.
4. Se você estiver obtendo números de erros do {{site.data.keyword.mysql}} e não tiver certeza do que se tratam, será possível executar o utilitário perror para consultar erros por meio da linha de comandos. Para obter mais informações, veja [perror ![Ícone de link externon](../../icons/launch-glyph.svg "Ícone de link externo")](http://dev.mysql.com/doc/refman/5.0/en/perror.html){: new_window}.

    Exemplos:
    *shell> perror 13 64
    *Código de erro 13: permissão negada
    *Código de erro 64: a máquina não está na rede
