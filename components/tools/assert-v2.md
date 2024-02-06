---
description: >-
  Descubra mais sobre o componente Assert V2 e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Assert V2

O **Assert V2** permite que você crie a interrupção da execução do seu _pipeline_ quando uma condição definida não for atendida. Essa condição será avaliada de acordo com itens da mensagem do _pipeline_, sendo que _Double Braces_ são utilizados para isso.

{% hint style="info" %}
Utilize o componente **Assert V2** para garantir uma condição ou interromper o fluxo.
{% endhint %}

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Condition</strong> <code>(DB)</code></td><td>Quando essa condição não for verdadeira, a execução do <em>pipeline</em> será interrompida.</td><td>N/A</td><td>Expressões <em>Double Braces</em></td></tr><tr><td><strong>Error Message</strong></td><td>Define a mensagem de erro que é retornada pelo <em>pipeline</em> quando a condição não for verdadeira.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Internal Error Message</strong></td><td>Campo onde você define a mensagem de erro interna quando a condição não for verdadeira (é uma mensagem apenas para fins internos).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>HTTP Status Code</strong></td><td>Status de retorno do componente.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td>N/A</td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens

### Entrada

O componente aceita qualquer mensagem de entrada e pode fazer uso dela através de _Double Braces_.

### Saída

O componente não altera nenhuma informação da mensagem de entrada quando a condição é verdadeira. Portanto, ela é retornada para o componente seguinte ou é utilizada como resposta final se o **Assert V2** for o último passo do _pipeline_.

Quando a condição for falsa e a propriedade **Fail On Error** for "true", a saída do componente segue a estrutura padrão:

<pre><code>{ 
<strong>    "timestamp": 1587151050249, 
</strong>    "error": "&#x3C;message declares in the config errorMessage>", 
    "code": &#x3C;errorCode>
}
</code></pre>

Se **Fail On Error** for "false":

```
{
    "error": "<message declares in the config errorMessage>",
    "internalErrorMessage": "<message declares in the config internalErrorMessage>",
    "code": <errorCode>,
    "success": false
}
```

Conforme visto, você deve utilizar expressões em _Double Braces_ no campo **Condition**. Aprenda mais no nosso[ artigo sobre Funções _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/funcoes-double-braces).

## Assert V2 em ação

* `{{ AND( EQUALTO(message.name, "Arthur"), LESSTHAN( message.number, 40)) }}`

Recebendo uma mensagem:

```
{ 
   "name": "Jimmy", 
   "number": 39
}
```

A condição resultará "false".

* `{{ AND( EQUALTO(message.name, "Arthur"), LESSTHAN( message.number, 40)) }}`

Recebendo uma mensagem:

```
{ 
   "name": "Arthur", 
   "number": 39
}
```

A condição resultará "true".\
