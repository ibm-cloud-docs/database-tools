---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Linux에서 MySQL 백업

## MySQL 디렉토리에서 복사

기본적으로 Linux 서버의 {{site.data.keyword.mysql}} 데이터베이스가 다음 디렉토리에 저장됩니다.

`/var/lib/mysql/`

먼저 mysqld 서비스를 종료하는 경우 다음 명령을 사용하여 /backup 디렉토리 예에 데이터베이스를 복사할 수 있습니다.

`cp –Rp /var/lib/mysql/*.* /backup`

cp 명령의 –R 스위치는 반복을 의미하며, 사용자는 각 데이터베이스가 개별 디렉토리에 있으므로 이를 사용하려 합니다. –p 스위치는 권한에 대한 스위치이며 복사된 원본에 대한 권한을 유지합니다.

일반적으로 이전 방법을 사용하기 전에 mysqld 서비스를 종료합니다. 데이터베이스가 사용 중에 복사되면 백업이 손상되며 의미 없이 렌더링됩니다. 이 때 데이터베이스를 사용하고 있지 않으면 이전 명령을 사용할 수 있습니다.

## mysqldump 명령

mysqldump 명령을 사용하면 mysqld 서비스를 종료하지 않고도 개별 데이터베이스와 한 서버의 모든 데이터베이스를 모두 백업합니다. 데이터베이스가 온라인 상태로 유지되는 동안 백업을 작성하는 기능 때문에 이 방법이 선호됩니다.

## 개별 데이터베이스

다음은 루트로 로그인했을 때 _'example'_ 데이터베이스를 /backup 디렉토리에 백업하는 데 사용하는 예제 명령입니다.

`mysqldump example > /backup/example_backup.sql`

소형 데이터베이스가 아니면 데이터베이스 백업을 압축하여 백업 전송 시간을 줄이십시오. 다음 명령은 예제 데이터베이스의 백업을 압축합니다.

`tar czvf /backup/example_backup.tar.gz /backup./example_backup.sql`

## 모든 데이터베이스

백업할 데이터베이스가 여러 개 있는 경우 다음 명령이 서버의 모든 {{site.data.keyword.mysql}} 데이터베이스를 /backup 디렉토리에 백업합니다.

`mysqldump -A > /backup/databases.sql(or --all-databases)`

–A 스위치(“-all-databases”가 동일한 기능 수행)가 서버의 모든 데이터베이스를 덤프합니다.
