---
copyright: years: 1994, 2017 lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Melhores práticas de segurança do MySQL

## Visão geral

Muitos usuários do
{{site.data.keyword.BluSoftlayer_full}} confiam no
{{site.data.keyword.mysql}} como solução de banco de
dados. Como os bancos de dados hospedam várias informações
importantes e, algumas vezes, confidenciais, é recomendado
assegurar os bancos de dados {{site.data.keyword.mysql}}
para proteger as informações. As práticas de segurança para o {{site.data.keyword.mysql}} são dependentes de necessidades individuais e necessidades de negócios; no entanto, há melhores práticas que são recomendadas para a introdução. Alinhe-se com as dicas a seguir para antecipar a proteção do seu banco de dados
{{site.data.keyword.mysql}}.

* Configure a senha raiz do {{site.data.keyword.mysql}}.
* Exclua a conta de teste e o banco de dados que foi
criado durante a instalação inicial do {{site.data.keyword.mysql}}.
* Assegure-se de que cada senha de conta individual do
{{site.data.keyword.mysql}} seja configurada.
* Conceda privilégios conforme a necessidade. Evite conceder privilégios globais desnecessariamente.
* Não use
[curingas![Ícone de link
externo](../../icons/launch-glyph.svg "Íconede link externo")](http://en.wikipedia.org/wiki/Wildcard_character){: new_window} no valor de nome

do host associado às contas.
* Revise periodicamente os usuários e bancos de
dados do {{site.data.keyword.mysql}} de uma conta
para verificar se as permissões continuam precisas.
* Não use senhas na linha de comandos com o comando `shell>mysql -u root - password=somepassword mysql`

**Nota:** use o comando a seguir para conceder a qualquer outro usuário o acesso de linha de comandos para puxar a senha com o comando `shell>ps`. Use o comando `shell>mysql -u root -p mysql` para ser solicitado para entrada de senha. Isso protege sua senha.

## Recursos adicionais

Há vários recursos que fornecem mais detalhes sobre como proteger seu banco de dados {{site.data.keyword.mysql}}. Recomenda-se iniciar com as diretrizes de segurança do {{site.data.keyword.mysql}} que são baseadas na versão do {{site.data.keyword.mysql}} que está em seu dispositivo:

* [{{site.data.keyword.mysql}} Versão 5.7 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://dev.mysql.com/doc/refman/5.7/en/security.html){: new_window}

Existem vários outros recursos que não são gerenciados pelo
{{site.data.keyword.mysql}} que podem ajudar. Esses recursos podem ser localizados procurando por
"{{site.data.keyword.mysql}} Security" usando
qualquer mecanismo de procura. Como os recursos de terceiros não são mantidos pelos
fabricantes do {{site.data.keyword.mysql}}, execute
essas práticas com cuidado. Como no caso de qualquer recurso, use sites
confiáveis e
consulte a documentação oficial e sites de suporte sempre que
possível.
