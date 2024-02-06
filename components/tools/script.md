---
description: >-
  Descubra mais sobre o componente Script (JavaScript) e saiba como usá-lo na
  Digibee Integration Platform.
---

# Script (JavaScript)

O componente **Script (JavaScript)** permite executar trechos de código JavaScript, também conhecido como ECMAScript.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="294">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Code</strong></td><td>Campo onde o código JavaScript deve ser inserido.</td><td>var currentDate = <a href="http://moment.tz/">moment.tz</a>(new Date(), "America/Sao_Paulo");<br>output = {currentDate: currentDate.format()};</td><td><em>String</em></td></tr><tr><td><strong>Script Timeout</strong></td><td>Tempo para que o <em>script</em> expire (em milissegundos).</td><td>10000</td><td>Inteiro</td></tr></tbody></table>

## Fluxo de mensagens

### Entrada

O componente **Script (JavaScript)** pode receber parâmetros de componentes prévios através do objeto `"body"`. Ou seja, caso a saída do componente anterior ao **Script (JavaScript)** tiver uma saída que inclui um objeto chamado `"body"`, é possível acessá-lo diretamente no código do **Script (JavaScript)**.

* **body:** objeto importado para o escopo do código do **Script (JavaScript)**.

Por exemplo, caso a entrada seja:

```
{
   "body": {
       "company": "Digibee"
   }
}
```

Então no campo **Code** será possível fazer algo como:

```
var x = body.company;
```

### Saída

O código executado no componente pode produzir uma saída, desde que ela seja atribuída à variável global chamada _output_.

* **success:** `"true"` se a execução do código foi bem sucedida; caso contrário, `"false"`.
* **output:** saída personalizável do componente.

Por exemplo, se você quiser que a saída do componente **Script (JavaScript)** seja `'Hello world'` basta atribuí-lo à variável _output_:

```
output = 'Hello world';
```

O resultado após executar o _pipeline_ será:

```
{
   "success": true,
   "output": "Hello world"
}
```

Também é possível construir um objeto JSON como saída:

```
output = { "company": "Digibee" }
```

O resultado após executar o _pipeline_ será:

```
{
   "success": true,
   "output": {
       "company": "Digibee"
   }
}
```

Caso algum erro ocorra durante a execução do _script_, a seguinte saída é apresentada após a execução do _pipeline_:

```
{
   "success": false,
   "error": "Error message"
}
```

{% hint style="warning" %}
Por questões de segurança, não é possível executar nenhuma função que faça uma chamada externa a partir do componente **Script (JavaScript)**, como por exemplo `fetch()` ou `XMLHttpRequest()`. Também não é possível importar bibliotecas usando `require`.
{% endhint %}

As seguintes bibliotecas já estão disponíveis e podem ser utilizadas:

* Lodash (variável global para utilizar lodash lib: 'lodash')
* Moment Timezone (variável global para utilizar moment-timezone: 'moment')
