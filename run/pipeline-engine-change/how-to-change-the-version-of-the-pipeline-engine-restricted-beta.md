---
description: Saiba mais sobre como alterar a versão do Pipeline Engine em seus pipelines.
---

# Como alterar a versão do Pipeline Engine (Beta Restrito)

{% hint style="info" %}
Essa _feature_ está na fase [Beta Restrito](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta) para alguns _Realms_ e está disponível apenas para clientes específicos.
{% endhint %}

Esse recurso permite selecionar a versão com a qual deseja trabalhar em seus _pipelines_ implantados para obter melhor desempenho e processamento. Dessa forma, você pode mudar facilmente para uma versão do _Pipeline Engine_ que se adeque aos seus planos e forneça uma melhor resposta para seus _pipelines_.

{% hint style="info" %}
Para ter acesso à **Implantação**, você deve ter a **permissão** de _**Deployment:**_** Ler** e _**Deployment:**_** Criar nos ambientes desejados (test/ prod)**, para sua conta de usuário ou um grupo ao qual você pertence.
{% endhint %}

## O que é um _Pipeline Engine_?

A _Digibee Integration Platform_ utiliza um motor de execução denominado _Pipeline Engine_, que é responsável por executar os fluxos (_pipelines_) criados na Plataforma. O mecanismo não apenas interpreta os _pipelines_ construídos por meio da interface, mas também converte cada fluxo em uma instância de contêiner _Docker_ que é executada usando a tecnologia _Kubernetes_.

O _Pipeline Engine_ é conectado ao componente _Trigger_, que recebe as chamadas de diferentes tecnologias e as encaminha para o _Pipeline Engine_. O mecanismo de filas é o mecanismo central da _Digibee Integration Platform_.

[Se você quiser saber mais sobre o _Pipeline Engine_, leia este artigo sobre ele.](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine)

## Versão _Pipeline Engine Beta_

O _Pipeline Engine Beta_ atualizou todos os conectores e bibliotecas. Essas atualizações destinam-se principalmente a desenvolver o código e a tecnologia para melhorar o desempenho, a performance e o processamento para solucionar vulnerabilidades em bibliotecas descontinuadas. Um dos pontos mais importantes é o aprimoramento da segurança na Plataforma.

Abaixo estão algumas atualizações e benefícios desta versão:

* Aprimoramento da segurança na  Digibee Integration Platform;
* Mais estabilidade para o Digibee Integration Platform;
* Maior desenvolvimento da arquitetura da Plataforma;
* Códigos mais limpos e eficientes;
* Aumento de performance da Plataforma.

## Alterando a versão do _Pipeline Engine_

{% hint style="info" %}
**Importante:** você só pode mudar para a versão _Pipeline Engine Beta_ ao executar uma implantação ou reimplantação.
{% endhint %}

Quando estiver na página Run, você pode proceder da mesma forma que implanta ou reimplanta um _pipeline_, ou seja, por meio do botão **+CRIAR** no canto superior direito da página, ou pode ir diretamente ao _card_ do _pipeline_ e selecionar **Reimplantar** através dos três pontos no canto superior direito do _card_.&#x20;

Após selecionar como deseja proceder, uma aba lateral será aberta onde você poderá selecionar o _pipeline_ e sua versão como de costume. Em seguida, logo após a informação de Projeto, temos as informações da Implantação atual caso seja necessário verificar as configurações. Seguindo, você poderá selecionar a versão do _Pipeline Engine Beta_ utilizando um botão de seleção.

<figure><img src="../../.gitbook/assets/Pipeline engine -ptbr.jpg" alt=""><figcaption></figcaption></figure>

Se você quiser usar a versão do _Pipeline Engine Beta_ em seu _pipeline_, basta alternar o botão para o modo **Ativo**. No entanto, se você não deseja usar esta versão e fazer qualquer alteração, pode pular esta parte do processo e o botão permanecerá no modo **Inativo**.

Em seguida, tudo o que você precisa fazer é selecionar as configurações de implantação para seu _pipeline_ e concluir sua ação clicando em **IMPLANTAR** na parte inferior da página.

## Identificação no _card_ do Pipeline

Depois de selecionar e implantar o _pipeline_, o _card_ do _pipeline_ agora irá mostrar que esse _pipeline_ em específico está utilizando a versão _Pipeline Engine Beta_, desse modo deixando de uma forma mais fácil e rápida a identificação de qual _pipeline_ está usando a versão Regular ou versão _Beta_ do _Pipeline Engine_.

[Para saber mais sobre o status no _card_ do _pipeline_, leia este artigo.](https://docs.digibee.com/documentation/v/pt-br/run/status-de-implantacao-do-pipeline)

<figure><img src="../../.gitbook/assets/Pipeline engine card.jpg" alt=""><figcaption></figcaption></figure>
