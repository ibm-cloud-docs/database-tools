---
copyright: years: 1994, 2017 lastupdated: "2017-11-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MongoDB - melhores práticas arquiteturais

Use as melhores práticas a seguir para usar o {{site.data.keyword.mongodb}} em implementações no {{site.data.keyword.cloud}}. Se você selecionou os servidores projetados, várias dessas recomendações já estão implementadas. 

## Estratégia de implementação

Ao planejar sua implementação do {{site.data.keyword.mongodb}}, você precisa considerar várias áreas chave. A mais importante é o tamanho do conjunto de dados atual e previsto. Essas duas áreas são o driver principal para sua escolha de necessidades individuais do recurso de nó físico e guias de seus planos de sharding. Você também precisa considerar a importância de seus dados e o grau de tolerância à possibilidade de perda ou atraso de dados (especialmente em cenários replicados). 
## Dimensionamento de memória

O {{site.data.keyword.mongodb}} (como muitos aplicativos orientados a dados) funciona melhor quando o conjunto de dados reside na memória. Nada executa melhor do que uma instância do {{site.data.keyword.mongodb}} que não requer E/S de disco. Sempre que possível, selecione uma plataforma que tenha mais RAM disponível do que o tamanho do conjunto de dados de trabalho. Se seu conjunto de dados excede a RAM disponível para um único nó, considere aproveitar a vantagem do sharding. O sharding aumenta a quantia de RAM disponível em um cluster para acomodar o conjunto de dados maior. Assim, você maximiza o desempenho geral de sua implementação. As falhas de página podem indicar que você está excedendo a RAM disponível em sua implementação. Você precisa considerar aumentar a sua RAM disponível.

## Tipo de disco

Se a velocidade não é uma preocupação ou se você tem um conjunto de dados maior do que a sua estratégia de memória disponível pode suportar, um tipo de disco adequado para sua implementação é importante. O IOPS é a chave para selecionar o tipo de disco. Quanto maior o IOPS, melhor o desempenho do {{site.data.keyword.mongodb}}. Os discos locais precisam ser usados, se possível, pois o armazenamento de rede pode causar latência alta e desempenho fraco para sua implementação. É aconselhável que você use RAID 10 para matrizes de disco.

## CPU

A velocidade do clock e o número de processadores disponíveis tornam-se uma consideração se você deseja usar um map-reduce. No entanto, quando você executa uma instância do {{site.data.keyword.mongodb}} com a maioria dos dados na memória, a velocidade do clock pode afetar o desempenho. Se o seu sistema é executado sob essas circunstâncias e você deseja maximizar suas operações por segundo, considere uma estratégia de implementação que inclua uma CPU com uma velocidade alta de clock/barramento.

## Replicação

A replicação fornece alta disponibilidade de seus dados se um nó falha em seu cluster. Recomenda-se replicar com pelo menos três nós em qualquer implementação do {{site.data.keyword.mongodb}}. A configuração mais comum para replicação com três nós é uma implementação 2x1 que tenha dois nós primários em um data center único com um servidor de backup em um data center secundário.


## Sharding

Se você prevê um conjunto de dados grande, é aconselhável fazer uma implementação do {{site.data.keyword.mongodb}} com shard. É possível usar sharding para particionar o conjunto de dados em múltiplos nós. O {{site.data.keyword.mongodb}} pode distribuir automaticamente os dados entre os nós no cluster. Ou, é possível definir uma chave de shard e criar sharding baseado em intervalo para essa chave. O sharding pode ajudar a gravar o desempenho, portanto é possível usar shard mesmo se seu conjunto de dados é pequeno, mas requer um número alto de atualizações ou inserções. Ao implementar um conjunto com shard, o {{site.data.keyword.mongodb}} requer somente três instâncias do servidor de configuração, que são tempos de execução especializados do Mongo, para rastrear a configuração de shard atual. A perda de um desses nós faz com que o cluster entre em um modo somente leitura somente para a configuração e requer que todos os nós sejam colocados novamente on-line antes que quaisquer mudanças na configuração possam ser feitas.

## Modo de segurança de gravação

Existem vários modos de segurança de gravação que governam como o {{site.data.keyword.mongodb}} manipula a persistência dos dados em disco. É importante considerar qual estratégia atende melhor às suas necessidades para integridade de dados e desempenho. Você tem os modos de segurança de gravação a seguir disponíveis:

* **Nenhum** - fornece uma estratégia de gravação adiada sem bloqueio que ajuda o alto desempenho. No entanto, há uma pequena chance de uma falha do nó e os dados podem ser perdidos. Também há a possibilidade de que os dados que são gravados para um nó em um cluster não estejam disponíveis imediatamente em todos os nós nesse cluster para consistência de leitura. O modo Nenhum não fornece nenhuma proteção de dados para falhas de rede. Esse modo é altamente não confiável e é usado somente quando o desempenho é uma prioridade e a integridade de dados não é uma preocupação.
* **Normal** - é o padrão para o {{site.data.keyword.mongodb}}. O modo Normal também é uma estratégia de gravação adiada sem bloqueio.  
* **Seguro** - bloqueia até que o {{site.data.keyword.mongodb}} reconheça que recebeu a solicitação de gravação, mas bloqueia até que a gravação seja executada. O modo Seguro fornece um nível melhor de integridade de dados e consistência de leitura dentro de um cluster.
* **Diário seguro** - fornece uma opção de recuperação para o {{site.data.keyword.mongodb}}. O modo Diário seguro garante que os dados sejam reconhecidos e que uma atualização de Diário seja executada antes de retornar.
* **Fsync** - fornece o nível mais alto de integridade de dados e bloqueia até que uma gravação física dos dados ocorra. O uso de Fsync vem com uma degradação no desempenho e você o usa somente se a integridade de dados é a preocupação primária para seu aplicativo.

