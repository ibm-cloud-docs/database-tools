---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MongoDB 네트워킹 구성

{{site.data.keyword.mongodb}}가 설치된 {{site.data.keyword.Bluemix}} 엔지니어링 서버는 {{site.data.keyword.mongodb}}가 사설 네트워크 IP 주소에 바인드되도록 구성되어 있습니다. 이는 10gen 권장사항에 따른 것이며, 배치 시 액세스 가능한 열린 {{site.data.keyword.mongodb}} 인스턴스가 공개적으로 노출되는 보안 위험을 최소화하기 위해 제공됩니다. 
{:shortdesc}

## 바인드된 인터페이스 변경

{{site.data.keyword.mongodb}}는 다음에 표시된 대로 설치의 `/etc/mongod.conf` 파일에서 `‘bind_ip’` 속성을 변경하여 인터페이스에 바인드하도록 구성될 수 있습니다.

        # mongo.conf
        bind_ip = 0.0.0.0  

이 속성이 바인딩을 모든 인터페이스에 위치하도록 변경하거나, 사용자가 이 필드에서 특정 인터페이스의 IP 주소를 설정할 수 있습니다(배치 세부사항에서 사용 가능). {{site.data.keyword.mongodb}} 인스턴스를 다시 시작해야 합니다.

**중요:** 다른 보안 조치(예: 인스턴스에 대한 액세스를 제한하는 방화벽 또는 iptable)가 준비되어 있지 않은 경우 {{site.data.keyword.mongodb}}를 공용 인터페이스에 공개적으로 노출하지 마십시오.
