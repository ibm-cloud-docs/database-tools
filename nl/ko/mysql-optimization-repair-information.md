---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL 최적화/복구 정보

## MySQL의 메모리 사용 방법 
다음은 mysqld 서버가 메모리를 사용하는 방식 및 연관된 mysqld 변수 이름입니다.
* [메모리 사용 MySQL 5.0 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://dev.mysql.com/doc/refman/5.0/en/memory-use.html){: new_window}
* [메모리 사용 MySQL 4.1 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://dev.mysql.com/doc/refman/4.1/en/memory-use.html){: new_window}

## MySQL 최적화에서 설명하는 항목:
- 최적화 개요
- SELECT 및 기타 명령문 최적화
- 잠금 문제
- 데이터베이스 구조 최적화
- MySQL 서버 최적화
- 디스크 문제

[최적화 MySQL 5.0 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://dev.mysql.com/doc/refman/5.0/en/optimization.html){: new_window}
[최적화 MySQL 4.1 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://dev.mysql.com/doc/refman/4.1/en/optimization.html){: new_window}

## MySQL 서버 변수 - SQL 계층 또는 스토리지 엔진 특정
다음 링크에는 일반적인 변수가 나열됩니다.
[기사 1로 이동 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.mysqlperformanceblog.com/2006/06/08/mysql-server-variables-sql-layer-or-storage-engine-specific/){: new_window}
[기사 2로 이동 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://forge.mysql.com/wiki/ServerVariables){: new_window}

## mysqld 변수 최적화(Ian Gilfillan 작성)
mysqld 서버 변수 설정에 대한 몇 가지 가이드라인을 포함해 MySQL 최적화에 대한 이 기사를 참조하십시오.
(key_buffer_size, 조회 캐시 변수, table_cache, sort_buffer 등)
[기사로 이동 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.databasejournal.com/features/mysql/article.php/3367871){: new_window}

## MySQL에서 데이터베이스 손상 복구(Ian Gilfillan 작성)
{{site.data.keyword.mysql}} 사용 시 테이블 손상은 드문 일입니다. 하지만 발생 시 문제점을 수정하는 방법을 알고 있는 것이 좋습니다.
[기사로 이동 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.databasejournal.com/features/mysql/article.php/3300511){: new_window}

## MySQL 최적화: 조회 및 색인(Ian Gilfillan 작성)
<!--The database is too slow. Queries are queuing up, backlogs growing, users being refused connection. Management is ready to spend millions on "upgrading" to some other system, when the problem is really that MySQL is simply not being used properly. Badly defined or non-existent indexes are one of the primary reasons for poor performance, and fixing these can often lead to phenomenal improvements.-->
[기사로 이동 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.databasejournal.com/features/mysql/article.php/1382791){: new_window}

[기타 {{site.data.keyword.mysql}} 기사(Ian Gilfillan 작성) ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.databasejournal.com/article.php/1474351){: new_window}
