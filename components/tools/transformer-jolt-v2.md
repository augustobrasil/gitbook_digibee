---
description: >-
  Descubra mais sobre o componente Transformer (JOLT) V2 e saiba como usá-lo na
  Digibee Integration Platform.
---

# Transformer (JOLT) V2

O **Transformer (JOLT)** permite a manipulação de um JSON através da tecnologia JOLT.

O componente é úti:

* Para modificar a estrutura de um JSON mantendo seus valores.
* Para adicionar, extrair e remover dados de um JSON.
* Para ordenar a estrutura de um JSON.
* Para modificar os valores contidos em um JSON através de funções, como manipular textos, realizar cálculos matemáticos, conversão entre tipos de dados, entre outros.
* Para acessar e manipular dados de _arrays_.

## **Parâmetros**

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="217">Parâmetro</th><th width="242">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Expression Reference</strong></td><td>Se a opção estiver ativada, o parâmetro <strong>JOLT Reference</strong> espera uma declaração de expressão JOLT através de uma referência <em>Double Braces</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>JOLT</strong></td><td>A expressão JOLT expression a ser executada.</td><td>N/A</td><td>JSON</td></tr><tr><td><strong>JOLT Reference</strong> <code>(DB)</code></td><td>A referência <em>Double Braces</em> para a expressão JOLT a ser executada. Este parâmetro fica disponível apenas se <strong>Expression Reference</strong> estiver ativado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do pipeline com erro será interrompida. Do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## **Uso recomendado para Expression Reference**

O parâmetro **Expression Reference** é recomendado apenas para cenários altamente dinâmicos, uma vez que a manter as operações JOLT separadamente do componente **Transformer (JOLT) V2** é muito complexo.

Estes cenários requerem alguns cuidados dependendo de como são implenentados, como: gerenciar as operações JOLT por meio do componente [**Object Store**](../structured-data/object-store.md), versionamento de transformações, definição de segregação e execução das transformações JOLT entre pipelines, entre outros.

Além disso, estes cenários também podem aumentar a necessidade de componentes [**Log**](log.md) no _pipeline_ devido à falta de visibilidade com cenários dinâmicos.

## **Operações JOLT**

### **Shift**

Utilizada para alterar a estrutura de um JSON, mantendo os valores contidos nesse mesmo JSON.

**Exemplo:**

**Entrada**

```
{  
    "body": {    
        "userName": "John"  
    }
}
```

**Transformação**

```
[
  {
    "operation": "shift",
    "spec": {
      "body": {
        "userName": "dados.nomeUsuario"
      }
    }
  }
]
```

**Saída**

```
{
  "dados" : {
    "nomeUsuario" : "John"
  }
}
```

### **Default**

Utilizada para adicionar novos campos ou objetos em um JSON, caso esses não existam previamente.

**Exemplo:**

**Entrada**

```
{
  "body": {
    "userName": "John"
  }
}
```

**Transformação**

```
[
  {
    "operation": "default",
    "spec": {
      "body": {
        "email": "default@email.com"
      }
    }
  }
```

**Saída**

```
{
  "body": {
    "userName": "John",
    "email": "default@email.com"
  }
}
```

### **Remove**

Utilizada para remover campos ou objetos de um JSON.

**Exemplo:**

**Entrada**

```
{
  "body": {
    "userName": "John",
    "email": "default@email.com"
  }
}
```

**Transformação**

```
[
  {
    "operation": "remove",
    "spec": {
      "body": {
        "email": ""
      }
    }
  }
]
```

**Saída**

```
{
  "body" : {
    "userName" : "John"
  }
}
```

### **Sort**

Utilizada para ordenar campos ou objetos de um JSON em ordem alfabética.

**Exemplo:**

**Entrada**

```
{
  "funcionario": {
    "telefone": "9 9999-9999",
    "nome": "Funcionario Sort",
    "dataNascimento": "01/01/1980",
    "cargo": "Analista"
  }
}
```

**Transformação**

```
[
  {
    "operation": "sort"
  }
]
```

**Saída**

```
{
  "funcionario" : {
    "cargo" : "Analista",
    "dataNascimento" : "01/01/1980",
    "nome" : "Funcionario Sort",
    "telefone" : "9 9999-9999"
  }
}
```

### **Cardinality**

Utilizada para transformar campos e objetos simples em _arrays_ e vice-versa.

**Exemplo:**

**Entrada**

```
{
  "produtos": {
    "nome": "Produto A",
    "id": "123-A",
    "valor": 10
  }
}
```

**Transformação**

```
[
  {
    "operation": "cardinality",
    "spec": {
      "produtos": "MANY"
    }
  }
]
```

**Saída**

```
{
  "produtos" : [ {
    "nome" : "Produto A",
    "id" : "123-A",
    "valor" : 10
  } ]
}
```

### **Modify-default-beta**

Utilizada para incluir valores e aplicar funções em um JSON.

**Exemplo:**

**Entrada**

```
{
  "produto": [
    {
      "nome": "Produto A",
      "preco": 10
    },
    {
      "nome": "Produto B",
      "preco": 20
    }
  ]
}
```

**Transformação**

```
[
  {
    "operation": "modify-default-beta",
    "spec": {
      "produto": {
        "*": {
          "fabricante": "Fabricante default"
        }
      }
    }
  }
]
```

**Saída**

```
{
  "produto" : [ {
    "nome" : "Produto A",
    "preco" : 10,
    "fabricante" : "Fabricante default"
  }, {
    "nome" : "Produto B",
    "preco" : 20,
    "fabricante" : "Fabricante default"
  } ]
}{
  "data": {
    "firstName": "John",
    "lastName": "Smith"
  }
}
```

### **Modify-overwrite-beta**

Utilizada para sobrescrever valores e aplicar funções em um JSON.

**Exemplo:**

**Entrada**

```
{
  "data": {
    "firstName": "John",
    "lastName": "Smith"
  }
}
```

**Transformação**

```
[
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "data": {
        "fullName": "=concat(@(1,firstName),' ',@(1,lastName))"
      }
    }
  }
]
```

**Saída**

```
{
  "data" : {
    "firstName" : "John",
    "lastName" : "Smith",
    "fullName" : "John Smith"
  }
}
```
