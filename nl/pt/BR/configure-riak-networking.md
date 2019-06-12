---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Configurando a rede do Riak

Quando você instala o Riak em um servidor projetado do {{site.data.keyword.Bluemix}}, o Riak é ligado ao [endereço IP de rede privada ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.softlayer.com/about/datacenters/rack-architecture){: new_window}. Ligar o Riak minimiza os riscos de segurança de ter uma instância do Riak acessível e aberta exposta publicamente na implementação. A qualquer momento, o endereço IP que está ligado ao Riak pode ser mudado. **Nota:** o Riak não deve ser exposto abertamente às interfaces públicas sem outras medidas de segurança no local para limitar o acesso externo à instância (por exemplo, firewalls e iptables). 
{:shortdesc}

Conclua as etapas a seguir para configurar a rede do Riak para ligar-se a uma nova interface.

## Ligando o Riak a uma nova interface

1. Acesse a seção `riak_core` do arquivo `/etc/riak/app.config` na instalação.
2. Atualize o atributo `http{}` na seção `riak_core` para refletir o novo endereço IP ao qual o Riak está ligado.<br/>`{http, [ {"127.0.0.1", 8098 } ] },`
3. Localize o arquivo `/etc/vm.args` na instalação.
4. Edite o atributo `-name` dentro do arquivo `/etc/vm.args` para refletir o novo endereço IP:<br/>`-name riak@127.0.0.1`
5. Reinicie o Riak para concluir as mudanças de ligação.

## Próximas Etapas

As mudanças feitas na ligação afetam todas as ligações anteriores para quaisquer interfaces associadas à instância do Riak. Após a reinicialização, o endereço IP ligado é atualizado e funciona de forma adequada. Se você reiniciar a instância do Riak e isso não resultar em uma ligação bem-sucedida, entre em contato com o [Suporte](/docs/get-support/getstarttssup.html).
