---
description: Saiba mais sobre o componente e como utilizá-lo.
---

# JSLT

O componente **JSLT** permite manipular um JSON através da JSLT, uma linguagem para processamento e consulta de JSON. Para mais informações, [leia a documentação oficial no Gitbub](https://github.com/schibsted/jslt).

O componente é útil para realizar diversas ações, como:

* modificar a estrutura de um JSON e manter seus valores;
* adicionar, extrair e remover dados de um JSON;
* classificar a estrutura de um JSON;
* modificar os valores em um JSON através de funções como manipulação de texto, cálculos matématicos, conversões entre tipos diferentes de dados, entre outras;
* acessar e manipular dados de _arrays_.

Dê uma olhada nos parâmetros de configuração do componente:

* **Payload:** o conteúdo JSON a ser manipulado. Esse campo suporta [expressões Double Braces](https://docs.digibee.com/documentation/build/double-braces).
* **JSLT:** a declaração JSLT a ser executada.
* **Fail On Error:** se a opção estiver ativada, a execução do _pipeline_ com erro será interrompida. Do contrário, a execução do _pipeline_ será mantida, mas o resultado vai mostrar um valor falso para a propriedade “success”.

{% hint style="info" %}
**Importante:** o componente não suporta importação de declarações JSLT.
{% endhint %}

## Exemplos de expressões JSLT

### **Transposição de dados simples**

**Payload**

```
{
  "id" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "type" : "component",
  "prefix": "jslt",
  "myString": "test",
  "myArray": [ 1, 2, 3, 4],
  "boolean": true
}

```

**JSLT**

```
{
  "uuid": .id,
  "obj": {
   "key-1": .type,
   "key-2": .prefix
  },
  * - myString, myArray, id: .
}

```

**Saída**

```
{
  "uuid" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "obj" : {
    "key-1" : "component",
    "key-2" : "jslt"
  },
  "type" : "component",
  "prefix" : "jslt",
  "boolean" : true
}

```

### **Funções nativas JSLT**

{% hint style="info" %}
**Importante:** o exemplo abaixo representa algumas das funções nativas JSLT disponíveis. Para mais informações e a lista completa de funções, [visite a documentação do Github](https://github.com/schibsted/jslt/blob/master/functions.md).
{% endhint %}

**Payload**

```
{
  "id" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "type" : "component",
  "prefix": "jslt",
  "myString": "TEST",
  "myArray": [ 1, 2, 3, 4],
  "boolean": true
}

```

**JSLT**

```
{
  "uuid": split(.id, "-"),
  "obj": {
   "key-1": uppercase(.type),
   "key-2": join(.myArray, lowercase(.myString))
  },
  * : .
}

```

**Saída**

```
{
  "uuid" : [ "w23q7ca1", "8729", "24923", "922b", "1c0517ddffjf1" ],
  "obj" : {
    "key-1" : "COMPONENT",
    "key-2" : "1test2test3test4"
  },
  "id" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "type" : "component",
  "prefix" : "jslt",
  "myString" : "TEST",
  "myArray" : [ 1, 2, 3, 4 ],
  "boolean" : true
}

```

### **Variáveis e funções personalizadas**

**Payload**

```
{
  "id" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "s1": "jslt",
  "s2": "component"
}

```

**JSLT**

```
let splitted = split(.id, "-")
let size = size($splitted)

def concat(s1, s2)
  if ($s1 != null)
    $s1 + "___" + $s2
  else
    ""

{
  "variables": $splitted,
  "size": $size,
  "customFunction": concat(.s1, .s2)
}

```

**Saída**

{% code overflow="wrap" %}
```
{
  "variables": [
    "w23q7ca1",
    "8729",
    "24923",
    "922b",
    "1c0517ddffjf1"
  ],
  "size": 5,
  "customFunction": "jslt___component"
}

```
{% endcode %}

### **Operadores If e For**

**Payload**

```
{
  "id" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "status": true
}

```

**JSLT**

```
let aux = split(.id, "-")

def concat(string1, string2)
   $string1 + "-" + $string2

{
  "forResult": [for ($aux) concat("test", .)],
  "ifResult": if (.status)
                 size(.id)
              else
                 0
}

```

**Saída**

{% code overflow="wrap" %}
```
{
  "forResult" : [ "test-w23q7ca1", "test-8729", "test-24923", "test-922b", "test-1c0517ddffjf1" ],
  "ifResult" : 38
}

```
{% endcode %}
