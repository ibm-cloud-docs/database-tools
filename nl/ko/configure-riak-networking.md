---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-15"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Riak 네트워킹 구성

## 개요

{{site.data.keyword.Bluemix}} 엔지니어링 서버에 Riak를 설치하면 Riak가 [사설 네트워크 IP 주소![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.softlayer.com/about/datacenters/rack-architecture){: new_window}에 바인드됩니다. Riak를 바인드하면 배치 시 액세스 가능한 열린 Riak 인스턴스가 공개적으로 노출되는 보안 위험이 최소화됩니다. Riak에 바인드된 IP 주소는 언제든 변경 가능합니다. **참고:** 인스턴스에 대한 외부 액세스를 제한하는 다른 보안 조치(예: 방화벽 및 iptable)가 준비되지 않은 경우 Riak를 공용 인터페이스에 공개적으로 노출하면 안됩니다.
{:shortdesc}

다음 단계를 완료하여 새 인터페이스에 바인드할 Riak 네트워킹을 구성하십시오.

## 새 인터페이스에 Riak 바인드

1. 설치에 있는 `/etc/riak/app.config` 파일의 `riak_core` 섹션으로 이동하십시오.
2. Riak가 바인드된 새 IP 주소를 반영하도록 `riak_core` 섹션에서 `http{}` 속성을 업데이트하십시오.<br/>`{http, [ {"127.0.0.1", 8098 } ] },`
3. 설치에서 `/etc/vm.args` 파일을 찾으십시오.
4. 새 IP 주소를 반영하도록 `/etc/vm.args` 파일 내 `-name` 속성을 편집하십시오.<br/>`-name riak@127.0.0.1`
5. Riak를 다시 시작하여 바인딩 변경을 완료하십시오.

## 다음 단계

바인드에 대한 변경사항은 Riak 인스턴스와 연관된 인터페이스에 대한 모든 이전 바인드에 영향을 줍니다. 다시 시작하면 바인드된 IP 주소가 업데이트되고 올바르게 작동됩니다. Riak 인스턴스를 다시 시작하지만 바인드에 성공하지 못한 경우 [지원](/general/support.html)에 문의하십시오.
