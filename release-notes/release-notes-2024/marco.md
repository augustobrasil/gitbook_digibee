# Março

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fkvk4JXHMxkDHmihD1lN9%2Fheader_realeasenews_March.gif?alt=media&token=a1f7760b-e933-4877-a342-eb5828d11f60" %}
Image do header de novidades ou release notes de março
{% endembed %}

## Novidades 19/03/2024

## Componentes

* **DynamoDB (Beta Restrito):** estamos lançando um novo componente que permite que _pipelines_ realizem operações em tabelas de bancos de dados DynamoDB na AWS. Esta funcionalidade atualmente está na fase Beta restrito. Saiba mais na [documentação do componente DynamoDB](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/dynamodb).
* **Salesforce (**_**General Availability**_**):** o componente foi atualizado [de Beta para _General Availability_ e agora está disponível para todos os clientes](https://docs.digibee.com/documentation/v/pt-br/general/programa-beta). O componente Salesforce permite que a pessoa usuária faça operações na plataforma Salesforce. Saiba mais na [documentação do componente Salesforce](https://docs.digibee.com/documentation/v/pt-br/components/enterprise-applications/salesforce-restricted-beta).\
  ​\
  ​

## Novo formulário de configuração de Cápsulas (Beta)

Implementamos melhorias no formulário de configuração de Cápsulas visando simplificar a sua configuração, melhorar a usabilidade e proporcionar mais facilidade ao operar a Digibee Integration Platform.

Nesta atualização, as abas Parâmetros e Contas foram unificadas na aba Formulário, e a pessoa usuária pode selecionar facilmente se irá adicionar campos de parâmetros ou contas. Essa mudança simplifica a experiência e reduz a complexidade da configuração.

Aprenda mais na documentação sobre [como configurar uma Cápsula](https://docs.digibee.com/documentation/v/pt-br/build/capsulas/how-to-use-capsules/how-to-configure-a-capsule).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FK26rzuOPEMV9VgvT6Yqq%2FCapsule%20configuration%20form.mp4?alt=media&token=60426c76-d17b-4447-a6bf-32b37831b4b4" %}
Vídeo da feature de novo formulário de configuração de Cápsulas
{% endembed %}

##

## Assistente de IA para criação de fluxos (Beta Restrito)

A nova funcionalidade de Assistente de IA para criação de fluxos usa tecnologia de IA para sugerir novos componentes para pessoas usuárias adicionarem em seus fluxos nos _pipelines_. Essa ferramenta simplifica a criação de fluxos e proporciona às pessoas usuárias mais liberdade para escolher a melhor sugestão, aumentando eficiência e produtividade.

Essa funcionalidade está em beta restrito. Aprenda mais sobre ela na documentação [Assistente de IA para criação de fluxos](https://docs.digibee.com/documentation/v/pt-br/build/canvas/ai-assistant-for-flow-creation).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FBSwSRUncRICPcyNkK71h%2FAI%20Assistant%20for%20flow%20creation.mp4?alt=media&token=57eb8314-ac73-44b2-b8d4-e7a3649c1dfa" %}
Vídeo da feature de assistente IA para criação de fluxo
{% endembed %}





## Digibee Academy: atualização no curso Functional Analysis

Atualizamos as lições do curso **Functional Analysis - Mapping your Integrations** para incluir conteúdo sobre ZTNA. Três lições do curso foram atualizadas:

* Desvendando o quebra-cabeça das conexões do sistema
* Conectividade: ZTNA, VPN ou _endpoints_ expostos?
* Noções básicas sobre conectividade, autenticação, mapeamento e comunicação segura

Agora as pessoas usuárias podem se familiarizar com conceitos de ZTNA e entender como isso impacta o mapeamento de integrações.\
​\
​\
​\
​​

### Nós também solucionamos alguns _bugs:_ ​

* **Login — Redefinição de senha não possível:** corrigimos o _bug_ que impedia as pessoas usuárias que estavam logadas na Digibee Integration Plataform de redefinirem suas senhas.
* **Consumo de licenças — Número incorreto de consumers no relatório**: corrigimos o _bug_ que fazia com que o número de consumers não correspondesse às implantações.
* **Contas — Limite de caracteres para valores de contas:** corrigimos o _bug_ que limitava o número de caracteres para os valores das contas para 1.000. O novo limite agora é de 10.000 caracteres.
* **Cápsulas — Nomes grandes de Cápsulas excedem o tamanho da tela:** corrigimos o _bug_ que fazia com que as Cápsulas excedessem o tamanho da tela na página de lista de Cápsulas caso os nomes fossem muito grandes.
* **Cápsulas — Duas barras de rolagem na página de lista de Cápsulas:** corrigimos o _bug_ onde duas barras de rolagem eram exibidas na página de lista de Cápsulas.
* **Cápsulas — Paginação incorreta na página de lista de Cápsulas:** corrigimos o _bug_ que fazia com que a paginação da lista de Cápsulas não fosse exibida corretamente.
* **Canvas — Caminho da execução do Choice não é exibido corretamente no modo debug:** corrigimos o _bug_ que exibia todos os caminhos do Choice em verde no modo _debug_, embora apenas a condição onde a execução ocorreu devesse ser exibida em verde, e as outras condições deveriam ter uma linha tracejada.
* **Run — Botão de rollback:** removemos a ID dinâmica para criarmos uma data estática e fixa que não se altera baseada na ID do _pipeline_.
* **Componentes — Stream DB V3:** corrigimos o _bug_ que causava um erro quando o componente manipulava valores nulos em colunas CLOB.



***

##

## Novidades 06/03/2024

## Componentes

* **Salesforce (Beta):** o componente foi atualizado [de Beta Restrito para Beta](https://docs.digibee.com/documentation/v/pt-br/general/programa-beta). O componente Salesforce permite que a pessoa usuária faça operações na plataforma Salesforce. Saiba mais na[ documentação do componente Salesforce](https://docs.digibee.com/documentation/v/pt-br/components/enterprise-applications/salesforce-restricted-beta).



## Run — Funções avançadas do histórico de implantação (Beta)

Gostaríamos de anunciar o lançamento das funções avançadas do histórico de implantação. Essa nova feature possibilita o acesso à visualização ou restauração de qualquer versão anterior de um pipeline implantado.&#x20;

Saiba mais na [documentação sobre funções avançadas do histórico de implantação.](https://docs.digibee.com/documentation/v/pt-br/run/deployment/como-utilizar-as-funcoes-avancadas-do-historico-de-implantacao)

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FzPm4WXwVHIVlHJX1bOg1%2Fdeployment-history-advanced-functions%20(2).mp4?alt=media&token=4afa610a-3669-4128-9236-c2c4fa52a518" %}
Vídeo da feature de funções avançadas do histórico de implantação
{% endembed %}





## Administração — Novas permissões para gerenciamento de projetos (General Availability)

O papel Project Manager agora tem a permissão PROJECT:READ:ALL. Com essa nova permissão, as pessoas usuárias podem ver todos os projetos, independentemente de serem membros ou não.&#x20;

Essa atualização também adiciona permissões para o papel Pipeline Manager, para possibilitar a gestão de projetos. As permissões adicionadas são: PROJECT:CREATE, PROJECT:UPDATE e PROJECT:DELETE.

Saiba mais na [documentação de Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fc42UwjqSppXHU6hJbLSX%2FNew%20permissions%20for%20the%20management%20of%20projects.mp4?alt=media&token=25609064-dde8-4aaa-9ad9-fceb32fa7b28" %}
Vídeo da feature de novas permissões para gerenciamento de projetos&#x20;
{% endembed %}







### Nós também solucionamos alguns bugs:



* **Canvas — Linha conectora entre componentes não é deletada:** corrigimos o bug que impedia remover a linha conectora entre os componentes do canvas.
* **Componentes — Salesforce:** corrigimos o bug que causava erro ao utilizar as operações Query e Search.
* **Componentes — Digibee Storage:** corrigimos o bug que impedia o componente de escolher a melhor região de nuvem de acordo com o cliente.
* **Globals — Validação de Globals:** corrigimos o bug que fazia com que a validação das Globals do tipo URL e JDBC não funcionasse corretamente.
* **Globals — Limite de caracteres no valor de Globals:** corrigimos o bug que limitava os caracteres do valor da Global para 200. Agora, o novo limite é de 10.000 caracteres.
* **Contas — Erro na autenticação de contas: corrigimos** o bug que impedia a autenticação e re-autenticação de contas do tipo “oauth-2”.
* _**Run — Rollback:**_ corrigimos o bug onde o processo de rollback era afetado pelo carregamento quando executado múltiplas vezes, o que causava instabilidade. Agora, o rollback é concluído com sucesso.
* **Run — Diferenças entre cards de pipelines:** corrigimos o bug que causava diferença de altura entre cards de  pipelines em versão beta e os que estão em diferentes fases.&#x20;
* **Permissões de acesso:** corrigimos o bug que permitia que pessoas usuárias visualizassem o histórico de pipelines sem as permissões necessárias do time de projetos.&#x20;
* **Run — Remoção da implantação do ambiente errado ao promover um pipeline:** corrigimos o bug onde, ao promover o pipeline entre ambientes, a implantação era removida do ambiente errado. Agora, ao promover o pipeline para prod, a implantação em test é removida, e os detalhes em prod são exibidos.

\
