---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MMS(MongoDB Monitoring Service) 설정

{{site.data.keyword.mongodb}} 솔루션을 완료한 후 복제본 세트의 호스트가 10gen의 무료 MMS({{site.data.keyword.mongodb}} Monitoring Service)에서 작동되도록 설정할 수 있습니다. 이 모니터링 서비스를 사용하여 복제된 데이터베이스의 자세한 기술 분석을 볼 수 있습니다. 시작하려면 MMS API 키 및 비밀 키가 필요하며, 이러한 키는 [10gen MMS 등록 웹 사이트![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.10gen.com/mongodb-monitoring-service){: new_window}에서 계정을 등록하여 얻을 수 있습니다.
{:shortdesc}

**참고:** {{site.data.keyword.mongodb}} 솔루션을 주문할 때 MMS 키 또는 새 MMS 계정 정보를 입력한 경우 이러한 MMS 신임 정보가 이미 설정되어 있을 수 있습니다.

계정의 MMS API 키와 비밀 키는 [10gen MMS 웹 사이트![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://mms.10gen.com/){: new_window}에 있습니다. 제공된 신임 정보를 사용하여 로그인하고 **설정**을 선택하여 MMS 그룹의 **API 키**와 **비밀 키**를 표시하십시오.

## 호스트 구성

MMS를 구성하려면 먼저 호스트에서 API 키와 비밀 키를 업데이트해야 합니다. **참고:** 이러한 단계는 세트의 단일 호스트에서만 수행되어야 합니다. 하지만 장애 복구 백업 MMS 에이전트를 사용하기 위해 다중 호스트에서 동일한 단계를 수행할 수 있습니다. 세트에 있는 하나의 에이전트만 MMS 서비스로 정보를 전달합니다.

1. 솔루션의 호스트 중 하나에 SSH로 연결하십시오(네트워크 주소와 신임 정보는 {{site.data.keyword.slportal_full}}에 있음).
2. 다음 명령을 실행하십시오. 해당 API와 비밀 키가 대체됩니다.

    `# /opt/local/bin/mongoConfigureAuthentication.sh -a -s`

    `Updating the /opt/local/10gen/mms-agent/settings.py file with the`
    `MMS API/secret keys...`

    `Restarting MMS agent...`

    `Shutting down MMS-agent:                                   [  OK  ]`

    `Starting MMS-agent:                                        [  OK  ]`


## MMS 그룹 구성

호스트를 구성하고 MMS 에이전트가 다시 시작되면 10gen MMS 웹 사이트에서 MMS 그룹을 다시 시작해야 합니다.

1. [10gen MMS 웹 사이트![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://mms.10gen.com/){: new_window}에 로그인하십시오.
2. **호스트 > 에이전트**를 선택하십시오.
3. 구성된 에이전트가 목록에 있는지 확인하십시오. 구성되고 다시 시작된 각각에 대해 하나의 에이전트가 나열됩니다.
4. 목록에 호스트를 추가하려면 **호스트**를 선택하고 **더하기(+)**를 클릭하십시오.
5. 호스트의 *사설 IP 주소*와 {{site.data.keyword.mongodb}}의 포트 번호를 입력하십시오. SoftLayer MongoDB 솔루션의 기본 포트 번호는 27018입니다.
6. 데이터베이스 관리 사용자 이름과 비밀번호({{site.data.keyword.slportal}}의 디바이스에 대한 **비밀번호**에 있음)를 입력하고 **추가**를 선택하십시오.
  * **중요:** 이러한 신임 정보는 필수입니다.

**참고:** 데이터가 MMS에 표시되기 전까지 최대 30분이 걸릴 수 있습니다.
