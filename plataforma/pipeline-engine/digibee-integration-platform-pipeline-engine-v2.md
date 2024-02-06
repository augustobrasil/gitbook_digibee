---
description: Entenda a importância e os impactos da atualização do Pipeline Engine.
---

# Digibee Integration Platform Pipeline Engine v2

O [Pipeline Engine](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine) da Digibee Integration Platform é responsável por interpretar e executar os _pipelines_ criados por meio da interface. O principal objetivo da versão atualizada (Engine v2) é evoluir código e tecnologia, corrigir vulnerabilidades e melhorar o desempenho da Plataforma.

## **Benefícios da atualização**

A atualização do Pipeline Engine tem muitas vantagens para clientes e Digibees, como:

* Mais estabilidade para a Plataforma
* Evolução da arquitetura da Plataforma
* Códigos mais limpos e poderosos
* Novos recursos podem ser desenvolvidos com mais facilidade
* Inicialização mais rápida
* Ganho de desempenho

O Pipeline Engine v2 também apresenta melhorias significativas na inicialização do contêiner e na execução do pipeline em comparação com a versão anterior:

**Inicialização do contêiner**

|             | **Engine atual** | **Engine v2** | **Melhoria %** |
| ----------- | ---------------- | ------------- | -------------- |
| **Tempo**   | 3980ms           | 2674 ms       | 32,83%         |
| **CPU**     | 0.0409326        | 0.0301709     | 26,29%         |
| **Memória** | 257.51MB         | 246.445MB     | 4,3%           |

**Execução do **_**Pipeline**_

|             | **Engine atual** | **Engine v2** | **Melhoria %** |
| ----------- | ---------------- | ------------- | -------------- |
| **Tempo**   | 253 ms           | 171 ms        | 32,37%         |
| **CPU**     | 0.0063913        | 0.0034888     | 45,41%         |
| **Memória** | 3.044MB          | 0.905MB       | 70,27%         |

_\*Os valores obtidos são resultado da média de 10 repetições. Esses dados podem variar de acordo com os pipelines dos clientes._

### Aprimoramento de precisão numérica no Engine v2 (Beta restrito)

Além dos benefícios citados acima, a versão Beta do Pipeline Engine V2 também apresenta melhorias no tratamento e utilização de números de pontos flutuantes.

O recurso de aprimoramento de precisão numérica atenua problemas de arredondamento para números fracionários e garante que quaisquer números decimais de ponto flutuante transmitidos no _pipeline_ de um componente possam ser representados com mais precisão, tornando os resultados de _query_ mais precisos.

Atualmente, números com grande número de casas decimais como por exemplo 1250259129,48955334546546 acabam sendo arredondados através da notação científica e perdem precisão. Com esta melhoria, todos os números agora serão exibidos com as casas decimais originais.

Este aprimoramento está presente na implementação do Engine v2 tanto para novos _realms_ quanto para _realms_ existentes, sendo estes últimos ativados por meio do mecanismo de Feature Flag. Os clientes que já possuem o Engine v2 e desejam ativar este recurso devem entrar em contato com a equipe de suporte da Digibee.&#x20;

{% hint style="info" %}
Funções matemáticas de Double Braces, como DIVIDE, SUM, ABS e outras, não estão incluídas nesta _feature_. No entanto, eles estão em desenvolvimento e devem ser abordados em breve.
{% endhint %}

### Suporte a credenciais dinâmicas (Beta Restrito)

