---
copyright: years: 1994, 2017 lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Configurando a rede do MongoDB

## Visão geral

Os servidores projetados do {{site.data.keyword.Bluemix}} com o {{site.data.keyword.mongodb}} instalado são configurados para ter o {{site.data.keyword.mongodb}} ligado ao endereço IP de rede privada. Isso é por recomendação da 10gen e serve para minimizar os riscos de segurança de ter uma instância do {{site.data.keyword.mongodb}} aberta e acessível exposta publicamente na implementação.
{:shortdesc}

## Mudando a interface ligada

O {{site.data.keyword.mongodb}} pode ser configurado para ser ligado a qualquer interface mudando o atributo `'bind_ip'` no arquivo `/etc/mongod.conf` em sua instalação conforme mostrado:

        # mongo.conf
        bind_ip = 0.0.0.0  

Este atributo muda a ligação para estar em todas as interfaces ou é possível configurar o endereço IP da interface específica neste campo (disponível em seus detalhes da implementação). Uma reinicialização da instância do {{site.data.keyword.mongodb}} é necessária.

**Importante:** não exponha o {{site.data.keyword.mongodb}} abertamente às interfaces públicas sem algumas outras medidas de segurança no local, como firewalls ou iptables que limitam o acesso à instância.
