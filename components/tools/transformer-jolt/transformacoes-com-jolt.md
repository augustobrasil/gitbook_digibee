---
description: >-
  Descubra mais sobre as Transformações com JOLT e saiba como utilizá-las na
  Digibee Integration Platform.
---

# Transformações com JOLT

Este artigo visa mostrar exemplos de transformações em JSONs muito comuns em integrações.

Para uma leitura referente aos conceitos e explicações sobre JOLT:&#x20;

[Transformer - Conhecendo o JOLT](transformer-conhecendo-o-jolt.md)

Exemplos contidos neste artigo:

* [Separando um campo de Nome completo em campos de Nome e Sobrenome](transformacoes-com-jolt.md#separando-um-campo-de-nome-completo-em-campos-de-nome-e-sobrenome)
* [Separando DDD de um número de telefone](transformacoes-com-jolt.md#separando-ddd-de-um-nmero-de-telefone)
* [Removendo caracteres especiais de CPF e CNPJ](transformacoes-com-jolt.md#removendo-caracteres-especiais-de-cpf-e-cnpj)
* [Eliminando valores duplicados](transformacoes-com-jolt.md#eliminando-valores-duplicados)
* [Somando valores numéricos](transformacoes-com-jolt.md#somando-valores-numericos)
* [Multiplicando 2 valores numéricos](transformacoes-com-jolt.md#multiplicando-2-valores-numericos)
* [Aplicando filtro no conteúdo de um campo](transformacoes-com-jolt.md#aplicando-filtro-no-contedo-de-um-campo)
* [Incluindo valores defaults dentro de uma lista](transformacoes-com-jolt.md#incluindo-valores-defaults-dentro-de-uma-lista)

### Separando um campo de Nome completo em campos de Nome e Sobrenome <a href="#separando-um-campo-de-nome-completo-em-campos-de-nome-e-sobrenome" id="separando-um-campo-de-nome-completo-em-campos-de-nome-e-sobrenome"></a>

JSON de entrada:

```
{  
    "nomeCompleto": "Vitor Aquiles Sordi"
}
```

JSON de saída:

```
{  
    "nome": "Vitor",  
    "sobrenome": "Sordi"
}
```

Transformação:

```
[
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "nomeCompleto": "=split(' ',@(1,nomeCompleto))",
      "nome": "=firstElement(@(1,nomeCompleto))",
      "sobrenome": "=lastElement(@(1,nomeCompleto))"
    }
  },
  {
    "operation": "remove",
    "spec": {
      "nomeCompleto": ""
    }
  }
]
```

> A _**operation remove**_ apenas remove o campo "nomeCompleto" que já não é mais útil. A mesma não tem impacto na separação do Nome e Sobrenome.

### Separando DDD de um número de telefone <a href="#separando-ddd-de-um-nmero-de-telefone" id="separando-ddd-de-um-nmero-de-telefone"></a>

JSON de entrada:

```
{  
    "telefone": "11999998888"
}
```

JSON de saída:

```
{  
    "ddd": "11",  
    "telefone": "999998888"
}
```

Transformação:

```
[
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "ddd": "=substring(@(1,telefone),0,2)",
      "tamanhoTelefone": "=size(@(1,telefone))",
      "telefone": "=substring(@(1,telefone),2,@(1,tamanhoTelefone))"
    }
  },
  {
    "operation": "remove",
    "spec": {
      "tamanhoTelefone": ""
    }
  }
]
```

Para este tipo de transformação, e pela natureza da função _substring_, podemos explicitar os valores de **início** e **fim** para o trecho que desejamos obter de uma _String._

Entretanto, se tratando de números de telefone, podemos ter tamanhos variados para o valor do campo "telefone", pois o mesmo pode aceitar tanto um número de telefone fixo como um número de celular, além de o campo poder aceitar um número formatado, como "1199999-8888".

Por conta disso, optamos por utilizar a função de maneira **dinâmica.**

Primeiro obtemos o tamanho do valor de "telefone" e em seguida o passamos como parâmetro da função _substring_. Assim, não precisamos nos preocupar com o tamanho da _String_ e garantimos que sempre pegaremos até o último caractere da mesma.

### Removendo caracteres especiais de CPF e CNPJ <a href="#removendo-caracteres-especiais-de-cpf-e-cnpj" id="removendo-caracteres-especiais-de-cpf-e-cnpj"></a>

JSON de entrada:

```
{  
    "cpf": "123.456.789-10",  
    "cnpj": "11.222.333/0001-10"
}
```

JSON de saída:

```
{  
    "cpf": "12345678910",  
    "cnpj": "11222333000110"
}
```

Transformação:

```
[
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "cpf": "=split('[.-]',@(1,cpf))",
      "cnpj": "=split('[./-]',@(1,cnpj))"
    }
  },
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "cpf": "=join('',@(1,cpf))",
      "cnpj": "=join('',@(1,cnpj))"
    }
  }
]
```

> O uso de **'\[ ]'** na função _split_ serve para aplicarmos **expressões regulares** como parâmetro da função e seu uso não é obrigatório.

No exemplo de CPF acima, conseguimos garantir que para cada ocorrência dos caracteres **"."** e **"-"**, será aplicado a _split_ na _String_ que estamos manipulando. Caso utilizássemos a função sem os **'\[ ]'** (`"=split('.-',(@1,cpf))"`), a mesma buscaria pela combinação dos caracteres **".-"** e não teríamos efeito nenhum, pois essa combinação não existe no valor do campo "cpf". O mesmo serve para o exemplo de CNPJ.

Em seguida, aplicamos a função _join_ para juntarmos todos os valores separados com a função _split_ anteriormente.

### Eliminando valores duplicados <a href="#eliminando-valores-duplicados" id="eliminando-valores-duplicados"></a>

JSON de entrada:

```
{
  "produtos": [
    {
      "id": 1
    },
    {
      "id": 2
    },
    {
      "id": 1
    }
  ]
}
```

JSON de saída:

```
{
  "produtos": [
    {
      "id": "1"
    },
    {
      "id": "2"
    }
  ]
}
```

Transformação:

```
[
  {
    "operation": "shift",
    "spec": {
      "produtos": {
        "*": {
          "id": {
            "*": "ids.&[]"
          }
        }
      }
    }
  },
  {
    "operation": "shift",
    "spec": {
      "ids": {
        "*": {
          "$": "produtos[].id"
        }
      }
    }
  }
]
```

Na primeira _operation shift_, em `"*": "ids.&[]"` pegamos todos os possíveis **valores** dos campos "id" e os utilizamos como **nome de campo**. Assim conseguimos garantir que qualquer ID duplicado seja um campo único. Em seguida, atribuímos esses novos campos para uma nova lista de ids.

Já na segunda _operation shift_, em `"$": "produtos[].id"` pegamos o **nome** de cada campo contido na lista "ids" e usamos como **valor** de novos campos "id" dentro de uma nova lista "produtos".

### **Somando valores numéricos**

JSON de entrada:

```
{
  "produtos": [
    {
      "id": 1,
      "nome": "Produto A",
      "valor": 10
    },
    {
      "id": 2,
      "nome": "Produto B",
      "valor": 20
    }
  ]
} 
```

JSON de saída:

```
{
  "produtos": [
    {
      "id": 1,
      "nome": "Produto A",
      "valor": 10
    },
    {
      "id": 2,
      "nome": "Produto B",
      "valor": 20
    }
  ],
  "valorTotal": 30
}
```

Transformação:

```
[
  {
    "operation": "shift",
    "spec": {
      "produtos": {
        "*": {
          "*": "produtos[#2].&",
          "valor": ["produtos[#2].&", "valores[]"]
        }
      }
    }
  },
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "valorTotal": "=doubleSum(@(1,valores))"
    }
  }
]

```

Com a _operation shift,_ criamos uma lista "valores" contendo todos os valores contidos nas listas "produtos" e garantimos que toda estrutura de "produtos" seja mantida no final da transformação.

Em seguida, aplicamos a função _doubleSum_ direto na lista "valores" para que todos os seus valores sejam somados.

Essa abordagem é útil quando lidamos com _arrays_ pois as funções aritméticas no JOLT nos permitem trabalhar de maneira dinâmica, enxergando de uma só vez todos os valores contidos em uma lista.

Em cenários mais simples, podemos aplicar as funções de maneira explícita como `"=doubleSum(@(1,primeiroValor),@(1,segundoValor))"`

### **Multiplicando 2 valores numéricos**

O JOLT não possui uma função nativa para multiplicação de valores.

Entretanto, para a multiplicação de 2 valores, podemos contornar da seguinte maneira:

JSON de entrada:

```
{  
    "valor1": 10,  
    "valor2": 2
}
```

JSON de saída:

```
{  
    "valor1": 10,  
    "valor2": 2,  
    "valorInverso": 0.5,  
    "valorFinal": 20
}
```

Transformação:

```
[
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "valorInverso": "=divide(1, @(1,valor2))",
      "valorFinal": "=divideAndRound(2, @(1,valor1), @(1,valorInverso))"
    }
  }
]
```

A ideia com essa transformação é realizar a multiplicação de maneira inversa, ou seja, sempre dividindo um dos valores por 1 e em seguida dividindo o outro valor a ser multiplicado pelo resultado da primeira divisão por 1.

> As funções `=divide` e `=divideAndRound` não suportam mais que 2 valores em sua declaração.

### Aplicando filtro no conteúdo de um campo <a href="#aplicando-filtro-no-contedo-de-um-campo" id="aplicando-filtro-no-contedo-de-um-campo"></a>

JSON de entrada:

```
{
  "clientes": [
    {
      "nome": "Aquiles",
      "email": "aquiles@gmail.com"
    },
    {
      "nome": "Marcos",
      "email": "marcos@outlook.com"
    },
    {
      "nome": "Yuri",
      "email": "yuri@gmail.com"
    }
  ]
}
```

JSON de saída:

```
{
  "clientes": [
    {
      "nome": "Aquiles",
      "email": "aquiles@gmail.com"
    },
    {
      "nome": "Yuri",
      "email": "yuri@gmail.com"
    }
  ]
}
```

Transformação:

```
[
  {
    "operation": "shift",
    "spec": {
      "clientes": {
        "*": {
          "email": {
            "*\\@gmail.com": {
              "@2": "gmail[]"
            }
          }
        }
      }
    }
  }
]
```

Em `"*\\@gmail.com"`, verificamos o valor do campo "email" para obtermos apenas os emails com domínio **"gmail.com".**

Neste filtro, o curinga **\*** nos permite pegar qualquer conteúdo antes de "@gmail.com" e o caractere **"\\"** nos permite tratar o caractere **"@"** exatamente como um caractere e não como o curinga **@** também existente no JOLT.

Por último, utilizamos a caractere **"\\"** mais uma vez para realizarmos o _escape_ do caractere **"\\"** subsequente.

### **Incluindo valores **_**defaults**_** dentro de uma lista**

Para incluir valores _default_ dentro de um _array_, é necessário especificar \[] na lista que vai informar. Segue exemplo abaixo.

JSON de entrada:

```
{
  "lista": [
    {
      "a": "a",
      "b": "b"
    },
    {
      "c": "c",
      "d": "d"
    }
  ]
}
```

JSON de saída:

```
{
  "lista" : [ {
    "a" : "a",
    "b" : "b",
    "e" : "e"
  }, {
    "c" : "c",
    "d" : "d",
    "e" : "e"
  } ]
}
```

Transformação:

```
[
  {
    "operation": "default",
    "spec": {
      "lista[]": {
        "*": {
          "e": "e"
        }
      }
    }
  }
]
```

Ou

```
[
  {
    "operation": "modify-default-beta",
    "spec": {
      "lista": {
        "*": {
          "e": "e"
        }
      }
    }
  }
]
```

\
