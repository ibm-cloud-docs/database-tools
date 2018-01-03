---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL 루트 사용자 비밀번호 재설정

{{site.data.keyword.mysql}} 루트 사용자 비밀번호를 재설정해야 하는 경우 다음 단계를 완료하십시오.

1. mysqld 서버로 kill(kill -9가 아님)을 전송하여 mysqld 서버를 중지하십시오. pid는 .pid 파일에 저장되며 일반적으로 이 파일은 {{site.data.keyword.mysql}} 데이터베이스 디렉토리에 있습니다.
  * 예: `shell> kill cat /your-mysql-data-directory/hostname.pid`
  * Red Hat에서 데이터베이스를 중지할 수도 있습니다.
    * 예: `shell> service mysqld stop`
    * 데이터베이스를 중지하려면 UNIX 루트 사용자이거나 서버를 실행하는 사용자와 동일한 사용자여야 합니다.
2. --skip-grant-tables 옵션을 사용하여 mysqld를 다시 시작하십시오.
3. mysqld 서버에 연결하십시오.
  * **옵션 1:** mysql -h hostname mysql 및 GRANT 명령으로 비밀번호 변경.
    * GRANT 명령에 대한 자세한 정보는 [{{site.data.keyword.mysql}} 문서![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.mysql.com/doc/G/R/GRANT.html){: new_window}를 참조하십시오.
  * **옵션 2:** `shell> mysqladmin -h hostname -u user password 'new password'`
4. `shell> mysqladmin -h hostname flush-privileges`를 사용하거나 SQL 명령 `mysql> FLUSH PRIVILEGES;`를 사용하여 권한 테이블을 로드하십시오.


**참고:** --skip-grant-tables로 mysqld를 시작한 후 GRANT 명령을 사용하면 _FLUSH PRIVILEGES_를 실행할 때까지 `Unknown command` 오류가 나타납니다.*
