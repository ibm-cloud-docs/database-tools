---
copyright: years: 1994, 2017 lastupdated: "2017-11-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Configurando o MongoDB Monitoring Service (MMS)

## Visão geral

Depois de concluir sua solução {{site.data.keyword.mongodb}}, os hosts no conjunto de réplicas podem ser configurados para trabalhar com o {{site.data.keyword.mongodb}} Monitoring Service (MMS) grátis da 10gen. É possível usar esse serviço de monitoramento para ver uma análise técnica detalhada do banco de dados replicado. Você precisa da chave API do MMS e a chave Secreta para a introdução, que é obtida ao registrar uma conta no [website de registro do MMS da 10gen ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.10gen.com/mongodb-monitoring-service){: new_window}.
{:shortdesc}

**Nota:** essas credenciais do MMS podem já estar configuradas se você inseriu suas chaves do MMS ou seus dados da conta do MMS quando pediu a solução {{site.data.keyword.mongodb}}.

A chave API do MMS e a chave Secreta para uma conta podem ser localizadas no [website do MMS da 10gen ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://mms.10gen.com/){: new_window}. Efetue login usando as credenciais fornecidas e selecione **Configurações** para revelar a **Chave API** e a **Chave Secreta** do Grupo do MMS.

## Configurando hosts

Antes de configurar o MMS, você precisa atualizar a chave API e chave Secreta nos hosts. **Nota:** estas etapas precisam ser executadas somente em um único host no conjunto. No entanto, as mesmas etapas podem ser executadas em múltiplos hosts para ativar o failover de agentes MMS de backup. Somente um agente em um conjunto sempre comunica informações para o serviço MMS.

1. Use SSH para um dos hosts na solução (endereço de rede e credenciais podem ser localizados no {{site.data.keyword.slportal_full}}.
2. Execute o comando a seguir, substituindo as chaves API e Secretas apropriadas.

    `# /opt/local/bin/mongoConfigureAuthentication.sh -a -s`

    `Updating the /opt/local/10gen/mms-agent/settings.py file with the`
    `MMS API/secret keys...`

    `Restarting MMS agent...`

    `Shutting down MMS-agent:                                   [  OK  ]`

    `Starting MMS-agent:                                        [  OK  ]`


## Configurando o Grupo do MMS

Depois de configurar seus hosts e os agentes MMS serem reiniciados, você precisa reiniciar o Grupo do MMS no website MMS da 10gen.

1. Efetue login no [website MMS da 10gen ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://mms.10gen.com/){: new_window}.
2. Selecione **Hosts > Agentes**.
3. Verifique se os agentes configurados estão na lista. Um agente é listado para cada um que foi configurado e reiniciado.
4. Para incluir um host na lista, selecione **Hosts** e clique em **mais (+)**.
5. Insira o *endereço IP privado* do host e o número da porta para o {{site.data.keyword.mongodb}}. O número da porta padrão para as soluções do SoftLayer MongoDB é 27018.
6. Insira o nome de usuário administrador do banco de dados e a senha, que pode ser localizada em **Senhas** para um dispositivo no {{site.data.keyword.slportal}} e selecione **Incluir**.
  * **Importante:** essas credenciais são obrigatórias.

**Nota:** pode levar até 30 minutos antes de os dados serem mostrados no MMS.
