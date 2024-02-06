---
description: >-
  Descubra mais sobre as transformações com JOLT e saiba como aplicá-las na
  Digibee Integration Platform.
---

# Transformer - Conhecendo o JOLT

As aplicações de **Transformer (JOLT)** permite transformações de JSON através do JOLT.

Para desenvolvimento e teste de todos os exemplos contidos neste artigo, [acesse o JOLT playground](https://jolt-demo.appspot.com/#inception).

## **JOLT** - **JS**ON  <a href="#jolt---json-language-for-transform" id="jolt---json-language-for-transform"></a>

JSON é o formato usado por JOLT em suas transformações.\
Sua utilização é baseada na estrutura abaixo, sempre dependente de uma entrada:

```
[ 
  { 
    "operation": "", 
    "spec": { 
        
    } 
  } 
] 
```

Onde:

* **"operations":** define o tipo da transformação que será aplicada.
* **"spec":** área para aplicação da transformação.
* **"\[ ]"**: a própria estrutura base do JOLT também é um JSON, e com isso temos um _array_ que nos permite encadear diversas _operations_.

## **Operations** <a href="#operations" id="operations"></a>

Existem diversos tipo de _operations_ no JOLT.\


* **shift**
* **default**
* **remove**
* **sort**
* **cardinality**
* **modify-default-beta**
* **modify-overwrite-beta**

Cada _operation_ tem sua peculiaridade e fará a transformação de maneira diferente.\
Entretanto, todas elas seguem o mesmo princípio para as transformações, que é a **navegação** na estrutura do JSON de entrada.\
Abaixo veremos com mais detalhes como isso ocorre.

### **shift** <a href="#shift" id="shift"></a>

Usado para alterar a estrutura de um JSON, mantendo os valores contidos neste mesmoarquivo JSON.\
\
Sua utilização consiste em navegar na estrutura do JSON até o **campo** ou **objeto** que desejamos pegar seu valor e em seguida informar onde esse valor deve ser colocado no novo JSON que queremos.

Vejamos o exemplo abaixo:

Temos um JSON de entrada contendo informações de Cliente:

```
{
  "cliente": {
    "nome": "Cliente Exemplo",
    "email": "cliente-exemplo@email.com",
    "cpf": "123.456.789.10",
    "dataNascimento": "15/02/1985",
    "endereco": "Rua do Cliente Exemplo, 123",
    "pais": "Brasil",
    "telefone": "8888-8888"
  }
}
```

E queremos um novo JSON com a seguinte estrutura:

```
{
  "customer" : {
    "name" : "Cliente Exemplo",
    "birthDate" : "15/02/1985",
    "address" : {
      "street" : "Rua do Cliente Exemplo, 123",
      "country" : "Brasil"
    },
    "phoneNumber" : "8888-8888",
    "mobileNumber" : "8888-8888"
  }
}
```

Nossa transformação ficará:

```
[ 
  { 
    "operation": "shift", 
    "spec": { 
      "cliente": { 
        "nome": "customer.name", 
        "dataNascimento": "customer.birthDate", 
        "endereco": "customer.address.street", 
        "pais": "customer.address.country",
        "telefone": ["customer.phoneNumber", "customer.mobileNumber"] 
      } 
    } 
  } 
] 
```

O que fizemos acima foi **navegar** até os **campos** de nosso interesse e informar onde os **valores** de cada um desses campos devem ser inseridos.

Através da notação **"." (ponto)**, conseguimos definir níveis no novo JSON que queremos criar.\
Com isso, em `"nome":"customer.name"` pegamos o valor do campo **nome** e jogamos para o campo _**name**_ dentro do objeto _**customer**_, e em `"endereco":"customer.address.street"` pegamos o valor do campo **endereco** e jogamos para o campo _**street**_ dentro do objeto _**address**_ que também estará contido no objeto _**customer**_.

{% hint style="info" %}
Podemos pegar um mesmo valor de um campo e jogá-lo para mais de 1 campo ao mesmo tempo.&#x20;
{% endhint %}

Em `"telefone": ["customer.phoneNumber", "customer.mobileNumber"]`, pegamos o valor do campo **telefone** e jogamos para _**phoneNumber**_ e _**mobileNumber**_, ambos dentro de _**customer**_. Essa abordagem nos permite transpor um único valor para _**n**_ novos campos.

{% hint style="warning" %}
Nesta _operation_, apenas os campos manipulados na transformação serão considerados, então qualquer dado no JSON de entrada que não for utilizado será descartado.
{% endhint %}

JSON final:

```
{
  "customer" : {
    "name" : "Cliente Exemplo",
    "birthDate" : "15/02/1985",
    "address" : {
      "street" : "Rua do Cliente Exemplo, 123",
      "country" : "Brasil"
    },
    "phoneNumber" : "8888-8888",
    "mobileNumber" : "8888-8888"
  }
}
```

### **default**

Usado para adicionar novos campos ou objetos em um JSON, caso esses não existam previamente.\
\
Sua utilização consiste em navegar na estrutura do JSON até o nível desejado e inserir o campo ou objeto com seu respectivo valor.

{% hint style="warning" %}
Caso o campo declarado na transformação já exista no JSON de entrada, a transformação não terá efeito.
{% endhint %}

Vejamos o exemplo abaixo:

Temos um JSON de entrada contendo informações de Cliente:

```
{
  "cliente": {
    "nome": "Cliente Default",
    "cpf": "123.456.789.10"
  }
}
```

Entretanto, precisamos de um JSON que além das informações de nome e cpf também contenha a data de nascimento do cliente.

```
{
  "cliente" : {
    "nome" : "Cliente Default",
    "cpf" : "123.456.789.10",
    "dataNascimento" : "01/01/1970"
  }
}

```

Nossa transformação ficará:

```
[
  {
    "operation": "default",
    "spec": {
      "cliente": {
        "dataNascimento": "01/01/1970"
      }
    }
  }
]
```

Acima nós navegamos até o objeto **cliente** e adicionamos o campo **dataNascimento** com um valor padrão.

### **remove**

Usado para remover campos ou objetos de um JSON.\
\
Sua utilização consiste em navegar na estrutura do JSON até o nível desejado e informar o campo a ser removido.

Vejamos o exemplo abaixo:

Temos um JSON de entrada contendo informações de Cliente:

```
{
  "cliente" : {
    "nome" : "Cliente Default",
    "cpf" : "123.456.789.10",
    "dataNascimento" : "01/01/1970"
  }
}
```

Entretanto, precisamos de um JSON que contenha apenas as informações de nome e cpf do cliente:

```
{
  "cliente" : {
    "nome" : "Cliente Default",
    "cpf" : "123.456.789.10"
  }
}
```

Nossa transformação ficará:

```
[
  {
    "operation": "remove",
    "spec": {
      "cliente": {
        "dataNascimento": ""
      }
    }
  }
]
```

O que fizemos acima foi apenas navegar até o campo **dataNascimento** e atribuí-lo para **" " (aspas vazias)**.

O campo a ser removido deve ser **sempre** atribuído à uma _String_ vazia(""), caso contrário teremos uma quebra na transformação e a mesma não ocorrerá.

### **sort**

Usado para ordenar campos ou objetos de um JSON em ordem alfabética.

{% hint style="warning" %}
A ordenação dos campos ou objetos não pode ser configurada, portanto todo JSON será afetado. Apenas os nomes dos **campos** recebem a ordenação e não seus valores.
{% endhint %}

Vejamos o exemplo abaixo:

Temos um JSON de entrada contendo informações de Funcionários:

```
{
  "funcionario": {
    "telefone": "9 9999-9999",
    "nome": "Cliente Sort",
    "dataNascimento": "01/01/1980",
    "cargo": "Analista JOLT"
  }
}
```

Precisamos que todos os campos contidos no JSON sejam ordenados em ordem alfabética:

```
{

  "funcionario" : {
    "cargo" : "Analista JOLT",
    "dataNascimento" : "01/01/1980",
    "nome" : "Cliente Sort",
    "telefone" : "9 9999-9999"
  }
}
```

Para a _operation sort_, não precisamos definir o objeto _**spec**_ que sempre usamos junto do campo _**operation**_.

Nossa transformação será apenas:

```
[
  {
    "operation": "sort"
  }
]
```

### **cardinality**

Usado para transformarmos campos e objetos simples em objetos listas e vice-versa.

{% hint style="warning" %}
Quando transformamos um objeto lista para um campo ou objeto simples, apenas o primeiro item da lista será considerado.
{% endhint %}

Vejamos o exemplo abaixo:

Temos um JSON de entrada contendo informações de Produtos:

```
{
  "produtos": {
    "nome": "Produto A",
    "id": "123-A",
    "valor": 10
  }
}
```

Precisamos transformar o **objeto** "produtos" em uma **lista**:

```
{
  "produtos" : [ {
    "nome" : "Produto A",
    "id" : "123-A",
    "valor" : 10
  } ]
}
```

Nossa transformação será:

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

Já no caso de termos uma lista de produtos:

```
{
  "produtos": [
    {
      "nome": "Produto A",
      "id": "123-A",
      "valor": 10
    },
    {
      "nome": "Produto B",
      "id": "456-B",
      "valor": 20
    }
  ]
}
```

E precisarmos transformar essa **lista** em um **objeto simples**:

```
{
  "produtos" : {
    "nome" : "Produto A",
    "id" : "123-A",
    "valor" : 10
  }
}
```

Nossa transformação ficará:

```
[
  {
    "operation": "cardinality",
    "spec": {
      "produtos": "ONE"
    }
  }
]
```

## **Aprofundando o conhecimento** <a href="#aprofundando-o-conhecimento" id="aprofundando-o-conhecimento"></a>

Até aqui vimos conceitos essenciais para o entendimento e utilização do JOLT, porém antes de conhecermos as _operations_ restantes, precisamos conhecer alguns conceitos mais elaborados.

Ainda como pré-requisito para avançarmos, veremos 2 termos que são utilizados para melhor entendimento sobre JOLT.

São eles:

* **LHS (**_**Left Hand Side**_**)**\
  Usado para referenciar o lado esquerdo da transformação.
* **RHS (**_**Right Hand Side**_**)**\
  Usado para referenciar o lado direito da transformação.

Ou seja, todo conteúdo do JSON que estiver **antes** dos **: (dois pontos)**, será nosso **LHS** e o que estiver **após** os **: (dois pontos)**, será nosso **RHS**.

Transformação exemplo:

```
[
  {
     "operation": "shift",
     "spec": {
LHS ->  "cliente": {
  LHS ->  "nome": "customer.name",  <- RHS
  LHS ->  "dataNascimento": "customer.birthDate",  <- RHS
  LHS ->  "endereco": "customer.address.street",  <- RHS
  LHS ->  "pais": "customer.address.country"  <- RHS
      }
    }
  }
]
```

Visto isso, agora podemos avançar.

O grande poder do JOLT está na possibilidade de lidarmos com as transformações de maneira **dinâmica**. Para isso, utilizamos **curingas** (_wildcards_), que são caracteres específicos alocados de diversas maneiras em nossas transformações, cada um com uma função diferente.

Um mesmo curinga pode ter funções diferentes dependendo de sua aplicação **(LHS** e **RHS)**, e, além disso, podemos combinar diferentes curingas em uma mesma transformação.

Abaixo veremos suas definições e alguns exemplos de aplicações.

### **&** <a href="#h_6c3778d162" id="h_6c3778d162"></a>

Usa o conteúdo do que está declarado no **LHS** para compor a estrutura do JSON de saída, sem a necessidade de explicitar este conteúdo na transformação.

Este curinga usa como base a **navegação** feita durante a transformação.

Uso: **RHS**\
_Operations_: _shift_

Exemplo:

Temos um JSON contendo dados de Cliente:

```
{
  "nome": "Cliente Exemplo",
  "email": "cliente-exemplo@email.com"
}
```

E precisamos desses dados em um objeto de nome "cliente" :

```
{
  "cliente": {
    "nome": "Cliente Exemplo",
    "email": "cliente-exemplo@email.com"
  }
}
```

Nossa transformação ficará:

```
[
  {
    "operation": "shift",
    "spec": {
      "nome": "cliente.&",
      "email": "cliente.&"
    }
  } 
]
```

Em **&**, pegamos os valores dos campos "**nome**" e "**email**", e atribuímos para outros campos chamados "**nome**" e "**email**" dentro do objeto "**cliente**" . Dessa forma criamos um novo JSON mantendo a estrutura dos campos do JSON de entrada.

### **\* (asterisco)** <a href="#asterisco" id="asterisco"></a>

Referencia todos os campos e objetos de um JSON sem a necessidade de explicitar seus nomes na transformação.

Uso: **LHS**\
_Operations_: _shift, remove, cardinality, modify-default-beta_ e _modify-overwrite-beta_

Exemplo:

Temos o JSON de entrada contendo dados de Cliente:

```
{ 
  "nome": "Cliente Exemplo", 
  "email": "cliente-exemplo@email.com", 
  "documento": "123.456.789-10", 
  "dataNascimento": "10/05/1990", 
  "endereco": "Rua do Cliente Exemplo" 
}
```

E precisamos desses dados em um objeto de nome "cliente", porém precisamos alterar o campo **"documento"** para um campo de nome **"cpf"**:

```
{ 
  "cliente": { 
    "nome": "Cliente Exemplo", 
    "email": "cliente-exemplo@email.com", 
    "cpf": "123.456.789-10", 
    "dataNascimento": "10/05/1990", 
    "endereco": "Rua do Cliente Exemplo" 
  } 
}
```

Nossa transformação ficará:

```
[
  {
    "operation": "shift",
    "spec": {
      "*": "cliente.&",
      "documento": "cliente.cpf"
    }
  }
]
```

Na linha `"*": "cliente.&"`, estamos pegando qualquer conteúdo que exista no JSON de entrada e colocando em um objeto de nome "cliente" mantendo toda a estrutura de qualquer que seja esse conteúdo. Já para o campo "documento", estamos pegando seu valor e atribuindo a um campo de nome "cpf" também dentro do objeto "cliente".

O uso do curinga **\*** junto do **&** faz com que para cada campo que o **\*** encontre, o **&** manterá seu nome e valor. Essa utilização combinada de curingas é muito útil pois nos permite manipular um JSON sem a necessidade de conhecer e declarar seu conteúdo.

### **@** <a href="#h_e18ce3599b" id="h_e18ce3599b"></a>

Referencia o valor de um campo ou objeto contido no JSON de entrada, porém possui efeitos diferentes dependendo de sua aplicação.

Uso: **LHS** e **RHS**\
_Operations_: _shift_ (LHS e RHS), _modify-default-beta_ (RHS) e _modify-overwrite-beta_ (RHS).

Exemplo _shift_:

Temos um JSON contendo informações de Produto isoladas:

```
{  
    "chave": "codigo",  
    "valor": "123-ABC"
}
```

E precisamos agrupá-las em um objeto "produto", relacionando o campo "chave" com o campo "valor":

```
{  
    "produto" : {    
        "codigo" : "123-ABC"  
    }
}
```

Nossa transformação será:

```
[
  {
    "operation": "shift",
    "spec": {
      "valor": "produto.@(1,chave)"      
    }               
  }
]
```

Em **"@(1,chave)"** estamos pegando o **valor** do campo "chave" para ser usado como **nome** do campo que receberá o valor do campo "valor" **("@valor")**. O uso do **@** tanto no **LHS** quanto no **RHS** envolve a declaração do **nível** no qual estamos buscando a informação e fazemos a contagem dos níveis a partir do nível 1.

No caso o campo "chave" se encontra no mesmo nível que o campo "valor", por isso utilizamos o número **1**.

A aplicação do **@** no **LHS** segue da mesma forma que no **RHS**.

Exemplos _modify-default-beta_ e _modify-overwrite-beta_:

Temos um JSON de entrada com dados de Produto:

```
{
  "produto": {
    "nome": "Produto A",
    "preco": 10
  },
  "fabricante": "Empresa A"
}
```

E precisamos que o objeto "produto" contenha um campo "empresa" com o valor do campo "fabricante", que está fora de "produto":

```
{
  "produto" : {
    "nome" : "Produto A",
    "preco" : 10,
    "empresa" : "Empresa A" 
  },
  "fabricante" : "Empresa A"
}
```

A transformação ficará:

```
[
  {
    "operation": "modify-default-beta",    //para modify-overwrite-beta
    "spec": {                              //teríamos a mesma transformação
      "produto": {                         <- nível 2  
        "empresa": "@(2,fabricante)"       <- nível 1
      }
    }
  }
]
```

O que fizemos foi criar um campo de nome "empresa" e atribuir nele o valor do campo "fabricante". Para isso subimos até o nível 2 para poder enxergar o campo "fabricante" e assim pegar seu valor.

A diferença entre modify-default-beta e modify-overwrite-beta é que na **modify-default-beta** a inclusão do campo "empresa" só é feita caso não exista outro campo de nome "empresa" dentro de "produto".

Já para a **modify-overwrite-beta** a inclusão do campo empresa será feita mesmo que já exista o campo "empresa" dentro de "produto". Como o próprio nome _overwrite_ sugere, caso o conteúdo que queremos adicionar já exista no JSON de entrada, ele sempre será sobrescrito.

### **$** <a href="#h_e8ce5bfd26" id="h_e8ce5bfd26"></a>

Referencia o **nome** de um campo ou objeto contido no JSON de entrada para ser usado como **valor** de um campo ou objeto no JSON de saída.

Uso: **LHS**\
_Operations_: _shift_

Exemplo:

Temos um JSON de entrada com informações de Produto:

```
{
  "produto": {
    "nome": "Produto Exemplo",
    "valor": 10,
    "categoria": "CATEG-1",
    "peso": 25
  }
}
```

E precisamos de um JSON para saber quais informações de Produto estão sendo fornecidas:

```
{
  "produto": [ 
    "nome",
    "valor",
    "categoria",
    "peso"
  ]
}
```

Nossa transformação será:

```
[
  {
    "operation": "shift",
    "spec": {
      "produto": {
        "*": {
          "$": "produto[]" 
        }
      }
    }
  }
]
```

O que fizemos foi selecionar todos **(\*)** os campos do objeto "produto", em seguida pegar o nome **($)** de cada um deles e atribuí-los a uma lista de nome "produto".

Dessa forma podemos obter o nome de cada campo e não seus valores.

### **#** <a href="#h_3c37ac906e" id="h_3c37ac906e"></a>

Se usado no **LHS**, tem a função de inserir valores manualmente no JSON de saída.

Já no **RHS**, é aplicável apenas para a criação de **listas** e tem a função de agrupar determinado conteúdo do JSON de entrada dentro da lista a ser criada.

Uso: **LHS** e **RHS**\
_Operations_: _shift_

Exemplo **LHS**:

Temos um JSON de entrada com informações de Produto:

```
{
  "produto": {
    "nome": "Produto Exemplo",
    "valor": 10,
    "peso": 25
  }
}
```

E precisamos de um JSON que contenha informações de **nome**, **valor**, **peso** e **categoria** do produto:

```
{
  "produto" : {
    "categoria" : "CATEGORIA-PADRAO",
    "nome" : "Produto Exemplo",
    "valor" : 10,
    "peso" : 25
  }
}
```

Porém o JSON de entrada nunca fornece informações de **categoria**, com isso precisamos adicionar manualmente esse campo:

```
[
  {
    "operation": "shift",
    "spec": {
      "produto": {
        "*": "produto.&",
        "#CATEGORIA-PADRAO": "produto.categoria"
      }
    }
  }
]
```

O valor contido após o curinga **#** será sempre atribuído ao campo declarado no **RHS**, que no nosso caso é o campo "categoria" dentro do objeto "produto".

Exemplo **RHS**:

Temos um JSON de entrada contendo uma lista de Produtos:

```
{
  "listaProdutos": [ 
    {
      "codigo": "PROD-A", 
      "valor": 10
    },
    {
      "codigo": "PROD-B", 
      "valor": 20
    }
  ]
}
```

E precisamos apenas alterar o nome do campo **"valor"** para **"preco"**:

```
{
  "produtos": [
    {
      "codigo": "PROD-A", 
      "preco": 10
    },
    {
      "codigo": "PROD-B", 
      "preco": 20
    }
  ]
}
```

Nossa transformação ficará:

```
[
  {
    "operation": "shift",
    "spec": {
      "listaProdutos": {                   <- nível 2
        "*": {                             <- nível 1   
          "codigo": "produtos[#2].&",      <- nível 0
          "valor": "produtos[#2].preco"    <- nível 0
        }
      }
    }
  }
]
```

O uso do **#** no **RHS** envolve a declaração do **nível** no qual estamos buscando a informação. A declaração **\[#2]** representa a criação de uma **lista** **(\[ ])** e que esta deve **agrupar** **(#)** todas as informações que forem encontradas **2 níveis** acima.

Precisamos dessa declaração para que seja garantido o agrupamento correto de cada produto com seu respectivo "codigo" e "preco".

Ou seja, em `"codigo": "produtos[#2].&"` estamos pegando o valor do campo "codigo" e jogando para outro campo "codigo" dentro de uma lista de nome "produtos", e em `"valor": "produtos[#2].preco"` pegamos o valor do campo "valor" e jogamos para um campo de nome "preco" dentro da mesma lista "produtos".

Porém no momento da criação da lista "produtos" olharemos **2 níveis** acima **(nivel da lista "listaProdutos")** e da maneira que cada item estiver agrupado na "listaProdutos" anterior, esse agrupamento será mantido na nova lista "produtos".

### **| (pipe)** <a href="#pipe" id="pipe"></a>

Permite referenciar múltiplos campos ou objetos de um JSON de entrada para que, independente do **nome** do campo ou objeto, seu valor seja alocado no mesmo **destino** no JSON de saída.

Uso: **LHS**\
_Operations_: _shift_

Exemplo:

Temos um JSON de entrada contendo dados de Cliente:

```
{
  "cliente": {
    "nomeCompleto": "Cliente Exemplo",
    "email": "cliente-exemplo@email.com"
  }
}
```

E precisamos de um JSON da seguinte maneira:

```
  {
    "cliente": {
      "nome": "Cliente Exemplo",
      "email": "cliente-exemplo@email.com"
    }
}
```

Entretanto, no JSON de entrada, existe a possibilidade do campo `"nomeCompleto"` vir com o nome `"nomeCliente".`Com isso precisamos que a transformação esteja preparada para reconhecer as duas possibilidades:

```
[
  {
    "operation": "shift",
    "spec": {
      "cliente": {
        "nomeCompleto|nomeCliente": "cliente.nome",
        "email": "cliente.&"
      }
    }
  }
]
```

### _Operations modify-default-beta_ e _modify-overwrite-beta_ <a href="#operations-modify-default-beta-e-modify-overwrite-beta" id="operations-modify-default-beta-e-modify-overwrite-beta"></a>

Como dito na explicação do **curinga @**, estas _operations_ nos permitem referenciar valores de maneira dinâmica. Enquanto a _modify-default-beta_ atribuirá um valor a um campo caso este não exista, a _modify-overwrite-beta_ sobrescreverá qualquer qualquer valor mesmo que o campo já exista.

Entretanto, a _modify-overwrite-beta_ nos permite também aplicar **funções** em nosso JSON.

São elas:

* **String**\
  toLower, toUpper, concat, join, split, substring, trim, leftPad e rightPad
* **Number**\
  min, max, abs, avg, intSum, doubleSum, longSum, intSubtract, doubleSubtract, longSubtract, divide e divideAndRound
* **Type**\
  toInteger, toDouble, toLong, toBoolean, toString, recursivelySquashNulls, squashNulls, size
* **List**\
  firstElement, lastElement, elementAt, toList, sort

Exemplos:

JSON de entrada:

```
{
  "STRING": {
    "produto": "PRODUTO A",
    "empresa": "empresa a",
    "valor": "100",

    "medidaComEspacos": "  10 metros "
  },
  "NUMBER": {
    "array": [3, 5, 2, 7, 1],
    "valorNegativo": -100,
    "valorPositivo": 50
  },
  "TYPE": {
    "valor": 10.5,
    "stringBoolean": "true",
    "objetoComNulo": {
      "campoComValor": "ABC",
      "campoNulo": null
    }
  },
  "LIST": {
    "array": ["c", "t", "m", "a"],
    "campoString": "123"
  }
}
```

Transformações:

```
[
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "STRING": {
        "produto": "=toLower(@(1,produto))",
        "empresa": "=toUpper(@(1,empresa))",
        "produto_empresa": "=concat(@(1,produto),'_',@(1,empresa))",
        "joinProdutoEmpresa": "=join(' - ',@(1,produto),@(1,empresa))",
        "splitProdutoEmpresa": "=split('[-]',@(1,joinProdutoEmpresa))",
        "substringProduto": "=substring(@(1,produto),0,4)",
        "valor": "=leftPad(@(1,valor),6,'A')",
        "medida": "=trim(@(1,medidaComEspacos))"
      },
      "NUMBER": {
        "minArray": "=min(@(1,array))",
        "maxArray": "=max(@(1,array))",
        "valorAbsoluto": "=abs(@(1,valorNegativo))",
        "mediaArray": "=avg(@(1,array))",
        "somaArray": "=intSum(@(1,array))",
        "subtrArray": "=intSubtract(@(1,valorPositivo), 20)",
        "divisao": "=divide(@(1,valorPositivo),2)",
        "divisaoArred": "=divideAndRound(3,@(1,valorPositivo),3)"
      },
      "TYPE": {
        "valorInteiro": "=toInteger(@(1,valor))", 
        "booleano": "=toBoolean(@(1,stringBoolean))",
        "valorString": "=toString(@(1,valor))",
        "stringBoolean": "=size",
        "objetoComNulo": "=recursivelySquashNulls"
      },
      "LIST": {
        "arrayPrimeiroItem": "=firstElement(@(1,array))",
        "arrayUltimoItem": "=lastElement(@(1,array))",
        "arrayPosicao": "=elementAt(@(1,array),2)",
        "campoParaLista": "=toList(@(1,campoString))",
        "ordenaArray": "=sort(@(1,array))"
      }
    }
  }
]
```

JSON de saída:

```
{
  "STRING" : {
    "produto" : "produto a",
    "empresa" : "EMPRESA A",
    "valor" : "AAA100",
    "produto_empresa" : "produto a_EMPRESA A",
    "joinProdutoEmpresa" : "produto a - EMPRESA A",
    "splitProdutoEmpresa" : [ "produto a ", " EMPRESA A" ],
    "substringProduto" : "prod",
    "medida" : "10 metros"
  },
  "NUMBER" : {
    "array" : [ 3, 5, 2, 7, 1 ],
    "valorNegativo" : -100,
    "valorPositivo" : 50,
    "minArray" : 1,
    "maxArray" : 7,
    "valorAbsoluto" : 100,
    "mediaArray" : 3.6,
    "somaArray" : 18,
    "subtrArray" : 30,
    "divisao" : 25.0,
    "divisaoArred" : 16.667
  },
  "TYPE" : {
    "valor" : 10.5,
    "stringBoolean" : 4,
    "objetoComNulo" : {
      "campoComValor" : "ABC"
    },
    "valorInteiro" : 10,
    "booleano" : true,
    "valorString" : "10.5"
  },
  "LIST" : {
    "array" : [ "c", "t", "m", "a" ],
    "campoString" : "123",
    "arrayPrimeiroItem" : "c",
    "arrayUltimoItem" : "a",
    "campoParaLista" : [ "123" ],
    "ordenaArray" : [ "a", "c", "m", "t" ]
  }
}
```

{% hint style="info" %}
Algumas funções não foram incluídas na transformação acima pois seguem o mesmo princípio de outras que foram inclusas, como por exemplo as funções **doubleSum** e **longSum** que são aplicadas da mesma forma que a **intSum**. Referente às funções **recursivelySquashNulls** e **squashNulls**, ambas são aplicáveis apenas em **objetos** e **listas** e servem para removermos campos com valores nulos, porém enquanto a **recursivelySquashNulls** olhará para todos os níveis abaixo do objeto ou lista, a **squashNulls** olhará apenas **1** nível abaixo.
{% endhint %}

A _modify-overwrite-beta_ tem sua execução em **cascata**, ou seja, cada nova transformação é impactada pelas transformações anteriores.

Para entendermos esse comportamento em cascata, vamos pegar um trecho do JSON de entrada e das transformações acima:

```
//JSON de entrada
"STRING": {
    "produto": "PRODUTO A",
    "empresa": "empresa a",
    "valor": "100",

//Transformação
"STRING": {
        "produto": "=toLower(@(1,produto))",
        "empresa": "=toUpper(@(1,empresa))",
        "produto_empresa": "=concat(@(1,produto),'_',@(1,empresa))",
```

Em `"produto": "=toLower(@(1,produto))"` mudamos o valor de "produto" para **minúsculo** e em `"empresa": "=toUpper(@(1,empresa))"`, mudamos o valor de "empresa" para **maiúsculo**.

Portanto no momento em que fazemos `"produto_empresa": "=concat(@(1,produto),'_',@(1,empresa))"`, estamos utilizando os valores de "produto" e "empresa" já transformados e não seus valores originais contidos no JSON de entrada e com isso teremos `"produto_empresa": "produto a_EMPRESA A"`.

Para uma leitura mais técnica a respeito de JOLT, [acesse a documentação sobre JOLT no GitHub](https://github.com/bazaarvoice/jolt).

\
