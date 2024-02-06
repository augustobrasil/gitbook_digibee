---
description: >-
  Descubra mais sobre o componente JSON to XML Transformer e como usá-lo na
  Digibee Integration Platform.
---

# JSON to XML Transformer

&#x20;componente **JSON to XML Transformer** gera um XML baseado em um JSON recebido na sua mensagem de entrada.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="280">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>JSON Field Path</strong></td><td>JSON como caminho do campo <em>string</em> em notação com pontos (<em>dotted notation</em>).</td><td><em>payload</em></td><td><em>String</em></td></tr><tr><td><strong>Root Element Name</strong></td><td>Elemento raiz do XML gerado.</td><td><em>body</em></td><td><em>String</em></td></tr><tr><td><strong>Preserve Original</strong></td><td>Se ativada, a opção preserva os campos originais.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Header</strong></td><td>XML <em>header</em> a ser incluído antes do XML <em>payload</em>.</td><td>&#x3C;?xml version='1.0' encoding='UTF-8' standalone='no' ?></td><td><em>String</em></td></tr></tbody></table>

## Fluxo de mensagens

### Entrada

O componente espera uma mensagem em qualquer formato, mas vai procurar procurar por um caminho dentro da propriedade de configuração **JSON Field Path**.

Alguns exemplos válidos de entrada:

#### Exemplo 1

```
{
    "orders": {
     "order": [
       {
         "a": 1,
 "b": 1
       },
       {
         "a": 2,
         "b": 2
       },
       {
         "a": 3,
         "b": 3
       }
   ]
   }
 }
```

#### Exemplo 2

```
{
 "payload": {
   "test": {
     "a": 1,
     "b": 1
   }
 }
}
```

### Saída

A estrutura será igual a de entrada, porém com outra propriedade de JSON _string_ e a sua representação de objeto JSON. Em caso de erro, a propriedade "error" será criada no mesmo nível da propriedade original.

A notação com pontos (_dotted notation_) de JSON vai procurar pelo elemento raiz que está sendo processado pelo _pipeline_ e realizar um cruzamento de acordo com as especificações passadas na propriedade **JSON Field Path**.

#### Exemplo

Em uma representação do **JSON Field Path** contendo a.b.c.d, "a" será procurado no elemento raiz. Em seguida será o "b", depois o "c" e finalmente o "d". Se um _array_ for encontrado durante o cruzamento, então o algoritmo vai gerar um caminho de cruzamento para cada elemento no _array_. O algoritmo substitui todas as ocorrências do caminho definido em **JSON Field Path**.

**Sem erro**

```
{
"XPTO": "TEMPLATE TRANSFORMADO"
"_body": {}
}
```

* **\_body:** se a opção **Preserve Original** estiver habilitada, a propriedade será exibida na saída contendo o JSON de entrada.
* **XPTO:** nome dinâmico baseado na configuração do **JSON Field Path** nas propriedades do componente.

**Com erro**

```
{
 "body": null,
 "_error": "Can not construct instance of java.util.LinkedHashMap: no String-argument constructor/factory method to deserialize from String value ('')\n at [Source: N/A; line: -1, column: -1]",
 "_body": ""
}
```

* **\_body:** se a opção **Preserve Original** estiver habilitada, a propriedade será exibida na saída contendo o JSON de entrada.
* **\_error:** descrição do erro que ocorreu na execução.
* **XPTO:** nome dinâmico baseado na configuração do **JSON Field Path** nas propriedades do componente.

## JSON to XML Transformer em ação

### Exemplo 1

* **JSON Field Path:** orders
* **Root Element Name:** doc
* **Preserve Original:** habilitado
* **Header:** \<?xml version='1.0' encoding='UTF-8' standalone='no' ?>

#### Entrada

```
{
    "orders": {
     "order": [
       {
         "a": 1,
         "b": 1
       },
       {
         "a": 2,
         "b": 2
       },
       {
         "a": 3,
         "b": 3
       }
     ]
   }
}
```

#### Saída

```
{
 "orders": "<?xml version='1.0' encoding='UTF-8' standalone='no' ?><doc><order><a>1</a><b>1</b></order><order><a>2</a><b>2</b></order><order><a>3</a><b>3</b></order></doc>",
 "_orders": {
   "order": [
     {
       "a": 1,
       "b": 1
     },
     {
       "a": 2,
       "b": 2
     },
     {
       "a": 3,
       "b": 3
    }
   ]
 }
}
```

### Exemplo 2

* **JSON Field Path:** payload
* **Root Element Name:** xpto
* **Preserve Original:** desabilitado

#### Entrada

```
{
 "payload": {
   "test": {
     "a": 1,
     "b": 1
   }
 }
}
```

#### Saída

```
{ 
   "payload": "<xpto><test><a>1</a><b>1</b></test></xpto>"
}
```
