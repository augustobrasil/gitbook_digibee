---
description: Saiba como promover um pipeline por diferentes ambientes.
---

# Como promover pipelines entre ambientes

A promoção de um _pipeline_ já implantado em um ambiente para implantação em outro ambiente escolhido ficou mais rápido e conveniente. Veja como você pode fazer isso.

{% hint style="info" %}
Para ter acesso à **Implantação**, você deve ter a **permissão** de _**Deployment:**_** Ler** e _**Deployment:**_** Criar nos ambientes desejados (test/ prod)**, para sua conta de usuário ou um grupo ao qual você pertence.
{% endhint %}

## Selecionando o _pipeline_

No ambiente de _test_ ou outro ambiente que não seja de produção, selecione um _pipeline_ implantado que deseja implantar em outro ambiente. Após identificar o _pipeline_, clique nos três pontinhos no canto superior direito do _card_ do _pipeline_.

Lá você encontrará o botão **Promover para**, clique nele e siga as instruções que aparecem.

<figure><img src="../../.gitbook/assets/01 - Promover para.jpg" alt=""><figcaption></figcaption></figure>

## Promover para

Ao clicar em **Promover para**, uma aba lateral é exibida com as configurações de implantação do _pipeline_, que você pode alterar se necessário. Você também pode selecionar se deseja excluir esse _pipeline_ do ambiente de teste após promovê-lo.

Uma vez especificadas as configurações, clique no botão **PROMOVER** para manter a ação.

<figure><img src="../../.gitbook/assets/ezgif.com-gif-maker (2).gif" alt=""><figcaption></figcaption></figure>

Você também pode verificar as configurações definidas na etapa anterior comparando o _pipeline_ no ambiente de _test_ com as informações do _pipeline_ que será implantado no outro ambiente.&#x20;

Além disso, também é exibido o número de licenças que serão consumidas nesta ação.

<figure><img src="../../.gitbook/assets/03 - Consumo.jpg" alt=""><figcaption></figcaption></figure>

Se você selecionar **PROMOVER**, o _pipeline_ selecionado do _test_ ou outro ambiente de não produção será implantado no ambiente e projeto desejados. No entanto, se clicar em **CANCELAR**, você retornará à página anterior da configuração de implementação sem executar nenhuma ação.

Depois de promover o _pipeline_, você é redirecionado para a página de Run do ambiente e projeto selecionados.

## Verificando o status atual do _pipeline_

Você pode verificar o status de implantação atual do _pipeline_ em seu _card_, que indica se o _pipeline_ já foi implantado. [Para saber mais sobre os Status disponíveis no _card_, leia mais neste artigo.](https://docs.digibee.com/documentation/v/pt-br/run/status-de-implantacao-do-pipeline)

Além disso, você pode verificar o status dos _pipelines_ implantados mais recentemente na página de Histórico. [Para saber mais sobre como verificar o histórico de _pipelines_ implantados, veja mais neste artigo.](https://docs.digibee.com/documentation/v/pt-br/run/historico-de-implantacao-de-pipeline)

\
\


\
