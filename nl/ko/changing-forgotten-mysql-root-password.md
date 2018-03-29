---
copyright:
  years: 2014, 2018
lastupdated: "2017-11-10"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 잊어버린 MySQL 루트 비밀번호 변경

{{site.data.keyword.mysql}} 루트 비밀번호를 변경하려면 다음 단계를 사용하십시오. 

1. 다음 명령을 실행하십시오.

        # /etc/init.d/mysqld stop
        # mysqld_safe --skip-grant-tables --skip-networking

2. 다음 명령을 사용하여 {{site.data.keyword.mysql}}에 연결하십시오.

        # mysql -u root

3. {{site.data.keyword.mysql}} 클라이언트에서 다음 명령을 실행하십시오.

        # UPDATE mysql.user SET Password=PASSWORD('newpassword') WHERE User='root';

4. 'newpassword'를 새 루트 비밀번호로 대체하십시오.

5. 다음 명령을 사용하여 {{site.data.keyword.mysql}} 서버를 다시 시작하십시오.

        # /etc/init.d/mysqld start