[Suporte a credenciais dinâmicas](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/suporte-a-credenciais-dinamicas-beta-restrito) é uma nova funcionalidade exclusiva do Pipeline Engine v2. Essa melhoria permite que os clientes que usam _pipelines_ multiuso na Digibee Integration Platform alterem suas configurações de credenciais na tela Run time, por meio do novo [componente Store Account](https://docs.digibee.com/documentation/v/pt-br/components/tools/store-account). O componente **Store Account**, disponível apenas no Pipeline Engine v2, armazena dinamicamente os dados das contas localmente.

Essa melhoria permite maior flexibilidade, pois as credenciais podem ser facilmente modificadas conforme necessário e perfeitamente integradas ao _pipeline_ de desenvolvimento sem a necessidade de um novo registro na seção Accounts da plataforma.

Dessa forma, os desenvolvedores podem gerenciar e atualizar com eficiência as credenciais sem complexidades desnecessárias, garantindo um processo de desenvolvimento tranquilo e simplificado. A atualização de credenciais dinâmicas está disponível nos seguintes componentes da Digibee Integration Platform:

* [SAP](https://docs.digibee.com/documentation/v/pt-br/components/untitled/sap)
* [SFTP](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/sftp)
* [FTP](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/ftp)
* [REST v2](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/rest-v2)
* [SOAP v3](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/soap-v3-beta)
* [DB v2](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/db-v2)
* [Kafka](https://docs.digibee.com/documentation/v/pt-br/components/queues-and-messaging/kafka)

Os novos parâmetros de configuração estão disponíveis nas documentações de cada um dos seus respectivos componentes.

{% hint style="warning" %}
O uso do componente Store Account em cenários paralelos, como execução paralela ou For Each (onde você substitui a conta configurada dinamicamente), **não é recomendado** na Fase de Beta Restrito.
{% endhint %}

### Redução no tempo da primeira execução do _pipeline_ - Pipeline Time to First Byte (Beta restrito)

Essa melhoria reduz o tempo da primeira execução do _pipeline_ em cerca de 50%. Por exemplo, se a solicitação demorava 6,5 segundos, agora leva apenas 2,3 segundos (estimativa).\
\
Essa otimização foi possível graças a uma atualização do [Double Braces ](https://docs.digibee.com/documentation/v/pt-br/build/double-braces/funcoes-double-braces)– uma linguagem de expressão da Digibee que utiliza Java reflection – para carregar as classes da aplicação durante a inicialização do _pipeline_, quando ocorre a implantação.

## Fases de Implementação

### Fase Alpha

A primeira fase da implementação do mecanismo começa no ambiente de Staging da Digibee Integration Platform. Este ambiente foi escolhido porque não recebe acesso de clientes e os problemas relacionados a atualizações ocorrem em um ambiente controlado.

**Nesta fase, o time de Core Platform realiza testes e coleta métricas**, tentando escalar a implementação e usando _pipelines_ complexos para testar os piores cenários possíveis. Esta fase foi executada com sucesso.

Na segunda parte da Fase Alpha, a implementação foi executada em Ambientes de Training e Enablement. O objetivo é monitorar os logs do contêiner para validar exceção e execução de _pipelines_, corrigir bugs e detectar vulnerabilidades e exposições comuns (CVEs).\
\
O time de Core Platform, em colaboração com o time de Education, realizou testes do Engine v2 na Digibee Integration Platform durante os treinamentos dos dias 9 e 23 de janeiro. Durante o treinamento, os conectores se comportaram conforme o esperado e a Engine v2 permanece ativa nesses ambientes.

### Fase de Beta Restrito

Essa fase se inicia com a análise e seleção dos clientes pelos Customer Success Managers (CSM) com as orientações do time de Core Platform. A Fase Beta Restrito é dividida em duas partes:

* **PARTE 1 - Implementação do Engine v2 em novos **_**realms**_** de clientes novos e estabelecidos:** Na Parte 1, novos _realms_ estão sendo criados já com o Engine v2, com a situação monitorada de perto por analistas funcionais e outras equipes da Digibee. A implementação foi executada no novo domínio de um cliente no _cluster_ US e funcionou corretamente em um POC realizado pela Digibee.&#x20;
* **PARTE 2 - Implementação do Engine v2 em **_**realms**_** existentes de clientes estabelecidos:** Esta parte acontece paralelamente à parte 1, apenas para clientes selecionados. A atualização é executada nos ambientes de teste e produção dos \_realms \_existentes. A atualização executa uma versão beta do Engine v2 com suporte dedicado da equipe de Produto.\
  \
  A fase Beta Restrito passa pelas seguintes etapas antes de se tornar Beta e, em seguida, General Availability (G.A.):

1. **Fase Beta** - Convite aos clientes para usar o Engine V2
2. **Fase GA** - Transição obrigatória para o Engine v2

{% hint style="danger" %}
Após a data final estabelecida para transição obrigatória, a Digibee não fornecerá mais suporte para _pipelines_ associados à versão anterior do Engine.
{% endhint %}

## **Requisitos do sistema**

Os clientes selecionados na **fase Beta Restrito** serão os primeiros a receber as implementações do Engine v2. Eles são selecionados com base nos tipos de conectores, complexidade dos _pipelines_, maturidade no uso da plataforma e relacionamento com a Digibee.

Essa combinação de critérios é crítica para o time de Produto fazer com que as implementações funcionem da maneira mais tranquila possível, ao mesmo tempo em que reúne métricas que ajudarão em futuras implementações.

## Processo de implementação&#x20;

* **Implementação do engine v2 em novos **_**realms**_**:** \
  O Engine v2 será implementado em novos _realms_ por analistas funcionais em colaboração com as equipes de pré-vendas e Customer Success. É feito em POCs com novos clientes ou em novos _realms_ de clientes estabelecidos, o que significa um acompanhamento próximo pela Digibee (especialmente para clientes que não têm uma abordagem autónoma). Nesses casos, nenhuma ação é exigida dos clientes. Engine V2 já está instalado em seus novos _realms._&#x20;
* **Implementação do motor v2 em **_**realms**_** existentes de clientes estabelecidos:**\
  Para a implementação do Pipeline Engine v2 em _realms_ existentes, os _pipelines_ de produção serão replicados no ambiente de teste. Quando o ambiente de teste é atualizado com sucesso, o Engine v2 é implantado no ambiente de produção. \

  *   **Processo de redeploy**

      O processo de atualização do Pipeline Engine v2 requer _redeployments_ obrigatórios para a implementação completa da nova versão. Como o Pipeline Engine v2 está em fase Beta, eventuais _redeployments_ após a instalação são necessários para a implementação completa das melhorias identificadas.\


      Inicialmente, o cliente deve coordenar o processo de _redeployment_ com seu respectivo CSM. Após o _redeploy_ inicial, o Engine v2 funcionará normalmente e o cliente será notificado com antecedência sobre as próximas datas de _redeployments_ de acordo com suas necessidades de planejamento, em alinhamento com o CSM.

### **Pipeline Engine API (Versão Beta)**

A API do Pipeline Engine foi projetada para permitir que duas versões do engine coexistam na Plataforma, com cada versão fornecendo funcionalidades distintas. Leia a documentação para saber [como alterar a versão do Pipeline Engine nos seus pipelines.](https://docs.digibee.com/documentation/v/pt-br/run/como-alterar-a-versao-do-pipeline-engine-beta-restrito)

{% hint style="info" %}
Tanto a API do Pipeline Engine quanto o Engine v2 estão em Beta, o que significa que podem apresentar instabilidade em alguns cenários.&#x20;
{% endhint %}

### **Recursos de Suporte**

Espera-se que a implementação do Engine v2 seja realizada com segurança, sem impacto negativo para os clientes e sendo acompanhada de perto pela equipe de Produto.

Caso algum problema relacionado à execução dos _pipelines_ apareça após a implementação, o cliente deverá entrar em contato com o Suporte ao Cliente da Digibee por meio do chat na Digibee Integration Platform ou via e-mail enviado para [support@digibee.com](mailto:support@digibee.com). Para otimizar o tempo de resolução, a Digibee recomenda compartilhar as seguintes informações:

* Nome do pipeline;
* Nome do projeto (se houver);
* Ambiente (Prod ou Teste);
* Pipeline key (para erros ou incidentes);
* Mensagem de erro com data e hora;
* Outras informações pertinentes para auxiliar na identificação e análise.