## Testando a implementação

A 10gen tem várias ferramentas para ajudá-lo no teste de carregamento de sua implementação. Uma ferramenta de console, ‘benchrun’, pode executar operações de dentro de uma rotina de teste de JavaScript. O benchrun retorna informações de operação e números de latência para cada operação. Se informações mais detalhadas sobre a instância do {{site.data.keyword.mongodb}} forem necessárias, considere executar o comando `mongostat` ou o MMS para monitorar sua implementação durante o teste. Para obter mais informações sobre essas ferramentas, veja as referências a seguir:

[Visão geral do MongoStat](http://docs.mongodb.org/manual/reference/mongostat/)

[Serviço de monitoramento do {{site.data.keyword.mongodb}} da 10gen](http://www.10gen.com/products/mongodb-monitoring-service)

## Instalação

Você tem várias considerações ao instalar o {{site.data.keyword.mongodb}} que podem ajudar a criar uma solução estável e orientada ao desempenho. A 10gen recomenda usar o CentOS (64 bits), se possível. Evite implementar em sistemas operacionais de 32 bits e sistemas operacionais Windows. Esses sistemas fornecem uma plataforma de implementação fraca. Os sistemas operacionais de 32 bits têm limites de tamanho do arquivo que causam problemas e o Windows pode causar problemas de desempenho se a memória virtual é usada pelo S.O. para compensar a falta de RAM em sua implementação. Por padrão, o {{site.data.keyword.cloud_notm}} fornece sistemas operacionais CentOS de 64 bits para todas as implementações do servidor projetado.

Além disso, certifique-se de fazer as alterações a seguir para a instalação do S.O. de base para maximizar o desempenho:
* **Configurar padrões de leitura antecipada de SSD para 16 blocos** – as unidades SSD têm excelentes tempos de busca que permitem reduzir a Leitura antecipada para 16 blocos. Os discos de rotação podem requerer buffer pequeno, portanto esses discos são configurados para 32 blocos.
* **noatime** - o noatime elimina a necessidade de o sistema gravar no sistema de arquivos para arquivos que estão sendo lidos. Isso significa que você tem acesso de arquivos mais rápido e menos uso de disco.
* **Desligar o NUMA na BIOS** - o Linux, o NUMA e o {{site.data.keyword.mongodb}} geralmente não funcionam juntos. Se você está executando o {{site.data.keyword.mongodb}} no hardware NUMA, recomenda-se desligá-lo (em execução com uma política de memória de intercalação). Se não, problemas como desacelerações massivas ou tempo alto de CPU do sistema podem se manifestar.
* **Configurar ulimit** - o ulimit é configurado para 64000 para arquivos abertos e 32000 para processos do usuário. Esses ulimits evitam falhas devido a uma perda de manipulações de arquivos ou processos do usuário disponíveis. 
* **Usar ext4** - o ext3 é lento ao alocar arquivos (ou removê-los). Além disso, o acesso em arquivos grandes é fraco com o ext3.

**Nota:** por padrão, essas alterações são configuradas em todos os servidores {{site.data.keyword.cloud_notm}}.

Também é recomendado que os volumes de Diário e Dados sejam volumes físicos distintos. Se os diretórios de Diário e Dados residem em um único volume físico, as liberações para o Diário interrompem o acesso de dados e fornecem aumentos de latência alta em sua implementação do {{site.data.keyword.mongodb}}.

## Operations

Depois que uma implementação do {{site.data.keyword.mongodb}} é promovida para produção, há algumas recomendações para monitoramento e otimização de desempenho. 
* Certifique-se de que você tenha o agente MMS em execução em todas as instâncias do {{site.data.keyword.mongodb}}. Isso ajuda a monitorar o funcionamento e o desempenho da implementação. O agente MMS fornece dados de depuração úteis para a 10gen durante as interações de suporte. 
* O comando `mongostat` também fornece informações de tempo de execução sobre o desempenho de um nó do MongoDB.

Se alguma dessas ferramentas descobrir problemas de desempenho, o sharding ou a indexação poderá ajudar a corrigir esses problemas de desempenho. 

* Índices - crie índices para uma implementação do MongoDB se as ferramentas de monitoramento indicarem que as consultas baseadas em campo estão operando de modo deficiente. Para ajudar a melhorar o desempenho, use sempre índices quando consultar dados que sejam baseados em campos distintos.
* Sharding - use sharding quando o desempenho geral do nó for afetado devido a um conjunto grande de dados em operação. Certifique-se de usar shard antes de ficar no vermelho. O sistema divide chunks somente para sharding na inserção ou atualização. Se você esperar muito tempo para o shard, poderá ter uma distribuição desigual. 

## Conclusão

Essas melhores práticas não representam todos os cenários possíveis que podem ser encontrados. É sempre melhor usar a assinatura 10gen para acessar o suporte diretamente da 10gen ou usar a documentação no website do MongoDB para ajudar com problemas e interesses específicos que você possa ter.
