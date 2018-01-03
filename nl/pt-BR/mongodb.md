---
copyright:
  years: 1994, 2017
lastupdated: "2017-06-08"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# MongoDB

O MongoDB, um servidor NoSQL repleto de recursos, é escalável horizontalmente para atender suas necessidades de serviço de banco de dados corporativo. O MongoDB pode ser pedido sem custo ou solicitado com um recarregamento do S.O. Os sistemas operacionais a seguir são suportados:

* CentOS 6.x
* RHEL 6.x
* Ubuntu 12.04
* Debian 6.x

Alguns itens a serem destacados ao provisionar uma instalação do SL-MongoDB:

* Por padrão, o Mongod (o serviço MongoDB) é ligado somente à sua interface de rede privada. O MongoDB é provisionado com um usuário administrativo pré-configurado. O nome do usuário é 'admin' e a senha é a mesma que a senha raiz do servidor.
* Se você estiver pedindo uma solução MongoDB, como um cluster de conjunto de réplicas, sua senha de administrador será configurada em todos os servidores MongoDB na solução no término do processo de configuração de cluster.

Para obter mais informações sobre o MongoDB, veja os links a seguir:

* [Biblioteca de documentos do MongoDB](http://www.mongodb.org/display/DOCS/Home)
* [Fóruns e suporte ao software livre do MongoDB](https://groups.google.com/forum/?fromgroups#!forum/mongodb-user)
* [The Little Mongo DB Book (PDF) de Karl Seguin](http://openmymind.net/mongodb.pdf)

## Como...?

* [Configurar a rede do MongoDB](configure-mongodb-networking.html)
* [Configurar o MongoDB Monitoring Service (MMS) para uma solução MongoDB](set-mongodb-monitoring-service-mms-mongodb-solution.html)
