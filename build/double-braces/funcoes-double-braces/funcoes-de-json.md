---
description: >-
  Saiba quais são as funções de JSON associadas aos Double Braces e como
  utilizá-las.
---

# Funções de JSON

As funções foram criadas para:

* acelerar ainda mais a criação das suas integrações
* diminuir a complexidade dos seus _pipelines_
* simplificar conversões e transformações dos dados durante o fluxo dos seus _pipelines_

As funções de JSON realizam operações em objetos do tipo JSON e estão disponíveis para componentes que suportam expressões com _Double Braces_. Para saber como passar informações para os componentes utilizando esse recurso, clique [aqui](./).

## JSONPATH <a href="#jsonpath" id="jsonpath"></a>

Essa função em _Double Braces_ retorna partes de um determinado documento conforme a expressão enviada.

### **Sintaxe**

```
JSONPATH(value:string, expression:string)
```

● **value:** _string_

● **expression:** _string_ contendo a expressão a ser recuperada

Digamos que você precise obter parte de um documento utilizando expressões. Você pode fazer o seguinte:

```
{
"test": {{ JSONPATH ({"store":{"book":[{"category":"reference","author":"Nigel Rees","title":"Sayings of the Century","price":8.95},{"category":"fiction","author":"Evelyn Waugh","title":"Sword of Honour","price":12.99},{"category":"fiction","author":"Herman Melville","title":"Moby Dick","isbn":"0-553-21311-3","price":8.99},{"category":"fiction","author":"J. R. R. Tolkien","title":"The Lord of the Rings","isbn":"0-395-19395-8","price":22.99}],"bicycle":{"color":"red","price":19.95}},"expensive":10}, "$.store.book[?(@.price > 10)]") }}
"test2": {{ JSONPATH (["aa","ss","","e"],"$.[0]" ) }}
}
```

O resultado esperado será:

```
{
"test": [{"category":"fiction","author":"Evelyn Waugh","title":"Sword of Honour","price":12.99},{"category":"fiction","author":"J. R. R. Tolkien","title":"The Lord of the Rings","isbn":"0-395-19395-8","price":22.99}]
"test2": "aa"
}
```

É possível utilizar as próprias funções que o _**JSONPATH**_ provê internamente, tais como:

* min()
* max()
* avg()
* stddev()
* length

### **Exemplo:**

Suponha que um _array_ de entrada seja recebido:

```
{
"numbers": [1,33,56,77.8,66,10475,665464,1,0.01]
}
```

E que você queira utilizar as funções descritas acima no campo “expression”:

```
{
"min": {{ JSONPATH(message.numbers, "$.min()") }},
"max": {{ JSONPATH(message.numbers, "$.max()") }},
"avg": {{ JSONPATH(message.numbers, "$.avg()") }},
"stddev": {{ JSONPATH(message.numbers, "$.stddev()") }},
"length": {{ JSONPATH(message.numbers, "$.length()") }}
}
```

O resultado será:

```
{
"min": 0.01,
"max": 665464.0
"avg": 75130.42333333334,
"stddev": 208739.83034832493,
"length": 9
}
```

## TOJSON <a href="#tojson" id="tojson"></a>

Essa função em _Double Braces_ retorna o valor do JSON a partir do objeto recebido.

### **Sintaxe**

```
TOJSON(value:string)
```

● **value:** _string_

Digamos que você precise obter os valores em um objeto JSON. Você pode fazer o seguinte:

```
{
"test": {{ TOJSON("aaS2fdeS") }}
"test2": {{ TOJSON(111) }}
"test3": {{ TOJSON("false") }}
"test4": {{ TOJSON([{"c":123}]) }}
"test5": {{ TOJSON({"a":123,"array":[1,2,3]}) }}
"test6": {{ TOJSON("{\"name\":\"John\",\"age\":31,\"city\":\"New York\"}") }}
"test7": {{ TOJSON(null) }}
}
```

O resultado esperado será:

```
{
"test": "aaS2fdeS"
"test2": 111
"test3": false
"test4": [{"c":123}]
"test5": {"a":123,"array":[1,2,3]}
"test6": {"name":"John","age":31,"city":"New York"}
"test2": null
}
```

## UNESCAPEJSON <a href="#unescapejson" id="unescapejson"></a>

Essa função em _Double Braces_ retorna um JSON removendo os _escapes_ encontrados no valor fornecido.

### **Sintaxe**

```
UNESCAPE(value:string)
```

● **value:** _string_

