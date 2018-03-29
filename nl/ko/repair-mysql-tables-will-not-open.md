---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 열리지 않은 MySQL 테이블 복구

{{site.data.keyword.mysql}} 테이블 복구는 케이스별로 처리되지만 MyISAM(변경되거나 다르게 지정되지 않는 한 기본 스토리지 엔진임)의 기본 {{site.data.keyword.mysql}} 테이블 유형을 사용하는 경우 몇 가지 옵션이 있습니다.

1. 명령행에서 myisamchk 유틸리티를 실행하여 테이블을 검사하거나, 복구하거나 최적화할 수 있습니다. 데이터베이스가 실행 중이 아니면 정상적으로 실행됩니다. 자세한 정보는 [myisamchk![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://dev.mysql.com/doc/refman/5.0/en/myisamchk.html){: new_window}를 참조하십시오.
2. mysqlcheck는 기능면에서 myisamchk와 유사하지만 데이터베이스가 실행되는 동안 실행될 수 있습니다. 자세한 정보는 [mysqlcheck![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://dev.mysql.com/doc/refman/5.0/en/mysqlcheck.html){: new_window}를 참조하십시오.
3. 데이터베이스에 로그인하면 문제점을 수정할 수 있는 SQL 명령을 실행할 수도 있습니다.

    예제 명령:
    *mysql> optimize table your-tablename
    *mysql> analyze table your-tablename
    *mysql> repair table your-tablename
    자세한 정보는 [테이블 유지보수 SQL![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://dev.mysql.com/doc/refman/5.0/en/table-maintenance-sql.html){: new_window}을 참조하십시오.
4. 수신한 {{site.data.keyword.mysql}} 오류 번호의 의미를 모르는 경우 perror 유틸리티를 실행하여 명령행에서 오류를 검색할 수 있습니다. 자세한 정보는 [perror![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://dev.mysql.com/doc/refman/5.0/en/perror.html){: new_window}를 참조하십시오.

    Examples:
    *shell> perror 13 64
    *Error code 13: Permission denied
    *Error code 64: Machine is not on the network
