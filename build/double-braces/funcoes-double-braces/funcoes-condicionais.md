---
description: >-
  Saiba quais são as funções condicionais associadas aos Double Braces e como
  utilizá-las.
---

# Funções de condição

As funções foram criadas para:

* acelerar ainda mais a criação das suas integrações
* diminuir a complexidade dos seus _pipelines_
* simplificar conversões e transformações dos dados durante o fluxo dos seus _pipelines_

As funções condicionais retornam um valor de acordo com o critério que você estabeleceu e estão disponíveis para componentes que suportam expressões com _Double Braces_. Para saber como passar informações para os componentes utilizando esse recurso, clique [aqui](./).

## EQUALTO <a href="#equalto" id="equalto"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função compara dois objetos (que podem ser números, _strings_, _arrays_, etc.) e verifica se são iguais.

### **Sintaxe**

```
EQUALTO(obj1, obj2 )
```

Vamos supor que você precise validar se este objeto

```
{
"body1":{
"cep": “01200-030”
}
}
```

é igual a este:

```
{
"body2":{
"CEP": “01200-030”
}
}
```

No exemplo abaixo o valor `false` será atribuído, pois os objetos são diferentes:

```
{
"valid": {{ EQUALTO( message.body1, message.body2 ) }}
}
```

{% hint style="info" %}
O retorno dessa função será `true` ou `false`.
{% endhint %}

## GREATERTHAN <a href="#greaterthan" id="greaterthan"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função compara se o primeiro número é maior que o segundo.

### **Sintaxe**

```
GREATERTHAN(num1, num2)
```

### **Payload**

```
{
"num1": 1,
"num2": 2
}
```

No exemplo abaixo o valor "false" será atribuído:

```
{
"valid": {{ GREATERTHAN( message.num1, message.num2 ) }}
}
```

O valor _null_ é considerado como o menor valor possível para comparação.

GREATERTHAN( null, null ) retornará "false".

{% hint style="info" %}
O retorno dessa função será `true` ou `false`.
{% endhint %}

## GREATERTHANEQUAL <a href="#greaterthanequal" id="greaterthanequal"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função compara se o primeiro número é maior ou igual ao segundo.

### **Sintaxe**

```
GREATERTHANEQUAL(num1, num2 )
```

### **Payload**

```
{
"num1": 1,
"num2": 2
}
```

No exemplo abaixo o valor `false` será atribuído:

```
{
"valid": {{ GREATERTHANEQUAL( message.num1, message.num2 ) }}
}
```

O valor `null` é considerado como o menor valor possível para comparação.

`GREATERTHANEQUAL(null, null)` retornará `true`.

{% hint style="info" %}
O retorno dessa função será `true` ou `false`.
{% endhint %}

## IF <a href="#if" id="if"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função permite que você faça comparações lógicas entre um valor e aquilo que você espera.

Portanto, uma instrução IF pode ter 2 resultados. O primeiro resultado acontece quando a comparação é verdadeira e o segundo quando a comparação é falsa.

### **Sintaxe**

```
IF(comparação, valor-se-verdadeiro, valor-se-falso)
```

Vamos supor que você precise tomar decisões dependendo se o valor recebido é `true` ou `false`:

```
{
"boolean": false
}
```

No exemplo abaixo o valor da condição (valor-se-falso) será atribuído ao JSON:

```
{
"cep": {{ IF( message.boolean, "cep-ok", "cep-nao-ok" ) }}
}
```

{% hint style="info" %}
O retorno dessa função será qualquer valor passado nas mensagens da condicional `true`/`false`.
{% endhint %}

## LESSTHAN <a href="#lessthan" id="lessthan"></a>

Utilizando _Double Brace_s, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função compara se o primeiro número é menor que o segundo.

### **Sintaxe**

```
LESSTHAN(num1, num2 )
```

### **Payload**

```
{
"num1": 1,
"num2": 2
}
```

No exemplo abaixo o valor "true" será atribuído:

```
{
"valid": {{ LESSTHAN( message.num1, message.num2 ) }}
}
```

O valor `null` é considerado como o menor valor possível para comparação.

`LESSTHAN(null, null)` retornará `false`.

{% hint style="info" %}
O retorno dessa função será `true` ou `false`.
{% endhint %}

## LESSTHANEQUAL <a href="#lessthanequal" id="lessthanequal"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função compara se o primeiro número é menor ou igual ao segundo.

### **Sintaxe**

```
LESSTHANEQUAL(num1, num2)
```

### **Payload**

```
{
"num1": 1,
"num2": 2
}
```

No exemplo abaixo o valor `true` será atribuído:

```
{
"valid": {{ LESSTHANEQUAL( message.num1, message.num2 ) }}
}
```

O valor `null` é considerado como o menor valor possível para comparação.

`LESSTHANEQUAL(null, null)` retornará `true`.

{% hint style="info" %}
O retorno dessa função será `true` ou `false`.
{% endhint %}

