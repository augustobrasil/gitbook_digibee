---
description: >-
  Saiba como verificar e rastrear o histórico de implantação de seus pipelines
  em Run.
---

# Como verificar o Histórico de implantação do pipeline

É sempre útil saber como estão os _pipelines_. Com esta parte do histórico de implantação do _pipeline_, a visão geral das implantações mais recentes, fica mais fácil rastrear as alterações mais recentes do _pipeline_ e ver quais foram implantadas em princípio.

## Campo de seleção

Na tela principal de execução, no canto superior esquerdo, você encontrará duas opções de seleção onde poderá selecionar _**Pipelines**_ ou **Histórico**. Para ver os projetos e _pipelines_ criados, basta clicar em _**Pipelines**_.&#x20;

Após clicar em _Pipelines_, a página contém as informações usuais em Run, como o seletor de ambiente e seus projetos.

<figure><img src="../../.gitbook/assets/01 - Página principal.jpg" alt=""><figcaption></figcaption></figure>

Ao clicar no campo **Histórico**, uma lista dos _pipelines_ implantados mais recentemente será exibida, do mais recente ao mais antigo implantado. Cada _pipeline_ na lista contém informações sobre o Nome do _pipeline_, o Nome do projeto, sua Versão major, o status mais recente do _pipeline_ e as pessoas que implantaram o _pipeline_.

Além disso, a aba do Histórico contém dois campos de pesquisa para ajudar a localizar o _pipeline_. São eles, o **Nome do **_**pipeline**_ e o **Nome do projeto**. Desta forma é mais fácil, simples e rápido encontrar o _pipeline_ implantado para analisá-lo e trabalhar nele.

<figure><img src="../../.gitbook/assets/02 - Página de histórico.jpg" alt=""><figcaption></figcaption></figure>

## Selecionando o _pipeline_

Depois de localizar e clicar no _pipeline_ com o qual deseja trabalhar, um painel lateral é aberto. Este painel lateral contém informações sobre o _pipeline_, como a Versão _major_, quando foi implantado e quem o implantou, abaixo disso, se tem uma visão geral de todas as implantações desse _pipeline_ até sua versão atual.

<figure><img src="../../.gitbook/assets/03 - folha lateral.jpg" alt=""><figcaption></figcaption></figure>

### Histórico de implantação

No **Histórico de implantação** você encontrará as informações sobre as últimas implantações feitas neste _pipeline_ específico, onde poderá encontrar os dados sobre Tamanho, Execuções Simultâneas e Réplicas usadas nesta versão do _pipeline_.

Além de mostrar a Versão _minor_, também mostra o projeto e o ambiente em que foi implantado. Outros dados incluem o status do _pipeline_, indicando quando foi implantado, se ocorreu um erro ou se foi excluído.

Também será informado quando houver um _rollback_ para uma versão anterior no _pipeline_. Dessa forma, você pode acompanhar cada movimento no _pipeline_ e saber qual versão está em uso no momento. [Para saber mais, leia este artigo sobre como fazer _rollback_ para uma versão anterior do _pipeline_.](https://docs.digibee.com/documentation/v/pt-br/run/deployment/how-to-rollback-to-a-previous-deployment-version-restricted-beta)

<figure><img src="../../.gitbook/assets/Rollback historico.jpg" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Nota: Vale ressaltar que todos os _pipelines_ implantados contêm todas essas informações em seus históricos.
{% endhint %}
