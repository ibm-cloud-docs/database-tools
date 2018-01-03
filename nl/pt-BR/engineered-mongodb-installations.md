---
copyright: years: 1994, 2017 lastupdated: "2017-10-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# O que há de novo com <!--installations--> projetadas do MongoDB 

As mudanças a seguir foram feitas para aprimorar o desempenho de instalações projetadas do {{site.data.keyword.mongodb}}. Essas mudanças usam a 10gen para oferecer a melhor experiência do usuário possível com servidores projetados. A 10gen e {{site.data.keyword.cloud}} usam vários {{site.data.keyword.baremetal_short}} para servidor como a base de plataforma. <!--{{site.data.keyword.baremetal_short}} provide a consistent high performance set of available resources that cannot be matched in shared resource, multi-tenant platforms.-->  

* **CentOS 6.X como o S.O. preferencial** - a 10gen indica que eles encontraram o melhor desempenho e a capacidade para suportar o {{site.data.keyword.mongodb}} é encontrada no sistema operacional CentOS. Sob essa recomendação, o {{site.data.keyword.cloud_notm}} implementa exclusivamente o {{site.data.keyword.mongodb}} em uma plataforma CentOS 6.X.

* **Padrões de leitura antecipada de SSD configurados para 16 blocos** - as unidades SSD têm excelentes tempos de procura, portanto a Leitura antecipada pode ser configurada para 16 blocos. Os discos de rotação podem requerer buffer pequeno, portanto os discos de rotação são configurados para 32 blocos.

* **Noatime** - a inclusão do noatime elimina a necessidade de o sistema gravar no sistema de arquivos para arquivos que estão sendo lidos, o que significa acesso mais rápido de arquivos e menos uso de disco.

* **NUMA desligado na BIOS** - o Linux, o NUMA e o {{site.data.keyword.mongodb}} tendem a não funcionar juntos. Se você executa o {{site.data.keyword.mongodb}} no hardware NUMA, recomenda-se desligá-lo (em execução com uma política de memória de intercalação). Os problemas podem se manifestar de formas estranhas, como desacelerações massivas por períodos de tempo ou tempo alto de CPU do sistema.

* **Ulimit** - o ulimit é configurado para 64000 para arquivos abertos e 32000 para processos do usuário. Esses limites ajudam a evitar falhas devido a uma perda de manipulações de arquivos ou processos do usuário disponíveis.

* **EXT4** - o ext4 é selecionado sobre ext3. O ext3 pode ser lento ao alocar arquivos (ou removê-los) e o acesso dentro de arquivos grandes também é fraco.

* **Volume de diário separado** - sob o aviso da 10gen, o {{site.data.keyword.cloud_notm}} usa um volume SSD separado que é montado para o diário. Isso está disponível nos servidores superiores e projetados e evita que o registro no diário interfira em operações de leitura/gravação na montagem de dados.

* **MMS pré-instalado** - o MMS é o serviço de monitoramento da 10gen fornecido gratuitamente para todas as instâncias do {{site.data.keyword.mongodb}}. Todos os servidores projetados do {{site.data.keyword.cloud_notm}} são pré-configurados com o agente MMS.