## ISOBJECT <a href="#isobject" id="isobject"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função permite que você verifique se o argumento passado é um objeto.

**Sintaxe**

```
ISOBJECT(objeto)
```

Vamos supor que você precise verificar se o argumento recebido é um objeto:

```
{
"argument": false
}
```

Validando o argumento:

```
{
"isObject": {{ ISOBJECT( message.argument) }}
}
```

O retorno será `false`, pois o valor não é um objeto.

Agora passando um objeto para a função:

```
{
"argument": {
"test": "xpto"
}
}
```

Validando o argumento:

```
{
"isObject": {{ ISOBJECT( message.argument) }}
}
```

O retorno será `true`.

## ISARRAY <a href="#isarray" id="isarray"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função permite que você verifique se o argumento passado é um _array_.

**Sintaxe**

```
ISARRAY(objeto)
```

Vamos supor que você precise verificar se o argumento recebido é um _array_:

```
{
"argument": false
}
```

Validando o argumento:

```
{
"isObject": {{ ISARRAY( message.argument) }}
}
```

O retorno será `false`, pois o valor não é um _array_.

Agora passando um objeto para a função:

```
{
"argument": [{
"test": "xpto"
}]
}
```

Validando o argumento:

```
{
"isArray": {{ ISARRAY( message.argument) }}
}
```

O retorno será `true`.

## ISBOOLEAN <a href="#isboolean" id="isboolean"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função permite que você verifique se o argumento passado é um valor booleano.

### **Sintaxe**

```
ISBOOLEAN(objeto)
```

Vamos supor que você precise verificar se o argumento recebido é um valor booleano:

```
{
"argument": false
}
```

Validando o argumento:

```
{
"isObject": {{ ISBOOLEAN( message.argument) }}
}
```

O retorno será `true`, pois o valor é booleano.

Agora passando um objeto para a função:

```
{
"argument": {
"test": "xpto"
}
}
{"isBoolean": {{ ISBOOLEAN( message.argument) }}}
```

Validando o argumento:

```
{
"isBoolean": {{ ISBOOLEAN( message.argument) }}
}
```

O retorno será `false`.

## ISSTRING <a href="#isstring" id="isstring"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função permite que você verifique se o argumento passado é uma _string_.

### **Sintaxe**

```
ISSTRING(objeto)
```

Vamos supor que você precise verificar se o argumento recebido é uma _string_:

```
{
"argument": "test"
}
```

Validando o argumento:

```
{
"isString": {{ ISSTRING( message.argument) }}
}
```

O retorno será `true`, pois o valor é uma _string_.

## ISNUMBER <a href="#isnumber" id="isnumber"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função permite que você verifique se o argumento passado é um número.

### **Sintaxe**

```
ISNUMBER(objeto)
```

Vamos supor que você precise verificar se o argumento recebido é um número:

```
{
"argument": 123
}
```

Validando o argumento:

```
{
"isNumber": {{ ISNUMBER( message.argument) }}
}
```

O retorno será `true`, pois o valor é um número.

## ISNULL <a href="#isnull" id="isnull"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função permite que você verifique se o argumento passado é `null`.

### **Sintaxe**

```
ISNULL(objeto)
```

Vamos supor que você precise verificar se o argumento recebido é um valor _null_:

```
{
"argument": null
}
```

Validando o argumento:

```
{
"isNull": {{ ISNULL( message.argument) }}
}
```

O retorno será `true`, pois o valor é um valor _null_.

## SWITCHCASE <a href="#switchcase" id="switchcase"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função permite que você passe várias comparações e os devidos parâmetros que devem ser retornados caso alguma dessas validações retorne `true`. Se nenhuma validação retornar `true`, valor padrão configurado será utilizado.

### **Sintaxe**

```
SWITCHCASE(defaultValue, condition1, result1, condition2, result2, …., conditionN, resultN)
```

Vamos supor que você precise validar algumas condições para tomada de decisão:

```
{
"argument": null
}
```

Validando o argumento:

```
{
"result": {{ SWITCHCASE("failed", ISNULL(message.argument), "ok", ISNUMBER(message.argument), "nok" ) }}
}
```

Portanto, a configuração da função ficará:

**Valor default:** "failed"

**Condition 1:** ISNULL(message.argument)

**Result If Condition 1 Matches:** "ok"

**Condition 2:** ISNUMBER(message.argument)

**Result If Condition 2 Matches:** "nok"

O retorno será "ok", pois a primeira condição foi atendida.

Conheça também as funções:

* [de comparação](funcoes-de-comparacao.md)
* [numéricas](funcoes-numericas.md)
* [de data](funcoes-de-data.md)
* [de arquivo](funcoes-de-arquivo.md)
* [de JSON](funcoes-de-json.md)
* [matemáticas](funcoes-matematicas.md)
* [de _string_](funcoes-de-string.md)
* [de utilidades](double-braces-funcoes-de-utilidades.md)
