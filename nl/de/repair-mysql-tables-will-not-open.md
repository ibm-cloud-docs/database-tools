---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL-Tabellen reparieren, die nicht geöffnet werden können

Die Reparatur von {{site.data.keyword.mysql}}-Tabellen wird auf einer Fall-zu-Fall-Basis gehandhabt. Wenn Sie jedoch den {{site.data.keyword.mysql}}-Standardtabellentyp 'MyISAM' (die Standardspeicherengine, wenn nicht anders angegeben) verwenden, stehen Ihnen einige Optionen zur Verfügung.

1. Sie können das Dienstprogramm 'myisamchk' über eine Befehlszeile ausführen, um Tabellen zu überprüfen, zu reparieren oder zu optimieren. Das Dienstprogramm wird normalerweise ausgeführt, wenn die Datenbank nicht aktiv ist. Weitere Informationen finden Sie in [myisamchk ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://dev.mysql.com/doc/refman/5.0/en/myisamchk.html){: new_window}.
2. 'mysqlcheck' ähnelt in seiner Funktionsweise dem Dienstprogramm 'myisamchk', es kann jedoch bei aktiver Datenbank ausgeführt werden. Weitere Informationen finden Sie in [mysqlcheck ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://dev.mysql.com/doc/refman/5.0/en/mysqlcheck.html){: new_window}.
3. Wenn Sie sich bei der Datenbank anmelden, können Sie auch SQL-Befehle ausführen, mit denen das Problem behoben werden kann.

    Beispielbefehle:
    *mysql> optimize table ihr_tabellenname
    *mysql> analyze table ihr_tabellenname
    *mysql> repair table ihr_tabellenname
    Weitere Informationen finden Sie in [Anweisungen für die Tabellenwartung ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://dev.mysql.com/doc/refman/5.0/en/table-maintenance-sql.html){: new_window}.
4. Wenn {{site.data.keyword.mysql}}-Fehlernummern zurückgegeben werden und Sie nicht sicher sind, was diese bedeuten, können Sie das Dienstprogramm 'perror' ausführen, um nach Fehlern über die Befehlszeile zu suchen. Weitere Informationen finden Sie in [perror ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://dev.mysql.com/doc/refman/5.0/en/perror.html){: new_window}.

    Beispiele:
    *shell> perror 13 64
    *Error code 13: Permission denied
    *Error code 64: Machine is not on the network
