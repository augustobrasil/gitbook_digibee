---
description: >-
  Saiba quais são as funções de comparação associadas aos Double Braces e como
  utilizá-las.
---

# Funções de comparação

As funções foram criadas para:

* acelerar ainda mais a criação das suas integrações
* diminuir a complexidade dos seus _pipelines_
* simplificar conversões e transformações dos dados durante o fluxo dos seus _pipelines_

As funções de comparação realizam comparações de entradas booleanas e estão disponíveis para componentes que suportam expressões com _Double Braces_. Para saber como passar informações para os componentes utilizando esse recurso, clique [aqui](./).

## AND <a href="#and" id="and"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

Na função de comparação AND, ambos os valores passados devem ser "true" para retornar "true".

### **Sintaxe**

```
AND( boolean1, boolean2, …, booleanN )
```

No exemplo abaixo, o valor "false" será atribuído:

```
{
"and": {{ AND( true, false ) }}
}
```

{% hint style="info" %}
o valor `null` é considerado como `false`. O retorno dessa função será `true` ou `false`.
{% endhint %}

## NOT <a href="#not" id="not"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função de comparação NOT retorna o valor oposto recebido.

### **Sintaxe**

```
NOT( boolean )
```

No exemplo abaixo o valor "true" será atribuído:

```
{
"not": {{ NOT( true ) }}
}
```

{% hint style="info" %}
o valor `null` é considerado como `false`. O retorno dessa função será `true` ou `false`.
{% endhint %}

## OR <a href="#or" id="or"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

Na função de comparação OR, pelo menos um dos valores passados deve ser "true" para retornar "true".

### **Sintaxe**

```
OR(boolean1, boolean2, …, booleanN )
```

No exemplo abaixo, o valor "true" será atribuído:

```
{
"or": {{ OR( true, false ) }}
}
```

{% hint style="info" %}
o valor `null` é considerado como `false`. O retorno dessa função será `true` ou `false`.
{% endhint %}

## XOR <a href="#xor" id="xor"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso a elemento do JSON de entrada de um componente.

A função de comparação XOR só retornará "true" se os valores passados forem opostos. Exemplo: TRUE e FALSE ou FALSE e TRUE.

Com o suporte a múltiplos valores booleanos, a estratégia de resolução da função é realizada em pares, com início da esquerda para direita. Exemplo: (TRUE e FALSE e TRUE) = FALSE ou (FALSE e TRUE e FALSE e FALSE) = TRUE .

### **Sintaxe**

```
XOR(boolean1, boolean2, …, booleanN )
```

No exemplo abaixo, o valor "true" será atribuído:

```
{
"xor": {{ XOR( true, false, true, true ) }}
}
```

{% hint style="info" %}
o valor `null` é considerado como `false`. O retorno dessa função será `true` ou `false`.
{% endhint %}

Conheça também as funções:

* [numéricas](funcoes-numericas.md)
* [condicionais](funcoes-condicionais.md)
* [de data](funcoes-de-data.md)
* [de arquivo](funcoes-de-arquivo.md)
* [de JSON](funcoes-de-json.md)
* [matemáticas](funcoes-matematicas.md)
* [de _string_](https://intercom.help/godigibee/pt-BR/articles/4623887-double-braces-funcoes-de-string)
* [de utilidades](double-braces-funcoes-de-utilidades.md)
