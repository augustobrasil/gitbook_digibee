---
description: Conheça o componente e saiba como utilizá-lo.
---

# For Each

O **For Each** realiza um _loop_ dentro de uma estrutura JSON, processando cada elemento do _array_ em um _subpipeline_.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="310">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>JSON Path Expression</strong></td><td>Expressão que é aplicada à estrutura JSON recebida pelo componente <strong>For Each</strong>, filtrando-a. O <strong>For Each</strong> pode receber um objeto que possua vários elementos e a expressão <em>JSON Path</em> permite obter apenas aqueles que atenderem a uma condição específica.<br><br>Para aprimorar a utilização do componente <strong>For Each</strong>, recomendamos que as expressões utilizadas no parâmetro <strong>JSON Path Expression</strong> sejam validadas utilizando a seguinte referência: <a href="https://jsonpath.com/">https://jsonpath.com/</a>.</td><td>$</td><td><em>String</em></td></tr><tr><td><strong>Element Identifier</strong></td><td>Elemento único que identifica a linha em processamento (por exemplo, elemento "id").</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Parallel Execution</strong></td><td><p>Quando habilitada, a opção faz com que elementos do <em>array</em> recebido pelo <strong>For Each</strong> sejam processados em paralelo, com um limite de até 10 execuções concorrentes - ou seja, caso o <em>array</em> recebido pelo componente <strong>For Each</strong> tenha 20 elementos, os 10 primeiros terão seu processamento iniciado imediatamente. </p><p></p><p>Assim que um desses processamentos terminar, o próximo elemento do <em>array</em> será processado e assim por diante, até que todo o <em>array</em> tenha sido processado. Caso a opção <strong>Parallel Execution</strong> esteja desabilitada, os elementos do <em>array</em> recebido pelo <strong>For Each</strong> são processados em série - é preciso que o primeiro tenha sido processado para que o processamento do segundo elemento possa começar.</p></td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>A habilitação desse parâmetro suspende a execução do <em>pipeline</em> apenas quando há uma ocorrência grave na estrutura da iteração, impedindo a sua conclusão por completo. A ativação do parâmetro <strong>Fail On Error</strong> não tem ligação com erros ocorridos nos componentes utilizados para a construção dos <em>subpipelines</em> (<em>onProcess</em> e <em>onException</em>). Se você quiser que a execução seja interrompida para qualquer tipo de ocorrência de erro, avalie a utilização do componente <strong>Do While</strong>. <a href="https://docs.digibee.com/documentation/v/pt-br/components/logic/do-while">Clique aqui para ler sobre esse componente e validar se ele se aplica ao seu cenário.</a></td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## **Exemplos de Expressões JSON Path**

```
$.[?(@.status == 'EXPIRED')]
```

A expressão acima mostra como a mensagem recebida pelo componente pode ser filtrada: neste exemplo, o _array_ é a raiz do objeto e somente os elementos cujo atributo status seja EXPIRED serão processados pelo componente **For Each**.

```
$.body.*
```

Obtém todo o conteúdo do _body_ da mensagem recebida.

```
$.body.products.*
```

Obtém o conteúdo de um _array_ _products_ que está dentro do _body_ da mensagem recebida.

## Definindo o subpipeline que é executado a cada iteração <a href="#definindo-o-subpipeline-que--executado-a-cada-iterao" id="definindo-o-subpipeline-que--executado-a-cada-iterao"></a>

Para definir o _subpipeline_ que será executado a cada iteração, basta clicar no ícone **onProcess** do componente **For Each.**



<figure><img src="../../../.gitbook/assets/for each onprocess nov 23.png" alt=""><figcaption></figcaption></figure>

Ao clicar nesse ícone, um _subpipeline_ será criado (ou exibido, caso já exista). Então basta construir o fluxo desejado conforme a necessidade de execução de cada iteração.

{% hint style="info" %}
Caso sejam utilizados componentes [**Session Management**](../../structured-data/session-management.md) para manipular dados de cada elemento do _array_ no _subpipeline_ do **For Each** e a opção **Parallel Execution** esteja ativa, é necessário que a opção **Scoped** do [**Session Management**](../../structured-data/session-management.md) esteja ativa para que cada execução em paralelo acesse os seus respectivos dados.
{% endhint %}

## Tratando erros no loop <a href="#tratando-erros-no-loop" id="tratando-erros-no-loop"></a>

O comportamento padrão do **For Each** é interromper a execução caso algum erro seja encontrado. Erros são situações atípicas na execução de um _pipeline_ que incorrem em uma parada. Por exemplo, o uso de um componente [**Assert V2**](../../tools/assert-v2.md) causa um erro no _pipeline_ quando a condição de asserção não for satisfeita. Outras situações de erro ocorrem quando são utilizados componentes com a configuração **Fail On Error** habilitada.

Conforme explicado anteriormente, é possível definir um _subpipeline_ para tratamento de erros. A definição desse _subpipeline_ é feita através do ícone **onException** do componente **For Each**:



<figure><img src="../../../.gitbook/assets/for each onexception nov 23.png" alt=""><figcaption></figcaption></figure>

[Leia o artigo sobre _subpipelines_ para entender melhor o funcionamento.](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/subpipelines)

{% hint style="warning" %}
Não é possível interromper a execução de todo o loop **For Each**. A interrupção pode ser feita apenas na iteração atual, através de componentes que possuam o parâmetro **Fail On Error** ativado dentro dos _subpipelines_ _onProcess_ e _onException_.
{% endhint %}

## Erro grave de estrutura durante o _subpipeline_ onException <a href="#erro-durante-o-subpipeline-onexception" id="erro-durante-o-subpipeline-onexception"></a>

* o _loop_ será interrompido;
* o erro será lançado para o próximo componente ao qual o componente For Each esteja associado;
* caso o **For Each** esteja no fluxo principal do _pipeline_, então o _pipeline_ será interrompido;
* se o **For Each** estiver dentro de um componente que possui _subpipeline_, então o _subpipeline onException_ será invocado e o erro será informado na entrada desse _subpipeline_.

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

O **For Each** aceita qualquer estrutura de JSON que contenha um _array_. Se o _array_ não for a raiz do objeto, então uma expressão JSON Path deve ser definida para localizar e filtrar o _array_. Caso o componente **For Each** não receba um _array_, nenhum processamento será executado.

### Saída <a href="#sada" id="sada"></a>

```
{
    "total": 0,
    "success": 0,
    "failed": 0
}
```

* **total:** número total de elementos processados.
* **success:** número total de elementos processados com sucesso.
* **failed:** número total de elementos que não puderam ser processados.

{% hint style="info" %}
Para informar que uma linha foi processada corretamente e iterar o valor do campo `"success"`, cada execução do _subpipeline_ _onProcess_ deve responder com `{ "success": true }` ao seu término. Somente desta forma a mensagem de saída representará corretamente o resultado dos processamentos.
{% endhint %}
