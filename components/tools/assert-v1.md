---
description: >-
  Descubra mais sobre o componente Assert V1 e saiba como usá-lo na Digibee
  Integration Platform.
---

# Assert V1 (descontinuado)

{% hint style="info" %}
O **Assert V1** foi descontinuado e não é mais atualizado. Consulte a documentação da versão mais recente da _feature_: [Assert V2](assert-v2.md).
{% endhint %}

O **Assert V1** permite criar a interrupção da execução de seu _pipeline_ quando uma condição definida por você não for atendida. Essa condição será avaliada de acordo com itens da mensagem do _pipeline_ que o componente **Assert** recebe através de uma Linguagem de Expressão.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="323">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Condition</strong></td><td>Condição passada através da Linguagem de Expressão SIMPLE. Se não for verdadeira, a execução do <em>pipeline</em> será interrompida.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Error Message</strong></td><td>Define a mensagem de erro que é retornada pelo <em>pipeline</em> quando a condição passada não for verdadeira.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>HTTP Status Code</strong></td><td><em>Status</em> HTTP de retorno do componente.</td><td>N/A</td><td>Inteiro</td></tr></tbody></table>

## Fluxo de Mensagens

### Entrada

O componente aceita qualquer mensagem de entrada e pode fazer uso dela através da Linguagem de Expressão SIMPLE.

#### Saída

O componente não altera nenhuma informação da mensagem de entrada quando a condição é verdadeira. Portanto, ela é retornada para o componente seguinte ou é utilizada como resposta final se este componente for o último passo do _pipeline_.

Quando a condição não for verdadeira, a saída desse componente seguirá a estrutura padrão:

```
{ 
   "timestamp": <momento da interrupção no formato timestamp>, 
   "error": "<mensagem configurada no parâmetro Error Message>", 
   "code": <status code configurado no parâmetro HTTP Status Code>
}
```

## Tecnologia SIMPLE

É uma Linguagem de Expressão destinada a ser simples e prática para avaliar Expressões e Predicados sem exigir novas dependências ou conhecimento da tecnologia JSON Path.

Imagine que você precise validar determinada informação de cidade trafegada pelo _pipeline_:

```
{
   "cidade" : "São Paulo"
}
```

Apenas mensagens que contenham o campo "cidade" com o valor "São Paulo" devem ser aceitas. Do contrário, a execução do _pipeline_ deve ser interrompida.

O parâmetro **Condition** do componente **Assert V1** deverá ser configurado da seguinte maneira:

```
   #{cidade} == 'São Paulo'
```

Conheça as demais opções para a declaração de expressões SIMPLE:

* **==**: igual a.
* **=\~**: igual a, ignorando maiúsculas e minúsculas (quando comparando _strings_).
* **>**: maior que.
* **>=**: maior ou igual a.
* **<**: menor que.
* **!=**: diferente.
* **!=\~**: diferente de, ignorando maiúsculas e minúsculas (quando comparando _strings_).
* **regex**: valida uma RegEx contra a _string_ informada. Exemplo: #{cidade} regex 'S.\*'
* **&&**: operador lógico E. Exemplo: #{cidade} == 'Sao Paulo' && #{estado} == 'SP'
* **||**: operador lógico OU. Exemplo: #{cidade} == 'Sao Paulo' || #{estado} == 'SP'
* **contains**: valida se determinado valor está contido em uma _string_. Exemplo: #{cidade} contains 'Paulo'
