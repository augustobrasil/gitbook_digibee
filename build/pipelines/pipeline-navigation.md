---
description: Conheça as funcionalidades que facilitam a navegação em um pipeline.
---

# Navegação em um pipeline

O Canvas contém funcionalidades que melhoram a experiência de navegação em um _pipeline_, facilitando e agilizando a construção de fluxos de integração.

### Botões de controle do Canvas <a href="#h_b1362a896d" id="h_b1362a896d"></a>

<figure><img src="../../.gitbook/assets/Canvas control buttons.png" alt=""><figcaption></figcaption></figure>

Use os botões de **Minimapa**, **Reorganizar**, **Ampliar zoom** e **Reduzir zoom** no canto inferior direito do Canvas para navegar pelo _pipeline_. O botão do **Minimapa** é usado para abrir e fechar o mini-mapa do Canvas. O de **Reorganizar** arranja os componentes utilizados de forma que facilite a visualização de cada etapa do fluxo. Os dois últimos botões são utilizados para controlar o zoom do Canvas.

Ao reorganizar, os componentes soltos (não conectados ao fluxo) são ajustados à esquerda da tela, um abaixo do outro. Já os componentes conectados ao fluxo, por sua vez, são alinhados horizontalmente.

### Movimentação automática <a href="#h_0009c98480" id="h_0009c98480"></a>

Com o _auto pan_, ao segurar um componente e o arrastar, a nova tela segue o cursor, facilitando a navegação em _pipelines_ muito grandes. Desse modo, você consegue arrastar um componente para qualquer área do Canvas, e a tela o acompanhará.

### Flow tree

Esta funcionalidade é uma estrutura em forma de árvore que exibe os componentes de um _pipeline_ de uma forma mais simples e centralizada. Utilizando a _Flow tree_, você pode visualizar todos os componentes do _pipeline_ principal e de todos os _subpipelines_, conectados ou não, em um só lugar.

<figure><img src="../../.gitbook/assets/02 - Flow tree - port.gif" alt=""><figcaption></figcaption></figure>

Para navegar até um componente ou _subpipeline_ específico, dê um duplo clique sobre ele dentro da estrutura da Árvore ou clique no ícone de destino (![](<../../.gitbook/assets/image1 (3).png>)).

Você também pode editar os parâmetros de configuração de um componente a partir da _Flow tree_. Para isso, clique no ícone de engrenagem (![](<../../.gitbook/assets/image2 (2).png>)) do componente dentro da estrutura da _Flow tree_ para abrir o formulário de configuração.

{% hint style="info" %}
A _Flow tree_ simplifica a navegação e o entendimento da lógica aplicada no fluxo de integração, permitindo que você veja os componentes de um _subpipeline_ enquanto visualiza o _pipeline_ principal ou vice-versa, facilitando depuração durante a construção do _pipeline_.
{% endhint %}

### Campo de busca&#x20;

Use o Campo de busca localizado ao lado esquerdo do Canvas para buscar por componentes, Contas, _Globals_ e quaisquer outros campos definidos nos formulários de configuração dos componentes utilizados no _pipeline_.

<figure><img src="../../.gitbook/assets/Campo de busca.gif" alt="O botão Focar foca o resultado da pesquisa no pipeline, e o botão Configurações abre o formulário de configurações do componente."><figcaption></figcaption></figure>

Na barra de pesquisas, digite o nome ou partes do nome de um componente, Conta, _Global_ ou qualquer outro valor definido nos campos do formulário de um componente. Os resultados são listados logo abaixo e estão divididos nas seguintes seções:

* Contas
* _Globals_
* Componentes
* Outros campos

Quando clicar no resultado ou no botão **Focar**, o componente é focado no _pipeline_. Você também pode editar as informações do componente clicando no botão **Configurações** representado pelo ícone de engrenagem.

