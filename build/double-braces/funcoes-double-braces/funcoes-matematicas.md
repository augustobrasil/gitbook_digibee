---
description: >-
  Saiba quais são as funções matemáticas associadas aos Double Braces e como
  utilizá-las.
---

# Funções Matemáticas

As funções foram criadas para:

* acelerar ainda mais a criação das suas integrações;
* diminuir a complexidade dos seus _pipelines;_
* simplificar conversões e transformações dos dados durante o fluxo dos seus _pipelines._

As funções matemáticas realizam operações matemáticas e estão disponíveis para componentes que suportam expressões com _Double Braces_. Para saber como passar informações para os componentes utilizando esse recurso, leia o artigo [Funções Double Braces](./).

### ABS <a href="#abs" id="abs"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para retornar o valor absoluto de um número.

**Sintaxe**

ABS(número)

Vamos supor que você precisa do valor absoluto do número exemplificado a seguir:

```
{

“a”: -34

}

{

“abs”: {{ ABS( message.a ) }}

}
```

O retorno dessa função será 34.0.

### CEIL <a href="#ceil" id="ceil"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para retornar o menor valor (mais próximo ao infinito negativo), maior ou igual ao valor argumento e igual a um número inteiro matemático.

**Sintaxe**

CEIL(número)

```
{

“a”: 12.885

}

{

"ceil": {{ CEIL( message.a ) }}

}
```

O retorno dessa função será 13.0.

### DIVIDE <a href="#divide" id="divide"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para dividir um número pelo outro.

**Sintaxe**

DIVIDE(numerador, denominador)

```
{

“a”: 10

}

{

"divide": {{ DIVIDE( message.a, 2 ) }}

}
```

O retorno dessa função será 5.0.

### LOG <a href="#log" id="log"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para dividir um número pelo outro.

**Sintaxe**

LOG(valor, base)

```
{

“a”: 8

}

{

"log": {{ LOG( message.a, 2 ) }}

}
```

O retorno dessa função será 3.0.

### MAX <a href="#max" id="max"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para declarar o maior valor entre dois números passados.

**Sintaxe**

MAX(num1, num2)

```
{

“a”: 8

}

{

"max": {{ MAX( message.a, 2 ) }}

}
```

O retorno dessa função será 8.0.

### MIN <a href="#min" id="min"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para declarar o menor valor entre dois números passados.

**Sintaxe**

MIN(num1, num2)

```
{

“a”: 8

}

{

"min": {{ MIN( message.a, 2 ) }}

}
```

O retorno dessa função será 2.0.

### MOD <a href="#mod" id="mod"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para retornar o resto da operação de divisão.

**Sintaxe**

MOD(numerador, denominador)

```
{

“a”: 8

}

{

"mod": {{ MOD( message.a, 2 ) }}

}
```

O retorno dessa função será 0.0.

### MULTIPLY <a href="#multiply" id="multiply"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para multiplicar n valores.

**Sintaxe**

MULTIPLY(num1, num2, ..., numN)

```
{

“a”: 8

}

{

"mult": {{ MULTIPLY( message.a, 2 ) }}

}
```

O retorno dessa função será 16.0.

### POW <a href="#pow" id="pow"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para trazer o exponencial.

**Sintaxe**

POW(num1, exp)

```
{

“a”: 2

}

{

"pow": {{ POW( message.a, 2 ) }}

}
```

O retorno dessa função será 4.0.

### ROUND <a href="#round" id="round"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para retornar o número mais próximo do argumento, com os laços arredondados para o infinito positivo.

**Sintaxe**

ROUND(num1)

```
{

“a”: 12.345

}

{

"round": {{ ROUND( message.a ) }}

}
```

O retorno dessa função será 12.0.

### SQRT <a href="#sqrt" id="sqrt"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para extrair a raiz quadrada do número.

**Sintaxe**

SQRT(num1)

```
{

“a”: 4

}

{

"sqrt": {{ SQRT( message.a ) }}

}
```

O retorno dessa função será 2.0.

### SUBTRACT <a href="#subtract" id="subtract"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para subtrair um número do outro.

**Sintaxe**

SUBTRACT(num1, num2)

```
{

“a”: 10

}

{

"sub": {{ SUBTRACT( message.a, 2 ) }}

}
```

O retorno dessa função será 8.0

### SUM <a href="#sum" id="sum"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para somar n valores.

**Sintaxe**

SUM(num1, num2, ..., numN)

```
{

“a”: 8

}

{

"sum": {{ SUM( message.a, 2 ) }}

}
```

O retorno dessa função será 10.0.

### Outras funções

Conheça também as funções:

* [de comparação](funcoes-de-comparacao.md)
* [numéricas](funcoes-numericas.md)
* [condicionais](funcoes-condicionais.md)
* [de data](funcoes-de-data.md)
* [de arquivo](funcoes-de-arquivo.md)
* [de JSON](funcoes-de-json.md)
* [de _string_](funcoes-de-string.md)
* [de utilidades](double-braces-funcoes-de-utilidades.md)
