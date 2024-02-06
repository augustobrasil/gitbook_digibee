---
description: >-
  Saiba mais sobre o novo modelo SaaS Subscription da Digibee Integration
  Platform.
---

# Modelo baseado em Subscription

Este artigo apresenta conceitos importantes do novo modelo baseado em _subscription_, lançado em abril de 2022.

A Digibee oferece um modelo de SaaS baseado em _subscription_ e _committed use_, no qual o cliente tem acesso à Digibee Integration Platform e aos serviços de suporte e sucesso do cliente por um determinado período.&#x20;

Nesse modelo, as implantações serão realizadas baseadas na quantidade de _Pipeline Subscriptions_ e RTUs (_Runtime Units_) de testes ou produção. Além disso, são aplicados cotas de uso da Plataforma e limitações de entrega.

[Para saber mais sobre como implantar um _pipeline_, leia o artigo de implantação de um _pipeline._ ](https://docs.digibee.com/documentation/v/pt-br/run/deployments)

## Definições

### _Pipeline subscription_

_Pipeline subscription_ é o item de preço inicial que permite aos clientes acessar a Plataforma, suporte, serviços de sucesso do cliente e Propriedade Intelectual (IP) da Digibee. Um _pipeline subscription_ refere-se a um fluxo de integração exclusivo implantado na Digibee Integration Platform.&#x20;

Contém dois (2) RTUs de produção implantados no ambiente de produção, emparelhados com um (1) RTU de teste implantado no ambiente de teste e toda a infraestrutura subjacente necessária para executá-las. [Saiba mais sobre a definição no artigo de Capacidade e cotas de uso.](https://docs.digibee.com/documentation/v/pt-br/licenciamento/limites-de-uso)

### Fluxo de integração único&#x20;

Uma necessidade de negócios ou tecnologia para capturar, transformar e/ou entregar dados de uma fonte para outra. Único porque é um único _pipeline_ em uma versão específica.&#x20;

### _Pipeline version_&#x20;

É um número (ex.: 1.2) que representa o estado único de um _pipeline_. A Digibee segue o esquema simplificado de Versão Semântica ([www.semver.org](https://www.semver.org)) com apenas os componentes _**Major**_ e _**Minor**_. A Digibee não suporta "rótulos adicionais para metadados de pré-lançamento e compilação", e as versões _**Major**_ começam com 1.&#x20;

Para cada _pipeline subscription_, apenas uma versão principal do _pipeline_ pode estar ativa (implantada) em um determinado ambiente e momento.

* **Versão **_**Major**_** do **_**pipeline**_: especifica o componente de versão que controla as alterações de quebra em um _pipeline_, ou seja, alterações que tornariam duas versões _Major_ incompatíveis em termos de APIs expostas, comportamento ou saída.
* **Versão **_**Minor**_** do **_**pipeline**_: especifica o componente de versão que controla as alterações que **não** tornam duas versões _Minor_ diferentes com a mesma versão _Major_ incompatíveis, em termos de APIs expostas, comportamento ou saída.&#x20;

### RTU (_Runtime Unit_)

RTU (_Runtime Unit_) é uma medida da capacidade de computação para processar integrações na Digibee Integration Platform. Os RTUs podem ser usados para dimensionar integrações vertical e horizontalmente. Quando dimensionados verticalmente, eles podem ser usados em três tamanhos diferentes: _Small_ (consome 1 RTU), _Medium_ (consome 2 RTUs) e _Large_ (consome 4 RTUs).

Quando dimensionado horizontalmente, cada nova réplica consumirá a mesma quantidade de RTU que a implantação original. Cada RTU vem com a infraestrutura subjacente para executá-los. [Para mais informações, consulte o artigo de Capacidade e cotas de uso.](https://docs.digibee.com/documentation/v/pt-br/licenciamento/limites-de-uso)

* **RTU de teste** representa a capacidade de processamento para executar integrações em uma _subscription_ ativa em um ambiente de teste. Os RTUs devem ser pareados com um _pipeline_ _subscription_ existente.&#x20;
* **RTU de produção** representa a capacidade de processamento para executar integrações sob uma _subscription_ ativa em um ambiente de produção. Para implantar um novo _pipeline_ em um ambiente de produção, os _pipeline_ _subscriptions_ e os RTUs de produção devem estar disponíveis em seu _realm_.&#x20;

### Cotas de uso da plataforma&#x20;

As cotas de uso da plataforma são limites técnicos impostos em cada _realm_ para evitar a sobrecarga da Plataforma e foram criados com base no uso médio da Plataforma. Estes são alguns dos limites:&#x20;

* Tamanho de implantação e réplicas (ou seja, CPU e memória para executar um _pipeline_ ou um conjunto de réplicas);
* Tráfego de saída;
* Taxa de mensagens sendo produzidas/consumidas;
* Mensagens retidas no _pipeline_ para processamento;
* Retenção de _logs_;&#x20;
* VPNs;
* Armazenamento de objetos, armazenamento Digibee e dados de relacionamento.

## Principais regras&#x20;

### Regras para _pipeline subscription_ implantado

Você pode **construir** quantos _pipelines_ quiser na Digibee Integration Platform. Todas as cotas são aplicadas na fase de **implantação**. Cada _pipeline_ desenvolvido pode ser implantado em ambientes de teste ou produção, respeitando o número de _pipeline subscriptions_ e RTUs disponíveis.

Os _pipelines_ implantados em um ambiente consomem RTUs (teste ou produção) conforme o tamanho e as réplicas de implantação do _pipeline_.

Na tabela abaixo, você pode ver quantas RTUs são consumidas por cada tamanho de implantação de _pipeline_:

| **Tamanho** | **RTUs Consumidos** |
| ----------- | ------------------- |
| _Small_     | 1                   |
| _Medium_    | 2                   |
| _Large_     | 4                   |

**Réplicas** consumirão tantas RTUs quanto a multiplicação do número de réplicas e o número de RTUs para o tamanho da implantação do _pipeline_.

Sempre que um _pipeline_ é implantado em um determinado ambiente, diz-se que um _pipeline subscription_ foi consumido nesse ambiente. Independentemente do número de RTUs disponíveis, você só poderá implantar a quantidade de _pipelines_ correspondente à quantidade de _pipelines subscription_ disponíveis.

### Versões dos _pipelines_&#x20;

Duas versões _Major_ diferentes do mesmo _pipeline_ são consideradas dois _pipelines_ diferentes e exclusivos e, portanto, consomem dois _pipeline subscriptions_.

Para cada _pipeline subscription_, apenas uma versão de _pipeline_ pode estar ativa em um determinado ambiente e momento.&#x20;

### Validação de subscriptions e RTUs&#x20;

Antes de cada implantação do _pipeline_ em um determinado ambiente, um algoritmo é aplicado: primeiro, o algoritmo verifica se o número de _pipelines_ exclusivos implantados é menor que o número de _pipeline subscriptions_ disponíveis.&#x20;

Se essa verificação for aprovada, o algoritmo verificará se o número de RTUs disponíveis para esse ambiente específico pode acomodar o número de RTUs solicitadas para essa implantação de _pipeline_. Caso essa checagem passar, o _pipeline_ será implantado.&#x20;

Caso contrário, a implantação falhará devido à falta de _pipeline subscriptions_ disponíveis ou de RTUs disponíveis.

### Regras para RTUs implantadas

As RTUs de teste e produção se acumulam à medida que _pipeline subscriptions_ são adicionados. Quando um _pipeline_ é implantado em um determinado ambiente, o número de RTUs correspondentes é reduzido do número total de RTUs disponíveis nesse ambiente. Quando não houver mais RTUs disponíveis em um determinado ambiente, nenhum _pipeline_ adicional será implantado.

RTUs de teste e RTUs de produção são destinados a serem usados em seus respectivos ambientes e não podem ser trocados.

O uso de RTUs de teste ou produção sempre requer um _pipeline subscription_ existente. As RTUs sobressalentes não podem ser usadas para executar _pipelines_ que não tenham um _pipeline subscription_ associado a ela.
