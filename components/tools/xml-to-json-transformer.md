---
description: >-
  Descubra mais sobre o componente XML to JSON Transformer e saiba como
  utilizá-lo na Digibee Integration Platform.
---

# XML to JSON Transformer

O **XML to JSON Transformer** transforma um XML _string_ em um objeto JSON.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>XML Field Path</strong></td><td>Caminho do campo que contém a <em>string</em> XML a ser transformada. A representação desse caminho deve ser feita utilizando notação com pontos. Caso o campo seja uma matriz, todos os seus elementos serão percorridos. Você pode especificar vários campos, separando-os por vírgula.</td><td>body</td><td><em>String</em></td></tr><tr><td><strong>Preserve Original</strong></td><td>Se a opção estiver ativada, os campos originais serão preservados no resultado da transformação e, para diferenciar do nome dos campos transformados, será adicionado o caractere <code>"_"</code> no início do nome dos campos originais.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>With Namespace</strong></td><td>Se a opção estiver ativada, os <em>namespaces</em> do XML serão mantidos no resultado da transformação.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Remove XML Attributes</strong></td><td>Se a opção estiver ativada, os atributos do XML serão omitidos do resultado da transformação.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>All Values As String</strong></td><td>Se a opção estiver ativada, todos os valores das <em>tags</em> do XML serão transformados para o tipo <em>string</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens <a href="#h_2b523ac67c" id="h_2b523ac67c"></a>

### Entrada <a href="#h_b1242ec6a1" id="h_b1242ec6a1"></a>

O componente não espera uma mensagem de entrada específica, apenas o preenchimento do parâmetro de configuração **XML Field Path** referenciando o caminho do campo a ser transformado. Esse campo deve existir na mensagem do passo anterior à execução do **XML to JSON Transformer**_._

### Saída <a href="#h_9af5c58cea" id="h_9af5c58cea"></a>

A estrutura será igual a da recebida do passo anterior do fluxo, porém os campos informados no parâmetro **XML Field Path** serão transformados em sua representação de objeto JSON. Em caso de erro, a propriedade "_error_" será criada no mesmo nível da propriedade original.

Quando o parâmetro **Preserve Original** estiver ativado, para cada campo informado no parâmetro **XML Field Path**_,_ será gerada uma nova propriedade apenas adicionando o caractere `"_"` no início de seu nome e contendo o XML _string_ original.

A notação com pontos de JSON vai procurar pelo elemento raiz que está sendo processado pelo _pipeline_ e realizar um cruzamento conforme as especificações passadas na propriedade **XML Field Path**.

**Exemplo:**

Em uma representação do **XML Field Path** contendo a.b.c.d, "a" será procurado no elemento raiz. Em seguida será o "b", depois o "c" e finalmente o "d". Se um _array_ for encontrado durante o cruzamento, então o algoritmo vai gerar um caminho de cruzamento para cada elemento no _array_. O algoritmo substitui todas as ocorrências do caminho definido em **XML Field Path**.

## XML to JSON Transformer em ação <a href="#h_8eecc69498" id="h_8eecc69498"></a>

Para todos os cenários abaixo, será considerado o seguinte _payload_ contendo campo XML _String_:&#x20;

```
{  
    "xmlField": "<?xml version=\"1.0\" ?><inf:ProductInformation xmlns:inf=\"urn:product:Info\" xmlns:stk=\"urn:product:Stock\"><inf:ProductName Code=\"C00001\">Computer</inf:ProductName><inf:Price Units=\"$\">2500</inf:Price><stk:Volume Units=\"Units\">200</stk:Volume></inf:ProductInformation>"
}
```

### Transformação de XML <a href="#h_04b9b7be13" id="h_04b9b7be13"></a>

#### **Entrada**

**Parâmetros**

* **XML Field Path:** xmlField
* **Preserve Original**: false
* **With Namespace**: false
* **Remove XML Attributes**: false
* **All Values As String**: false

#### **Saída**

```
{
  "xmlField": {
    "ProductInformation": {
      "ProductName": {
        "Code": "C00001",
        "content": "Computer"
      },
      "Price": {
        "Units": "$",
        "content": 2500
      },
      "Volume": {
        "Units": "Units",
        "content": 200
      },
      "xmlns:stk": "urn:product:Stock",
      "xmlns:inf": "urn:product:Info"
    }
  }
}
```

### Transformação de XML com parâmetro Preserve Original ativado <a href="#h_b00e976c0d" id="h_b00e976c0d"></a>

#### **Entrada**

**Parâmetros**

* **XML Field Path:** xmlField
* **Preserve Original**: true
* **With Namespace**: false
* **Remove XML Attributes**: false
* **All Values As String**: false

#### **Saída**

```
{
  "xmlField": {
    "ProductInformation": {
      "ProductName": {
        "Code": "C00001",
        "content": "Computer"
      },
      "Price": {
        "Units": "$",
        "content": 2500
      },
      "Volume": {
        "Units": "Units",
        "content": 200
      },
      "xmlns:stk": "urn:product:Stock",
      "xmlns:inf": "urn:product:Info"
    }
  },
  "_xmlField": "<?xml version=\"1.0\" ?><inf:ProductInformation xmlns:inf=\"urn:product:Info\" xmlns:stk=\"urn:product:Stock\"><inf:ProductName Code=\"C00001\">Computer</inf:ProductName><inf:Price Units=\"$\">2500</inf:Price><stk:Volume Units=\"Units\">200</stk:Volume></inf:ProductInformation>"
}

```

### Transformação de XML com parâmetro With Namespace ativado <a href="#h_77d05c7d86" id="h_77d05c7d86"></a>

#### **Entrada**

**Parâmetros**

* **XML Field Path:** xmlField
* **Preserve Original**: false
* **With Namespace**: true
* **Remove XML Attributes**: false
* **All Values As String**: false

#### **Saída**

```
{
  "xmlField": {
    "inf:ProductInformation": {
      "inf:Price": {
        "Units": "$",
        "content": 2500
      },
      "xmlns:stk": "urn:product:Stock",
      "xmlns:inf": "urn:product:Info",
      "inf:ProductName": {
        "Code": "C00001",
        "content": "Computer"
      },
      "stk:Volume": {
        "Units": "Units",
        "content": 200
      }
    }
  }
}
```

### Transformação de XML com parâmetro Remove XML Attributes ativado <a href="#h_5ccda188f2" id="h_5ccda188f2"></a>

#### **Entrada**

**Parâmetros**

* **XML Field Path:** xmlField
* **Preserve Original**: false
* **With Namespace**: false
* **Remove XML Attributes**: true
* **All Values As String**: false

#### **Saída**

```
{
  "xmlField": {
    "ProductInformation": {
      "ProductName": "Computer",
      "Price": 2500,
      "Volume": 200
    }
  }
}
```

### Transformação de XML com parâmetro All Values As String ativado <a href="#h_18c937c5db" id="h_18c937c5db"></a>

#### **Entrada**

**Parâmetros**

* **XML Field Path:** xmlField
* **Preserve Original**: false
* **With Namespace**: false
* **Remove XML Attributes**: true
* **All Values As String**: true

#### **Saída**

```
{
  "xmlField": {
    "ProductInformation": {
      "ProductName": "Computer",
      "Price": "2500",
      "Volume": "200"
    }
  }
}
```

\