Digamos que você precise remover caracteres de _escape_. Você pode fazer o seguinte:

```
{
"test": {{ UNESCAPE ("{\\\"name\\\":\\\"John\\\",\\\"age\\\":31,\\\"city\\\":\\\"New York\\\"}") }}
}
```

O resultado esperado será:

```
{
"test": "{\"name\":\"John\",\"age\":31,\"city\":\"New York\"}"
}
```

## GETELEMENTAT <a href="#h_66a3c0ca98" id="h_66a3c0ca98"></a>

Essa função permite que você capture um elemento específico de um _array_.

### **Sintaxe**

GETELEMENTAT(_array_, índice)

Vamos supor que você precise capturar o primeiro elemento do _array_ abaixo:

```
{
"data": [
{
"field": "value-1"
},
{
"field": "value-2"
},
{
"field": "value-3"
}
]
}
```

Capturando o elemento:

```
{
"element": {{ GETELEMENTAT(message.data, 0) }}
}
```

O resultado será:

```
{
"element": {
"field": "value-1"
}
}
```

Se a função receber um índice inexistente, o valor _**null**_ será retornado.

## LASTELEMENT <a href="#h_0931a48b4a" id="h_0931a48b4a"></a>

Essa função permite que você capture o último elemento de um _array_.

**Sintaxe**

```
LASTELEMENT(array)
```

Vamos supor que você precise capturar o último elemento do _array_ abaixo:

```
{
"data": [
{
"field": "value-1"
},
{
"field": "value-2"
},
{
"field": "value-3"
}
]
}
```

Capturando o elemento:

```
{
"element": {{ LASTELEMENT(message.data) }}
}
```

O resultado será:

```
{
"element": {
"field": "value-3"
}
}
```

Se a função receber um _array_ vazio, o valor _**null**_ será retornado.

## **REMOVEAT** <a href="#h_6994f76ca4" id="h_6994f76ca4"></a>

Essa função permite que você remova um elemento específico de um _array_.

### **Sintaxe**

```
REMOVEAT(array, index)
```

Vamos supor que você precise remover o segundo elemento do _array_ abaixo:

```
{
"data": [
{
"field": "value-1"
},
{
"field": "value-2"
},
{
"field": "value-3"
}
]
}
```

Removendo o elemento:

```
{
"data": {{ REMOVEAT(message.data, 1) }}
}
```

O resultado será:

```
{
"data": [
{
"field": "value-1"
},
{
"field": "value-3"
}
]
}
```

Se a função receber um índice inexistente, o _array_ original será retornado sem alterações.

## PUSH <a href="#h_f720a597c4" id="h_f720a597c4"></a>

Essa função permite que você insira um elemento no final de um _array._

### **Syntax**

```
PUSH(array, element)
```

Vamos supor que você precise inserir um novo elemento no _array_ abaixo:

```
{
"element": {
"example": "123"
},
"array": [
{
"example": "ABC"
},
{
"example": "FFF"
}
]
}
```

Inserindo o novo elemento:

```
{
"array": {{ PUSH(message.array, message.element) }}
}
```

O resultado será:

```
{
"array": [
{
"example": "ABC"
},
{
"example": "FFF"
},
{
"example": "123"
}
]
}
```

Se a função receber um elemento inexistente ou nulo, o valor _null_ será inserido no final do array

## POP <a href="#h_aa365201c7" id="h_aa365201c7"></a>

Essa função permite que você remova o último elemento de um _array_, retornando o elemento removido e o _array_ remanescente.

### **Syntax**

```
POP(array)
```

Vamos supor que você precise remover o último elemento do _array_ abaixo:

```
{
"array": [
{
"id": "ABC"
},
{
"id": "FFF"
},
{
"id": "123"
}
]
}
```

Removendo o último elemento:

```
{
"data": {{ POP(message.array) }}
}
```

O resultado será:

```
{
"data": {
"array": [
{
"id": "ABC"
},
{
"id": "FFF"
}
],
"element": {
"id": "123"
}
}
}
```

Se a função receber um _array_ vazio, o mesmo _array_ vazio será retornado.

## **NEWEMPTYOBJECT**

Essa função permite que você crie um novo objeto vazio.

### **Sintaxe**

```
NEWEMPTYOBJECT()
```

Vamos supor que você precise criar um novo objeto vazio:

```
{
"data": { }
}
```

Criando:

```
{
"data": {{ NEWEMPTYOBJECT() }}
}
```

O resultado será:

```
{
"data": { }
}
```

