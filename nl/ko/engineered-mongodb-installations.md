---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 엔지니어링 MongoDB의 새로운 기능 <!--installations-->

엔지니어링 {{site.data.keyword.mongodb}} 설치의 성능을 개선하기 위해 다음과 같이 변경되었습니다. 이러한 변경을 통해 10gen을 사용하여 엔지니어링 서버에 대한 최고의 사용자 경험을 제공합니다. 10gen 및 {{site.data.keyword.cloud}}는 다양한 {{site.data.keyword.baremetal_short}}을 사용하여 플랫폼 기본의 역할을 합니다. <!--{{site.data.keyword.baremetal_short}} provide a consistent high performance set of available resources that cannot be matched in shared resource, multi-tenant platforms.-->  

* **선호되는 OS로서의 CentOS 6.X** – 10gen은 {{site.data.keyword.mongodb}}를 지원하는 최고의 성능 및 기능이 CentOS 운영 체제에서 발견되었음을 표시합니다. 이 권장사항에 따라 {{site.data.keyword.cloud_notm}}는 독점적으로 {{site.data.keyword.mongodb}}를 CentOS 6.X 플랫폼에 배치합니다.

* **16개의 블록으로 SSD 미리 읽기 기본값 설정** - SSD 드라이브는 월등한 찾기 시간을 가지므로 미리 읽기를 16개의 블록으로 설정할 수 있습니다. 스피닝 디스크에는 약간의 버퍼링이 필요하므로 스피닝 디스크를 32개의 블록으로 설정합니다.

* **Noatime** - noatime을 추가하면 시스템이 읽고 있는 파일에 대해 파일 시스템에 기록하지 않아도 되며, 이로 인해 파일 액세스가 빨라지고 디스크 마모가 줄어듭니다.

* **BIOS에서 NUMA 끄기** - Linux, NUMA 및 {{site.data.keyword.mongodb}}는 함께 작동되지 않습니다. NUMA 하드웨어에서 {{site.data.keyword.mongodb}}를 실행하는 경우 NUMA 하드웨어를 끄십시오(인터리브 메모리 정책을 사용하여 실행). 문제점은 이상한 방식으로 나타날 수 있습니다(예: 일정한 시간 동안 엄청나게 느려지거나 높은 시스템 CPU 시간 발생).

* **Ulimit** – ulimit가 열린 파일의 경우 64,000으로 설정되고, 사용자 프로세스의 경우 32,000으로 설정됩니다. 이러한 한계를 사용해 사용 가능한 파일 핸들 또는 사용자 프로세스 유실로 인한 실패를 방지할 수 있습니다.

* **EXT4** – Ext4는 Ext3을 통해 선택됩니다. Ext3은 파일 할당(또는 파일 제거) 시 느리며 대형 파일 내 액세스도 양호하지 않습니다.

* **개별 저널 볼륨** – 10gen의 제안에 따라 {{site.data.keyword.cloud_notm}}는 저널에 대해 마운트된 개별 SSD 볼륨을 사용합니다. 이는 고급 엔지니어링 서버에서 사용 가능하며 저널링이 데이터 마운트 시 읽기/쓰기 오퍼레이션에 개입하지 않도록 합니다.

* **사전 설치된 MMS** -  MMS는 모든 {{site.data.keyword.mongodb}} 인스턴스에 무료로 제공되는 10gen 모니터링 서비스입니다. 모든 {{site.data.keyword.cloud_notm}} 엔지니어링 서버는 MMS 에이전트로 사전 구성됩니다.
