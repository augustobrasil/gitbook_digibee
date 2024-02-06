---
description: Conheça o componente e saiba como utilizá-lo.
---

# Block Execution

O **Block Execution** declara um trecho de _pipeline_ para um fim específico. Ele pode ser usado para:

* separar logicamente trechos de um _pipeline_ extenso de maneira que o seu comportamento se torne mais fácil de entender;
* permitir que os diferentes caminhos criados por componentes de desvio de fluxo possam se unir ao final do trecho declarado (mais detalhes adiante);
* declarar um trecho de _pipeline_ para tratamento de erros específicos.

## Parâmetros

O **Block Execution** não possui nenhuma configuração específica para o seu funcionamento, bastando apenas construir os _subpipelines onProcess_ e _onException_.

## Subpipelines

O **Block Execution** faz parte de um conjunto de componentes que trabalham com _subpipelines_ para executar as suas funções. Para mais informações, [leia a documentação sobre Subpipelines](../../build/pipelines/subpipelines.md).&#x20;

Para trabalhar com este tipo de componente, você precisa levar em consideração 2 conceitos importantes:

* **Subpipeline definido no bloco onProcess:** o _pipeline_ definido nesse bloco é o trecho de execução do componente.
* **Subpipeline definido no bloco onException:** o _pipeline_ definido nesse bloco é executado sempre que ocorrer uma falha no bloco _onProcess_. Veja mais detalhes abaixo.

## Definindo o subpipeline executado como parte do bloco <a href="#definindo-o-subpipeline-executado-como-parte-do-bloco" id="definindo-o-subpipeline-executado-como-parte-do-bloco"></a>

Para definir o _subpipeline_ a ser executado, basta clicar no ícone **onProcess** do componente:



<figure><img src="../../.gitbook/assets/block exec example nov 23.png" alt=""><figcaption><p>O ícone <em>onProcess</em> fica destacado acima do componente</p></figcaption></figure>

Ao clicar nesse ícone, um _subpipeline_ será criado (ou exibido, caso já exista). Então basta construir o fluxo desejado conforme a necessidade de execução.

{% hint style="info" %}
A entrada desse _subpipeline_ será alimentada com a mensagem imediatamente anterior ao **Block Execution**.
{% endhint %}

## Utilizando o Block Execution para unir caminhos diferentes de um componente de desvio de fluxo <a href="#utilizando-o-block-execution-para-unir-caminhos-diferentes-de-um-componente-de-desvio-de-fluxo" id="utilizando-o-block-execution-para-unir-caminhos-diferentes-de-um-componente-de-desvio-de-fluxo"></a>

Quando um componente de desvio de fluxo é utilizado, assim como o [**Choice**](choice.md), múltiplos caminhos são criados no _pipeline_ para atender ao desvio de fluxo desejado. Por exemplo:



<figure><img src="../../.gitbook/assets/block exec ex2 nov 23.png" alt=""><figcaption><p>Exemplo de <em>pipeline</em> usando múltiplos caminhos</p></figcaption></figure>

No caso acima, você pode ver 2 desvios de fluxo: **path 1** e **path 2**, que levam a caminhos completamente diferentes no _pipeline_. Suponha que seja necessário unir esses caminhos para continuar a execução do _pipeline_. O componente **Block Execution** tem a função de realizar esse agrupamento de caminhos diferentes em um bloco de execução separado. Quando um dos caminhos terminar, o controle volta para o **Block Execution** que, por sua vez, é seguido pelo próximo componente. Veja:



<figure><img src="../../.gitbook/assets/block exec ex3 nov 23.png" alt=""><figcaption><p>Exemplo do Block Execution sendo usado para agrupar caminhos diferentes</p></figcaption></figure>



Nesse outro exemplo acima, o **Block Execution** é seguido pelo [**JSON Generator**](../tools/json-generator.md). Dentro do _subpipeline onProcess_ do **Block Execution**, foi utilizado um componente **Choice** com desvios.

Quando os desvios chegam ao final, eles encerram o **Block Execution**, que retorna ao _pipeline_ principal e executa o componente seguinte - nesse caso, o **JSON Generator**.

Dessa forma, é possível unir e organizar _subpipelines_ que contenham fluxos com ramificações.

## Tratamento de erros <a href="#tratamento-de-erros" id="tratamento-de-erros"></a>

Assim como todos os outros componentes que possuem os _subpipelines_ _onProcess_ e _onException_, o **Block Execution** também faz o tratamento de erros por meio da execução do _subpipeline_ _onException_.

Um erro pode ser ocasionado por outros componentes quando eles identificam situações adversas. Geralmente os componentes possuem uma propriedade de configuração denominada **Fail On Error**, que controla se você deseja ou não gerar um erro que possa ser tratado em fluxos _onException_.

Assim, quando um componente "lança" um erro e está com a propriedade **Fail On Error** ativada, o **Block Execution** intercepta o erro e o envia para tratamento no _subpipeline_ _onException_.

Estas são as situações especiais que você deve levar em consideração:

* se um fluxo _onException_ não for definido, o **Block Execution** simplesmente repassa o erro adiante para que outro componente com execução por _subpipeline_ o trate. Por outro lado, se o fluxo principal do _pipeline_ for utilizado, então o _pipeline_ é encerrado com o erro;
* se um novo erro ocorre durante o _subpipeline onException_, o **Block Execution** também repassa o erro adiante para que outro componente com execução por _subpipeline_ o trate. Mas se o fluxo principal do _pipeline_ for utilizado, o _pipeline_ é igualmente encerrado com o erro.
