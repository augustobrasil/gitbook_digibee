---
description: >-
  Saiba quais são as funções de utilidades associadas aos Double Braces e como
  utilizá-las.
---

# Funções de Utilidades

As funções foram criadas para:

* acelerar ainda mais a criação das suas integrações
* diminuir a complexidade dos seus _pipelines_
* simplificar conversões e transformações dos dados durante o fluxo dos seus _pipelines_

As funções de utilidades realizam operações diversas, que não se enquadram em nenhuma das outras categorias e estão disponíveis para componentes que suportam expressões com _Double Braces_. Para saber como passar informações para os componentes utilizando esse recurso, clique [aqui](./).

### BASEDECODE <a href="#basedecode" id="basedecode"></a>

Essa função em Double _Braces_ decodifica uma _string_ em um formato base64.

**Sintaxe**

BASEDECODE(value:string, \[charset:string - optional])

* **value:** _string_ a ser decodificada
* **charset:** _charset_ para a decodificação (padrão = UTF-8) (opcional)

Digamos que você precise decodificar uma _string_. Você pode fazer o seguinte:

```
{
"test": {{ BASEDECODE("eHB0bw==", "UTF-8") }}
}
```

O resultado esperado será:

```
{
"test": "xpto"
}
```

### BASEENCODE <a href="#baseencode" id="baseencode"></a>

Essa função em _Double Braces_ codifica uma _string_ em um formato base64.

**Sintaxe**

BASEENCODE(value:string, \[charset:string - optional])

* **value:** _string_ a ser codificada
* **charset:** _charset_ para a codificação (padrão = UTF-8) (opcional)

Digamos que você precise codificar uma _string_. Você pode fazer o seguinte:

```
{
"test": {{ BASEENCODE("xpto", "UTF-8") }}
}
```

O resultado esperado será:

```
{
"test": "eHB0bw=="
}
```

### _BASEURLDECODE_

Essa função em _Double Braces_ decodifica uma _string_ em um formato base64 no padrão de uso para URL.

**Sintaxe**

BASEDECODE(value:string, \[charset:string - optional])

* **value:** string a ser decodificada
* **charset:** charset para a decodificação (padrão = UTF-8) (opcional)

Digamos que você precise decodificar uma _string_. Você pode fazer o seguinte:

```
{
 "test": {{ BASEURLDECODE("eHB0bw", "UTF-8") }}
}

```

O resultado será:

```
{
 "test": "xpto"
}

```

### _BASEURLENCODE_&#x20;

Essa função em Double Braces codifica uma string em um formato base64 para uso em URL's.

**Sintaxe**

BASEENCODE(value:string, \[charset:string - optional])

* **value**: _string_ a ser codificada&#x20;
* **charset**: _charset_ para a codificação (padrão = UTF-8) (opcional)

Digamos que você precise codificar uma _string_. Você pode fazer o seguinte:

```
{
 "test": {{ BASEURLENCODE("xpto", "UTF-8") }}
}

```

O resultado será:

```
{
 "test": "eHB0bw"
}

```

### UUID <a href="#uuid" id="uuid"></a>

Essa função em _Double Braces_ gera um identificador único universal - o número de 128 bits é utilizado para identificar informações em sistemas.

**Sintaxe**

UUID()

Digamos que você precise gerar um identificador único. Você pode fazer o seguinte:

```
{
"test": {{ UUID() }}
}
```

O resultado esperado será:

```
{
"test": "4caad555-09b5-479c-98b4-ac72ffbb486c"
}
```

### TOBOOLEAN <a href="#h_8373c1f27d" id="h_8373c1f27d"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função permite que você converta um valor _string_ para booleano.

**Sintaxe**

TOBOOLEAN(valor)

Vamos supor que você precise converter os valores abaixo para booleano:

```
{
"string": "false",
"stringUpperCase": "TRUE",
"boolean": true,
"integer": 1,
"nullValue": null,
"object": {
"string": "abc"
}
}
```

Convertendo os valores:

```
{
"string": {{ TOBOOLEAN(message.string) }},
"stringUpperCase": {{ TOBOOLEAN(message.stringUpperCase) }},
"boolean": {{ TOBOOLEAN(message.boolean) }},
"integer": {{ TOBOOLEAN(message.integer) }},
"nullValue": {{ TOBOOLEAN(message.nullValue) }},
"object": {{ TOBOOLEAN(message.object) }}
}
```

O resultado será:

```
{
"string": false,
"stringUpperCase": true,
"boolean": true,
"integer": false,
"nullValue": false,
"object": false
}
```

