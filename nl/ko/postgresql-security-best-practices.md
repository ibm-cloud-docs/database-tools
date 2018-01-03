---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# PostgreSQL 보안 우수 사례

## 개요

많은 {{site.data.keyword.BluSoftlayer_full}} 사용자가 데이터베이스 솔루션을 위해 {{site.data.keyword.mysql}}에 의존합니다. 데이터베이스에는 다양하고 중요하며 때때로 민감한 정보가 보관되므로 {{site.data.keyword.mysql}} 데이터베이스를 보안하여 정보를 보호하는 것이 좋습니다. {{site.data.keyword.mysql}}에 대한 보안 사례는 개인의 요구와 비즈니스 요구에 따라 다릅니다. 하지만 시작을 위해 권장되는 우수 사례가 있습니다. 다음 팁에 맞춰 {{site.data.keyword.mysql}} 데이터베이스 보안을 우선 시작해야 합니다.
{:shortdesc}

* 루트 {{site.data.keyword.mysql}} 비밀번호를 설정하십시오.
* {{site.data.keyword.mysql}} 초기 설치 중에 작성된 테스트 계정과 데이터베이스를 삭제하십시오.
* 각 개별 {{site.data.keyword.mysql}} 계정 비밀번호가 설정되었는지 확인하십시오.
* 필요에 따라 권한을 부여하십시오. 글로벌 권한을 불필요하게 부여하지 마십시오.
* 계정과 연관된 호스트 이름 값에 [와일드카드![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://en.wikipedia.org/wiki/Wildcard_character){: new_window}를 사용하지 마십시오.
* 주기적으로 계정의 {{site.data.keyword.mysql}} 사용자와 데이터베이스를 검토하여 권한이 정확하게 유지되는지 확인하십시오.

## 추가 리소스

도움이 될 수 있는 {{site.data.keyword.mysql}}에서 관리하지 않는 다양한 추가 리소스가 있습니다. 이러한 리소스는 검색 엔진으로 "{{site.data.keyword.mysql}} 보안"을 검색하여 찾을 수 있습니다. 써드파티 리소스는 {{site.data.keyword.mysql}}의 제작사에서 유지보수하지 않으므로 이러한 사례를 주의해서 수행하십시오. 모든 리소스에 대해 신뢰할 수 있는 사이트를 사용하고 가능하면 공식 문서와 지원 사이트를 참조하십시오.
