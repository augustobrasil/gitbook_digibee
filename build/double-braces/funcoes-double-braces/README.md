---
description: Saiba quais são as funções Double Braces e como utilizá-las
---

# Funções Double Braces

Você pode usar funções Double Braces para manipular dados em um _pipeline_.

## Sintaxe

As funções Double Braces são usadas entre dois conjuntos de chaves e um espaço em branco, com o nome da função seguido por uma lista de parâmetros entre parênteses, como abaixo:

```
{{ NOMEDAFUNÇÃO(param1, param2) }}
```

Funções Double Braces são _case-insensitive_, isto é, não diferenciam entre letras maiúsculas e minúsculas. Entretanto, nós recomendamos como uma melhor prática escrevê-las com letras maiúsculas.

## Funções aninhadas

Você pode fazer chamadas a funções Double Braces dentro de outras funções, como abaixo:

```
{{ FUNÇÃOEXTERNA(FUNÇÃOINTERNA(param1, param2), param3) }}
```

Quando usa essa sintaxe, as funções são executadas de dentro para fora. Isto é, no exemplo acima, `FUNÇÃOINTERNA` é executada primeiro e seu _output_ é usado como um parâmetro de `FUNÇÃOEXTERNA`, que é executada por último.

Diferentemente das linguagens de programação, as expessões Double Braces executam todas as funções ao mesmo tempo, independentemente se a condição do IF é `true` ou `false`. Isso difere das linguagens de programação, que normalmente executam as funções somente após checar a condição do IF.

#### Exemplo

**Input**

```
{
    "date": "2022-10-26T03:00:00Z"
}
```

**Expressão Double Braces**

```
{
    "format": {{ IF(EQUALTO(SIZE(message.date),20),FORMATDATE( message.date, "yyyy-MM-dd'T'HH:mm:ss'Z'", "dd/MM/yyyy"),FORMATDATE( message.date, "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'", "dd/MM/yyyy")) }}
}
```

**Output**

```
{
  "success": false,
  "message": "Encountered a configuration error while generating JSON",
  "error": "com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: com.digibee.doublebraces.service.DoubleBracesConfigurationException: Syntax error parsing double braces expression {{ IF(EQUALTO(SIZE(message.date),20),FORMATDATE( message.date, \"yyyy-MM-dd'T'HH:mm:ss'Z'\", \"dd/MM/yyyy\"),FORMATDATE( message.date, \"yyyy-MM-dd'T'HH:mm:ss.SSS'Z'\", \"dd/MM/yyyy\")) }}: Could not parse date/time evaluating function FORMATDATE. Error: Text '2022-10-26T03:00:00Z' could not be parsed at index 19"
}
```

## Lista de funções

Abaixo, listamos as funções Double Braces por grupos baseados em seu uso.

### DE COMPARAÇÃO <a href="#de-comparao" id="de-comparao"></a>

Usadas para comparar _inputs_ booleanos. Para saber mais, leia o artigo [Funções de Comparação](funcoes-de-comparacao.md):

* AND
* NOT
* OR
* XOR

### NUMÉRICAS <a href="#numricas" id="numricas"></a>

Usadas para manipular valores numéricos. Para saber mais, leia o artigo [Funções Numéricas](funcoes-numericas.md):

* FORMATNUMBER
* TODOUBLE
* TOINT
* TOLONG

### CONDICIONAIS <a href="#condicionais" id="condicionais"></a>

As funções desse grupo retornam um valor de acordo com um critério específico. Para saber mais, leia o artigo [Funções Condicionais](funcoes-condicionais.md):

* EQUALTO
* GREATERTHAN
* GREATERTHANEQUAL
* IF
* LESSTHAN
* LESSTHANEQUAL
* ISOBJECT
* ISARRAY
* ISBOOLEAN
* ISSTRING
* ISNUMBER
* ISNULL
* SWITCHCASE

### DE DATA <a href="#de-data" id="de-data"></a>

Usadas para manipular datas. Para saber mais, leia o artigo [Funções de Data](funcoes-de-data.md):

* FORMATDATE
* NOW
* SUMDATE
* TOISODATE
* DIFFDATE

### DE ARQUIVO <a href="#de-arquivo" id="de-arquivo"></a>

Usadas para consultar metadados e validar arquivos. Para saber mais, leia o artigo [Funções de Arquivo](funcoes-de-arquivo.md):&#x20;

* FILEEXISTS
* FILESIZE

### DE JSON <a href="#de-json" id="de-json"></a>

Usadas para manipular objetos JSON. Para saber mais, leia o artigo [Funções de JSON](funcoes-de-json.md):

* JSONPATH
* TOJSON
* UNESCAPEJSON
* GETELEMENTAT
* LASTELEMENT
* REMOVEAT
* ARRAYTOOBJECT
* OBJECTTOARRAY
* NEWEMPTYOBJECT
* NEWEMPTYARRAY

### MATEMÁTICAS <a href="#matemticas" id="matemticas"></a>

Usadas para fazer operações matemáticas. Para saber mais, leia o artigo [Funções Matemáticas](funcoes-matematicas.md):

* ABS
* CEIL
* DIVIDE
* LOG
* MAX
* MIN
* MOD
* MULTIPLY
* POW
* ROUND
* SQRT
* SUBTRACT
* SUM

### DE STRING <a href="#de-string" id="de-string"></a>

Usadas para manipular _strings_. Para saber mais, leia o artigo [Funções de String](funcoes-de-string.md):

* CAPITALIZE
* CONCAT
* ESCAPE
* INDEXOF
* JOIN
* LASTINDEXOF
* LEFTPAD
* LOWERCASE
* MATCHES
* NORMALIZE
* REPLACE
* RIGHTPAD
* SPLIT
* SUBSTRING
* TOSTRING
* UPPERCASE
* CONTAINS

### DE UTILIDADE <a href="#de-utilidades" id="de-utilidades"></a>

Usadas para fazer operações que não se encaixam nas outras categorias. Para saber mais, leia o artigo [Funções de Utilidade](double-braces-funcoes-de-utilidades.md):&#x20;

* BASEDECODE
* BASEENCODE
* UUID
* TOBOOLEAN
* SIZE
