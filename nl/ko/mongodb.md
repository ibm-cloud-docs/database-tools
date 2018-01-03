---
copyright:
  years: 1994, 2017
lastupdated: "2017-06-08"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MongoDB

MongoDB는 엔터프라이즈 클래스 데이터베이스 서비스 요구를 충족시키기 위해 수평으로 확장 가능한 완전히 기능을 갖춘 NoSQL 서버입니다. MongoDB는 무료로 주문하거나 OS 다시 로드를 통해 요청할 수 있습니다. 다음 운영 체제가 지원됩니다.

* CentOS 6.x
* RHEL 6.x
* Ubuntu 12.04
* Debian 6.x

SL-MongoDB 설치를 프로비저닝하는 경우 참고의 몇 가지 항목:

* 기본적으로 Mongod(MongoDB 서비스)는 사설 네트워크 인터페이스에만 바인드됩니다. MongoDB는 사전 구성된 관리자에 프로비저닝됩니다. 사용자 이름은 'admin'이며 비밀번호는 서버 루트 비밀번호와 같습니다.
* 복제본 세트 클러스터와 같은 MongoDB 솔루션을 주문하는 경우, 관리 비밀번호는 클러스터 구성 프로세스의 마지막에 솔루션의 모든 MongoDB 서버에서 설정됩니다.

MongoDB에 대한 자세한 정보는 다음 링크를 참조하십시오.

* [MongoDB 문서 라이브러리](http://www.mongodb.org/display/DOCS/Home)
* [MongoDB 포럼 및 오픈 소스 지원](https://groups.google.com/forum/?fromgroups#!forum/mongodb-user)
* [Karl Seguin's The Little Mongo DB Book(PDF)](http://openmymind.net/mongodb.pdf)

## 수행 방법

* [MongoDB 네트워킹 구성](configure-mongodb-networking.html)
* [MongoDB 솔루션을 위한 MMS(MongoDB Monitoring Service) 설정](set-mongodb-monitoring-service-mms-mongodb-solution.html)