Se a função for aplicada em _strings_ com valores diferentes de "true", "false", "TRUE" e "FALSE", campos numéricos, campos nulos, objetos e _arrays_, a função sempre retornará o resultado _false_.

### SIZE <a href="#h_3cd70ce23f" id="h_3cd70ce23f"></a>

Essa função em Double Braces permite que o tamanho de _strings_, _arrays_ e _objects_ seja obtido.

**Sintaxe**

SIZE(value, \[throwErrorOnUnexpectedType:boolean - optional])

* **value:** valor a ser verificado o tamanho
* **throwErrorOnUnexpectedType:** indica se será retornada uma exceção quando o parâmetro _value_ for de um tipo não esperado pela função. Caso não informado, será assumido valor _true_ e, quando informado valor _false_, o retorno da função será _null_.

Digamos que você precise obter o tamanho de um texto de uma propriedade _comments_ contida em seu _payload_. Você pode utilizar o seguinte trecho no componente _**JSON Generator**_:

```
{
"commentsSize": {{ SIZE(message.comments) }}
}
```

O resultado será um valor numérico que corresponde à quantidade de caracteres contida no texto:

```
{
"commentsSize": 1000
}
```

Agora digamos que exista um _JSON object_ na seguinte estrutura:

```
{
"body":{
"field1": "test",
"field2": {
"field2.1": "testing"
}
}
}
```

É preciso verificar o tamanho desse objeto. Utilizando o _**JSON Generator**_ novamente, veja a configuração do seguinte trecho:

```
{
"bodySize": {{ SIZE(message.body) }}
}
```

O resultado é a quantidade de propriedades contidas no objeto _body_:

```
{
"bodySize": 2
}
```

Nesse caso, a função considera apenas propriedades diretamente pertencentes ao objeto _body_ e não considera propriedades aninhadas.

Também é possível verificar o tamanho de um _array_:

```
{
"array": [
10,20,30
]
}
```

Assumindo que o _array_ acima, o _**JSON Generator**_ é utilizado mais uma vez para configurar o seguinte trecho:

```
{
"arraySize": {{ SIZE(message.array) }}
}
```

Ao executar a função, este é o resultado que representando a quantidade de elementos contidos no _array_:

```
{
"arraySize": 3
}
```

A função SIZE espera valores dos tipos _string_, _array_ e _object_. Quando algum valor que não seja desses tipos é passado, uma exceção é lançada. Porém, existe a opção de informar para a função não lançar exceção e simplesmente retornar _null_. Para isso, basta configurar o segundo parâmetro da função com o valor _false_.

Considere o seguinte _payload_:

```
{
"elements": 13
}
```

E a configuração do _**JSON Generator**_ conforme abaixo:

```
{
"elementsSize": {{ SIZE(message.elements, false) }}
}
```

Após a execução, o resultado será o seguinte:

```
{
"elementsSize": null
}
```

Dessa forma, não será lançada exceção e poderá ser adotada alguma lógica de verificação no seu fluxo de integração.

### URIDECODE

Essa função permite que você decodifique uma _URI_ (_string_).

**Sintaxe**

URIDECODE( uri:string, \[charset:string - optional ] )

* **uri**: _string_ a ser decodificada
* **charset**: _charset_ para decodificação ( padrão = UTF-8 ) ( opcional )

Digamos que você precise decodificar uma URI. Você pode fazer o seguinte:

```
{
 "test": {{ URIDECODE("http%3A%2F%2Flocalhost%3A8080", "UTF-8") }}
}

```

O resultado será:

```
{
 "test": "http://localhost:8080"
}

```

### URIENCODE

Essa função permite que você codifique uma URI (_string_).

**Sintaxe**

* **uri:** string a ser codificada
* **charset:** charset para codificação ( padrão = UTF-8 ) ( opcional )

Digamos que você precise codificar uma URI . Você pode fazer o seguinte:

```
{
 "test": {{ URIENCODE("http://localhost:8080", "UTF-8") }}
}
```

O resultado será:

```
{
 "test": "http%3A%2F%2Flocalhost%3A8080"
}
```

### Outras funções

Conheça também as funções:

* [de comparação](funcoes-de-comparacao.md)
* [numéricas](funcoes-numericas.md)
* [condicionais](funcoes-condicionais.md)
* [de data](funcoes-de-data.md)
* [de arquivo](funcoes-de-arquivo.md)
* [de JSON](funcoes-de-json.md)
* [matemáticas](funcoes-matematicas.md)
* [de _string_](funcoes-de-string.md)