## NEWEMPTYARRAY <a href="#h_09f3fbefe8" id="h_09f3fbefe8"></a>

Essa função permite que você crie um novo _array_ vazio.

**Sintaxe**

```
NEWEMPTYARRAY()
```

Digamos que você precise criar um novo _array_ vazio:

```
{
"data": []
}
```

Criando:

```
{
"data": {{ NEWEMPTYARRAY() }}
}
```

O resultado será:

```
{
"data": []
}
```

## **CARDINALITYONE**

Essa função possibilita aplicar uma cardinalidade de _n:1_ na estrutura informada, onde independente da quantidade de elementos na entrada, a saída será sempre 1 elemento.

### **Sintaxe**

```
CARDINALITYONE(data)
```

Digamos que você precise aplicar a cardinalidade _n:1_ em cada elemento do JSON abaixo:

```

"arrayObject": [
{
"id": "PROD-123",
"type": "Product"
},
{
"id": "CUST-456",
"type": "Customer"
}
],
"arrayNumber": [ 23, 790 ],
"emptyArray": [],
"object": {
"test": "value"
},
"singleNumber": 500,
"singleString": "CARDINALITY",
"nullValue": null,
"emptyObject": {}
}
```

Aplicando a função:

```
{
"arrayObject": {{ CARDINALITYONE(message.arrayObject) }},
"arrayNumber": {{ CARDINALITYONE(message.arrayNumber) }},
"emptyArray": {{ CARDINALITYONE(message.emptyArray) }},
"object": {{ CARDINALITYONE(message.object) }},
"singleNumber": {{ CARDINALITYONE(message.singleNumber) }},
"singleNumber": {{ CARDINALITYONE(message.singleNumber) }},
"singleString": {{ CARDINALITYONE(message.singleString) }},
"emptyObject": {{ CARDINALITYONE(message.emptyObject) }}
}
```

O resultado será:

```
{
"arrayObject": {
"id": "PROD-123",
"type": "Product"
},
"arrayNumber": 23,
"emptyArray": null,
"object": {
"test": "value"
},
"singleNumber": 500,
"singleString": "CARDINALITY",
"emptyObject": {}
}
```

## **CARDINALITYMANY**

Essa função possibilita normalizar a saída em cardinalidade múltipla. Ou seja, caso a entrada seja um _array_ com _n_ elementos, a saída será um _array_ com _n_ elementos e caso a entrada seja uma único objeto, a saída será um _array_ contendo este único objeto.

### **Sintaxe**

```
CARDINALITYMANY(data)
```

Digamos que você precise aplicar a cardinalidade _m:n_ em cada elemento do JSON abaixo:

```
{
"arrayObject": [
{
"id": "PROD-123",
"type": "Product"
},
{
"id": "CUST-456",
"type": "Customer"
}
],
"arrayNumber": [ 23, 790 ],
"emptyArray": [],
"object": {
"test": "value"
},
"singleNumber": 500,
"singleString": "CARDINALITY",
"nullValue": null,
"emptyObject": {}
}
```

Aplicando a função:

```
{
"arrayObject": {{ CARDINALITYMANY(message.arrayObject) }},
"arrayNumber": {{ CARDINALITYMANY(message.arrayNumber) }},
"emptyArray": {{ CARDINALITYMANY(message.emptyArray) }},
"object": {{ CARDINALITYMANY(message.object) }},
"singleNumber": {{ CARDINALITYMANY(message.singleNumber) }},
"singleNumber": {{ CARDINALITYMANY(message.singleNumber) }},
"singleString": {{ CARDINALITYMANY(message.singleString) }},
"emptyObject": {{ CARDINALITYMANY(message.emptyObject) }}
}
```

O resultado será:

```
{
"arrayObject": [
{
"id": "PROD-123",
"type": "Product"
},
{
"id": "CUST-456",
"type": "Customer"
}
],
"arrayNumber": [ 23, 790 ],
"emptyArray": [],
"object": [ {
"test": "value"
} ],
"singleNumber": [ 500 ],
"singleString": [ "CARDINALITY" ],
"emptyObject": [ {} ]
}
```

Conheça também as funções:

* [de comparação](funcoes-de-comparacao.md)
* [numéricas](funcoes-numericas.md)
* [condicionais](funcoes-condicionais.md)
* [de data](funcoes-de-data.md)
* [de arquivo](funcoes-de-arquivo.md)
* [matemáticas](funcoes-matematicas.md)
* [de _string_](funcoes-de-string.md)
* [de utilidades](double-braces-funcoes-de-utilidades.md)
