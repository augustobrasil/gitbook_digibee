---
description: >-
  Descubra mais sobre o componente Do While e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Do While

O **Do While** permite a construção de blocos em _loop_ dentro de um _pipeline_. Ele faz parte de um conjunto de componentes que trabalham com _subpipelines_ para executar as suas funções.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="293">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Iteration</strong></td><td>Define o número máximo de vezes que o <em>loop</em> é executado (é possível parar o <em>loop</em> antes desse número ser atingido).</td><td>10</td><td>Inteiro</td></tr><tr><td><strong>Timeout</strong></td><td>Tempo máximo que o <em>loop</em> deverá executar</td><td>300000</td><td>Inteiro</td></tr><tr><td><strong>Loop Index</strong></td><td>Se a opção estiver ativada, uma propriedade <code>“loopIndex”</code> será inserida na mensagem apresentada a cada iteração do <em>loop</em> e informará o índice da iteração atual (1, 2, 3, …).</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Interrupt Loop On Error</strong></td><td>Se opção for ativada, um erro ocorrido dentro de uma iteração causará a interrupção do <em>loop</em> como um todo. Do contrário, o <em>loop</em> continuará a partir da próxima iteração.</td><td><em>True</em></td><td>Booleano</td></tr></tbody></table>

## Definindo o subpipeline que é executado a cada iteração <a href="#definindo-o-subpipeline-que--executado-a-cada-iterao" id="definindo-o-subpipeline-que--executado-a-cada-iterao"></a>

Para trabalhar com esse tipo de componente, é importante levar em consideração:

* _**Subpipeline**_** definido no bloco onProcess:** o _pipeline_ definido nesse bloco é executado a cada iteração do _loop_. Portanto, se o _loop_ tem 10 iterações, o _subpipeline_ é executado 10 vezes.
* _**Subpipeline**_** definido no bloco onException:** o _pipeline_ definido nesse bloco é executado sempre que uma iteração do _loop_ resultar em uma falha.

Para definir o _subpipeline_ que será executado a cada iteração, basta clicar no ícone **onProcess** do componente **Do While**:

<figure><img src="../../.gitbook/assets/Do While onprocess nov 23.png" alt=""><figcaption></figcaption></figure>

Ao clicar nesse ícone, um _subpipeline_ será criado (ou exibido, caso já exista). Então basta construir o fluxo desejado conforme a necessidade de execução de cada iteração.

{% hint style="warning" %}
A entrada desse _subpipeline_ será alimentada com a mensagem imediatamente anterior ao **Do While**. Isso acontecerá na execução da iteração #1 do _loop_. Nas demais iterações, a mensagem apresentada será a mensagem final da iteração anterior e assim por diante. Se **Loop Index** estiver ativo, uma propriedade `loopIndex` será inserida na mensagem informando a iteração atual.
{% endhint %}

## Interrompendo um loop <a href="#interrompendo-um-loop" id="interrompendo-um-loop"></a>

Para interromper um _loop_ antes do número máximo de iterações definido, basta informar uma propriedade `"loopBreak: true"` no final da iteração. Se a propriedade for encontrada, o _loop_ será quebrado.

Uma maneira de informar essa propriedade é usando o componente [**JSON Generator**](../tools/json-generator.md), que permite a definição de JSONs arbitrários no fluxo do _pipeline_.

## Tratando erros no loop <a href="#tratando-erros-no-loop" id="tratando-erros-no-loop"></a>

O comportamento padrão do **Do While** é interromper o _loop_ caso algum erro seja encontrado. Erros são situações atípicas na execução de um _pipeline_ que incorrem em uma parada. Por exemplo, o uso de um componente Assert causa um erro no _pipeline_ quando a condição de asserção não for satisfeita. Outras situações de erro ocorrem quando são utilizados componentes com a configuração **Fail On Error** habilitada.

Conforme explicado anteriormente, é possível definir um _subpipeline_ para tratamento de erros. A definição desse _subpipeline_ é feita através do ícone **onException** do componente **Do While**:

<figure><img src="../../.gitbook/assets/Do While onexception nov 23.png" alt=""><figcaption></figcaption></figure>

A entrada desse _subpipeline_ será alimentada com uma mensagem de erro, que informará o que ocorreu com a iteração e o índice da iteração (`loopIndex`) que causou a falha.

{% code overflow="wrap" %}
```
{"timestamp": <timestamp do erro>"error": <mensagem do erro>"code": 500"loopIndex": <índice da iteração onde ocorreu o erro>}
```
{% endcode %}

## Cenários de utilização do componente Do While com tratamento de erros <a href="#cenrios-de-utilizao-do-componente-do-while-com-tratamento-de-erros" id="cenrios-de-utilizao-do-componente-do-while-com-tratamento-de-erros"></a>

### Propriedade "Interrupt loop on error" habilitada e nenhum subpipeline definido em onException <a href="#propriedade-interrupt-loop-on-error-habilitada-e-nenhum-subpipeline-definido-em-onexception" id="propriedade-interrupt-loop-on-error-habilitada-e-nenhum-subpipeline-definido-em-onexception"></a>

* o _pipeline_ será interrompido imediatamente.
* um erro será emitido a partir do componente **Do While**.
* nenhum outro componente será invocado após o **Do While**_._

### Propriedade "Interrupt loop on error" habilitada e um subpipeline definido em onException <a href="#propriedade-interrupt-loop-on-error-habilitada-e-um-subpipeline-definido-em-onexception" id="propriedade-interrupt-loop-on-error-habilitada-e-um-subpipeline-definido-em-onexception"></a>

* o _pipeline_ será interrompido imediatamente.
* o _subpipeline_ definido em _onException_ será executado e a saída dele alimentará o próximo componente após o **Do While**_._
* o componente após o **Do While** será invocado.

### Propriedade "Interrupt loop on error" desabilitada e nenhum subpipeline definido em onException <a href="#propriedade-interrupt-loop-on-error-desabilitada-e-nenhum-subpipeline-definido-em-onexception" id="propriedade-interrupt-loop-on-error-desabilitada-e-nenhum-subpipeline-definido-em-onexception"></a>

* a iteração onde ocorreu o erro será interrompida.
* uma mensagem de erro padrão será informada na entrada da próxima iteração e o _loop_ continuará a ser executado normalmente.

### Propriedade "Interrupt loop on error" desabilitada e um subpipeline definido em onException <a href="#propriedade-interrupt-loop-on-error-desabilitada-e-um-subpipeline-definido-em-onexception" id="propriedade-interrupt-loop-on-error-desabilitada-e-um-subpipeline-definido-em-onexception"></a>

* a iteração onde ocorreu o erro será interrompida.
* o _subpipeline_ definido em _onException_ será executado e a saída dele alimentará a próxima iteração.
* o _loop_ continuará a ser executado normalmente.

## Erro durante o subpipeline onException <a href="#erro-durante-o-subpipeline-onexception" id="erro-durante-o-subpipeline-onexception"></a>

* o _loop_ será interrompido.
* o erro será lançado para o próximo componente ao qual o componente **Do While** esteja associado.
* caso o **Do While** esteja no fluxo principal do _pipeline_, então o _pipeline_ será interrompido.
* se o **Do While** estiver dentro de um componente que possui _subpipeline_, então o _subpipeline onException_ será invocado e o erro será informado na entrada desse _subpipeline**.**_
