---
copyright: years: 1994, 2017 lastupdated: "2017-11-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# FAQs: MySQL

## Como é possível monitorar meu servidor MySQL?

O _mytop_, um aplicativo Linux pequeno e
fácil de usar, é um monitor quase em tempo real (semelhante ao
utilitário 'top' do UNIX) que verifica especificamente o que o
servidor {{site.data.keyword.mysql}} está fazendo. O _mytop_ atualiza-se a cada instante
permitindo verificar com eficácia o desempenho do SQL. O _mytop_ também é capaz de exibir uma
grande quantia de informações. Ele também considera que você está se conectando ao
servidor {{site.data.keyword.mysql}} no host local com o
usuário raiz e sem senha. As credenciais podem ser mudadas no próprio
script ou na linha de comandos.

## Qual é minha senha raiz do MySQL?

* Se o servidor foi autoprovisionado com o
{{site.data.keyword.mysql}}, a senha raiz é a
mesma que a senha raiz do servidor.
* Se o Plesk foi autoprovisionado no servidor, use "admin" e
a senha admin para ele.
* Se você instalou o {{site.data.keyword.mysql}} por
meio de código-fonte, RPM ou up2date, as senhas da conta raiz
iniciais estão vazias. Qualquer pessoa pode se conectar ao servidor
{{site.data.keyword.mysql}} como raiz sem uma senha e
receber todos os privilégios, a não ser que você configure a
senha raiz durante ou após a instalação do {{site.data.keyword.mysql}}.

## Qual é o melhor recurso on-line para obter informações
sobre MySQL?

O website do [{{site.data.keyword.mysql}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://dev.mysql.com/doc/){: new_window} tem um manual de referência completo com recursos de procura disponíveis.

A documentação aborda tudo, desde instalação básica e
sintaxe SQL até uso avançado, como replicação e armazenamento em
cluster. Além disso, existem traduções do manual de
referência em alemão, francês, japonês, português e
russo.
