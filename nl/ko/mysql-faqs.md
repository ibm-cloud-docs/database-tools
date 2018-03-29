---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# FAQs: MySQL

## 내 MySQL 서버를 모니터하는 방법

Linux 애플리케이션 _mytop_은 특히 {{site.data.keyword.mysql}} 서버가 수행하는 작업을 검토하는 단기 모니터(UNIX 유틸리티 'top'과 유사)입니다. _mytop_은 몇 초마다 업데이트되므로 SQL 성능을 합리적으로 검토할 수 있습니다. 또한 _mytop_은 많은 양의 정보를 표시할 수 있습니다. 그리고 비밀번호 없이 루트 사용자를 사용하여 로컬 호스트의 {{site.data.keyword.mysql}} 서버에 연결되어 있는 것으로 가정합니다. 신임 정보는 스크립트에서 또는 명령행에서 변경될 수 있습니다.

## MySQL의 내 루트 비밀번호에 대한 개념

* 서버가 {{site.data.keyword.mysql}}에 자동 프로비저닝된 경우 루트 비밀번호는 서버 루트 비밀번호와 같습니다.
* Plesk가 서버에 자동 프로비저닝된 경우 Plesk에 "admin" 및 관리 비밀번호를 사용하십시오.
* 소스, RPM 또는 up2date를 통해 {{site.data.keyword.mysql}}을 설치한 경우 초기 루트 계정 비밀번호가 비어 있습니다. {{site.data.keyword.mysql}} 설치 중에 또는 설치 후에 루트 비밀번호를 설정하지 않는 한, 아무나 비밀번호 없이 루트로 {{site.data.keyword.mysql}} 서버에 연결할 수 있고 모든 권한을 부여받을 수 있습니다.

## MySQL에 대한 정보를 위한 최고의 온라인 리소스

[{{site.data.keyword.mysql}} 웹 사이트![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://dev.mysql.com/doc/){: new_window}에는 사용 가능한 검색 기능과 함께 전체 참조 매뉴얼이 있습니다.

문서에서는 기본 설치, SQL 구문부터 복제 및 클러스터링과 같은 고급 사용법까지 모든 내용을 다룹니다. 또한 독일어, 프랑스어, 일본어, 포르투갈어 및 러시아어로 작성된 참조 매뉴얼의 번역본이 있습니다.
