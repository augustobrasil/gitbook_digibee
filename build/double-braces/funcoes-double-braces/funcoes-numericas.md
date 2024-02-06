---
description: >-
  Saiba quais são as funções numéricas associadas aos Double Braces e como
  utilizá-las.
---

# Funções Numéricas

As funções foram criadas para:

* acelerar ainda mais a criação das suas integrações
* diminuir a complexidade dos seus _pipelines_
* simplificar conversões e transformações dos dados durante o fluxo dos seus _pipelines_

As funções numéricas realizam tratamentos de números e estão disponíveis para componentes que suportam expressões com _Double Braces_. Para saber como passar informações para os componentes utilizando esse recurso, clique [aqui](./).

### FORMATNUMBER <a href="#formatnumber" id="formatnumber"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função pode ser aplicada para converter um elemento do tipo _string_ para um formato numérico (incluindo a possibilidade de tratar o seu _locale_).

**Sintaxe**

FORMATNUMBER(valor, "formatDestination", "localeDest"?)

Os itens indicados com "?" podem ser definidos com valor _null_.

* **asInteger:** é opcional e do tipo BOOLEAN. Se "true", o resultado será do tipo _Integer_; do contrário, será considerado _BigDecimal_. O valor _default_ é "false".
* **localeDest:** o _locale_ representado deve ser considerado para a geração do número. Se o _localeDest_ não for definido, será considerado _en-us_.

**Valor de entrada:**

```
{
"numero": 123456.9123,
"negativo": -987.123
}
```

**Exemplos de conversões:**

```
{
"number-US":{{ FORMATNUMBER( message.numero, "###,###.###", "us-EN") }},

"number-BR":{{ FORMATNUMBER( message.numero, "###,###.###", "pt-BR") }},

"number-BR-1":{{ FORMATNUMBER( message.numero, "###,###.#", "pt-BR") }},

"number-positivo-BR-a": {{ FORMATNUMBER( message.numero, "'+'###,###.###;'-'###,###.###", "pt-BR") }},

"number-negative-BR": {{ FORMATNUMBER( message.negativo, "###,###.###'C';###,###.###'D'", "pt-BR") }},

"number-negative-BR-a": {{ FORMATNUMBER( message.negativo, "'+'###,###.###;'-'###,###.###", "pt-BR") }}
}
```

Outros exemplos de _**formatDestination**_:

| Pattern    |  Number    |  Formatted String |
| ---------- | ---------- | ----------------- |
| ###.###    | 123.456    | 123.456           |
| ###.#      | 123.456    | 123.5             |
| ###,###.## | 123456.789 | 123,456.79000.    |
| ###        | 9.95       | 009.95            |
| ##0.###    | 0.95       | 0.95              |

### TODOUBLE <a href="#todouble" id="todouble"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para retornar o valor _double_ de um número inteiro.

**Sintaxe**

TODOUBLE(num1)

```
{

“a”: 12

}

{

"doub": {{ TODOUBLE( message.a ) }}

}
```

O retorno dessa função será 12.0.

### TOINT <a href="#toint" id="toint"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para retornar o valor inteiro de um número _double_.

**Sintaxe**

TOINT(num1)

```
{

“a”: 12.345

}

{

"int": {{ TOINT( message.a ) }}

}
```

O retorno dessa função será 12.

### TOLONG <a href="#tolong" id="tolong"></a>

Utilizando _Double Braces_, você pode ter retornado de um número um valor no tipo LONG. É possível receber tanto uma _string_ como um número como parâmetro de entrada.

**Sintaxe**

TOLONG(num1)

```
{

“a”: 12.345

}

{

"long": {{ TOLONG( message.a ) }}

}
```

O retorno dessa função será 12.

### TONUMBER&#x20;

Essa função permite que você converta uma string para um valor numérico com base no seu formato de origem e _locale_.

**Sintaxe**&#x20;

TONUMBER(_string_, _formatSource_, _localeSource_?, _asInteger_?)

Os parâmetros indicados com "?" são opcionais.

* **string:** _string_ a ser convertida
* **formatSource:** formato de origem da _string_. Ex.: "###.###", "###.#", "###,###.##"
* **localeSource:** _locale_ da _string_, que se não for definido, será considerado "en-us"
* **asInteger:** valor _booleano_ que indica se a _string_ deve ser convertida para um número inteiro. Caso não seja definido, o valor padrão será _false_.

Digamos que você precise converter duas _strings_ referentes a um valor numérico genérico e um valor monetário:

```
{
	"generic": "150.33",
	"currency": "R$ 300.754,15"
}
```

Aplicando a conversão:

```
{
	"generic": {{ TONUMBER(message.generic, "###.##") }},
	"currency": {{ TONUMBER(message.currency, "'R$ '###,###.##", "pt-br") }}
}
```

O resultado será:

```
{
  	"generic": 150.33,
  	"currency": 300754.15
}
```

Outros exemplos de formatação:

| String    | Formato | Numérico |
| --------- | ------- | -------- |
| "123.456" |  ###.#  | 123.5    |
| "009.95"  | 000.### | 9.95     |
| "0.95"    | ##0.### | 0.95     |
| "-300"    | '-'###  | -300     |

### **RANDOMNUMBERS** <a href="#h_2c04156981" id="h_2c04156981"></a>

Essa função permite que você gere números inteiros randômicos com base em um intervalo de valores.

**Sintaxe**

RANDOMNUMBERS(_minValue_, _maxValue_)

Digamos que você precise gerar um número randômico dentro do intervalo de 0 a 50000.

Gerando o número:

```
{
"randomNumber": {{ RANDOMNUMBERS(0, 50000) }}
}
```

O resultado será:

```
{
"randomNumber": 37122
}
```

Os valores que definem o intervalo numérico são inclusivos.

{% hint style="info" %}
**IMPORTANTE:** a função tem limitação numérica e aceita apenas valores dentro do intervalo de -9223372036854775808 a 9223372036854775807. Qualquer valor fora desses limites acarretará em uma execução imprevisível da função.
{% endhint %}

### Outras funções

Conheça também as funções:

* [de comparação](funcoes-de-comparacao.md)
* [condicionais](funcoes-condicionais.md)
* [de data](funcoes-de-data.md)
* [de arquivo](funcoes-de-arquivo.md)
* [de JSON](funcoes-de-json.md)
* [matemáticas](funcoes-matematicas.md)
* [de _string_](funcoes-de-string.md)
* [de utilidades](double-braces-funcoes-de-utilidades.md)
