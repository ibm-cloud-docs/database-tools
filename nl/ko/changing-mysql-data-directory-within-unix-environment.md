---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# UNIX와 같은 환경에서 MySQL 데이터 디렉토리 변경

다음 단계에 따라 {{site.data.keyword.mysql}} 데이터 디렉토리를 변경하십시오.

1. [PuTTY![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html){: new_window} 또는 선호되는 클라이언트를 사용하여 서버에 로그인하십시오.

  **참고:** 데이터 디렉토리에 전용 파티션을 사용하는 경우 데이터를 복사한 후 원래 데이터 디렉토리 대신 새 파티션을 마운트하십시오. 새 파티션을 마운트하면 비표준 구성 변경사항이 저장되며 이로 인해 일부 애플리케이션이 작동되지 않을 수도 있습니다.

2. mysqld({{site.data.keyword.mysql}} 디먼/서버)를 종료하십시오. 디먼을 시작하고 중지하는 프로세스는 서로 다른 운영 체제와 배포판에서 차이가 있습니다.

  **참고:** 원시 파일에 직접 영향을 주는 프로세스 중에는 {{site.data.keyword.mysql}}을 중지해야 합니다.

  `/etc/init.d/mysql stop`
  또는
  `/etc/init.d/mysqld, /etc/init.d/mysql-server, /usr/loca/etc/init.d/mysql, /opt/lamp…`

3. 변경하기 전에 데이터베이스를 백업하십시오. 원시 데이터베이스 파일의 사본을 작성하는 경우 {{site.data.keyword.mysql}} 디먼이 실행되지 않는지 확인하십시오. <!--(or be good at flushing and locking)-->

  서버에서 cPanel을 사용하는 경우 디먼이 다시 시작하기 전에 cPanel(주로 TailWatch/chkservd)을 중지하십시오. 임시 파일 `/etc/chkserv.d/mysqlisevil`을 작성하여 'chkservd'가 서비스를 다시 시작하지 않도록 할 수 있습니다. rsync에 대해 모르는 경우 다른 도구를 사용하여 백업(예: cp, cpio 또는 tar)을 작성할 수 있습니다.

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql.'date +%s'`

4. 데이터 디렉토리를 작성하고 {{site.data.keyword.mysql}} 사용자('my.cnf' 글로벌 옵션 파일에 지정된 사용자에 관계없이) 소유권을 제공하십시오. 이 예에서는 위치 `/var/lib/mysql-data`가 사용되지만 원하는 위치를 사용할 수 있습니다. 이를 위해 특별히 디스크/논리 디바이스를 추가하는 경우, 계속하기 전에 항목을 `/etc/fstab`에 추가하고 디렉토리를 마운트해야 합니다.

  `chown mysql:mysql /var/lib/mysql-data`

5. 원래 디렉토리를 새 {{site.data.keyword.mysql}} 데이터 디렉토리에 최종 복사하십시오(첫 번째 디렉토리의 끝에 / 유지).

  `rsync -vaP /var/lib/mysql/ /var/lib/mysql-data`

6. 새 데이터 디렉토리에 올바른 소유권, 즉 기본 {{site.data.keyword.mysql}} 사용자/그룹 또는 'my.cnf' 글로벌 옵션 파일에 지정된 사용자가 있는지 확인하십시오. 모르는 경우, 다음 명령을 사용하여 재귀적으로 {{site.data.keyword.mysql}} 사용자 및 그룹에 대한 전체 계층 구조를 소유할 수 있습니다.

  `chown -R mysql:mysql /var/lib/mysql-data`

  **참고:** 사용자 {{site.data.keyword.mysql}}에 데이터베이스 폴더에 대한 전체 권한(rwx) 및 로그, 바이너리, 데이터, 색인 및 양식 파일에 대한 읽기/쓰기 권한이 있어야 합니다.<br/>
일반적으로 공유 호스팅 환경에 있을 때 데이터베이스 폴더에는 700(drwx------) 권한이 있고 이 폴더는 mysql:mysql의 소유권 하에 있습니다. 전용 환경에서 권한은 755(drwxr-xr-x)로 자유롭게 구성할 수 있습니다.

7. 새 데이터 디렉토리를 가리키도록 '/etc/my.cnf' 구성 파일을 업데이트하십시오. 
  **중요:** 구성 파일을 편집하기 전에 모두 백업하십시오.

  `cp -vp /etc/my.cnf /etc/my.cnf.'date +%s'`<br/>
  `vi /etc/my.cnf`

8. '/var/lib/mysql' 인스턴스를 '/var/lib/mysql-data'로 대체하십시오. datadir 항목이 없는 경우 [mysqld] 스탠자 내에 배치하십시오.

  `[mysqld]`<br/>
  `user = mysql`<br/>
  `datadir = /var/lib/mysql-data`<br/>
  `socket =  /var/lib/mysql-datal/mysql.sock`<br/>

9. 일부 애플리케이션에는 사용자 정의 구성이 있으며 이 문서에서는 이를 다루지 않습니다. 일부 스크립트는 데이터 디렉토리가 /var/lib/mysql이 아닌 경우 실패하는 것으로 알려져 있습니다. 따라서 기호 링크는 새 위치를 가리키는 데 사용됩니다. <!--(first, moving the old data directory out of the way)-->

  `mv -v /var/lib/mysql /var/lib/mysql.orig`<br/>
  `ln -s /var/lib/mysql-data /var/lib/mysql`<br/>

  링크를 작성하지 않으려면 'php.ini'에서 'mysql.default'_ 소켓 및 'mysqli.default'_ 소켓을 변경하고 Apache를 완전히 중지하고 시작하십시오.

10. {{site.data.keyword.mysql}} 디먼을 시작하십시오.

  `/etc/init.d/mysql start`

11. {{site.data.keyword.mysql}}이 작동 중인지 확인하십시오. {{site.data.keyword.mysql}}에서 응답하지 않으면 오류 로그를 검토하십시오. 필요한 경우 변경을 되돌리십시오.

  `mysqladmin ping`
