---
description: >-
  Descubra mais sobre qual operation pode ser utilizada no Transformer (JOLT) e
  saiba como utilizá-la na Digibee Integration Platform.
---

# Transformer - Visão geral das operations

Este artigo apresenta exemplos das seguintes _operations (string)_ de JOLT:

* shift
* sort
* cardinality
* modify-overwrite-beta
* remove

## **shift**

Usado para alterar a forma dos valores JSON ou partes da árvore de entrada e incluí-los em locais especificados na saída. A estrutura se resume em navegar até a variável ou objeto JSON que deseja alterar a estrutura, colocar : (dois pontos) e entre "" aspas, informar o destino para o objeto.&#x20;

* **\* (asterisco):** referencia "todos os elementos" dentro de um objeto.
* **& (e comercial):** copia o nome da variável para o destino.
* **. (ponto):** cria níveis no JSON de destino.

Exemplo:&#x20;

### **Entrada**

```
{
  "body": {
    "cep": "05350-000",
    "logradouro": "Avenida Escola Politécnica",
    "bairro": "Rio Pequeno",
    "localidade": "São Paulo",
    "uf": "SP"
  },
  "cliente": {
    "codigo": 2,
    "name": "RODRIGO LARA",
    "email": "mail@digibee.com.br",
    "due_date": "2019-03-27"
  }
}
```

### **Spec**

```
[

  {
    "operation": "shift",
    "spec": {
      "cliente": {
        "codigo": "customer.id",
        "name": "customer.&",
        "email": "customer.email"
      },
      "body": {
        "*": "customer.address.&"
      }
    }
    }

]
```

### **Saída**

```
{
  "customer" : {
    "id" : 2,
    "name" : "RODRIGO LARA",
    "email" : "mail@digibee.com.br",
    "address" : {
      "cep" : "05350-000",
      "logradouro" : "Avenida Escola Politécnica",
      "bairro" : "Rio Pequeno",
      "localidade" : "São Paulo",
      "uf" : "SP"
    }
  }
}
```

## **default**

Usado para adicionar novos campos e valores no JSON de saída.

Exemplo:

### **Entrada**

```
{
     "counterTop": {
       "loaf1": {
         "type": "white"
       },
       "loaf2": {
         "type": "wheat"
       },
       "jar1": {
         "contents": "peanut butter"
       },
       "jar2": {
         "contents": "jelly"
       }
}
```

### **Spec**

```
  [
     {
       "operation": "default",
       "spec": {
         "counterTop": {
           "loaf1": {
             "slices": [
               "slice1",
               "slice2",
               "slice3",
               "slice4
             ]
           }
         }
       }
     }
   ]
 }
```

### **Saída**

```
{
   "counterTop" : {
    "loaf1" : {
      "type" : "white",
       "slices" : [ "slice1", "slice2", "slice3", "slice4" ]
    },
    "loaf2" : {
      "type" : "wheat"
    },
    "jar1" : {
       "contents" : "peanut butter"
    },
    "jar2" : {
       "contents" : "jelly"
    }
  }
}
```

\
**cardinality**
---------------

Usado para transformar elementos no JSON de entrada em valores únicos (objeto) ou em listas (_array_) na saída.

Exemplo:

### **Entrada**

```
{
   "counterTop": {
    "loaf1": {
       "type": "white",
       "slices": [
         "slice1",
        "slice2",
         "slice3",
         "slice4"
      ]
    },
    "loaf2": {
       "type": "wheat"
    },
    "jar1": {
       "contents": "peanut butter"
    },
    "jar2": {
       "contents": "jelly"
    }
  }
}
```

### **Spec**

```
[
   {
      "operation": "cardinality",
     "spec": {
        "counterTop": {
          "loaf1": {
            "slices": "ONE" 
         }
       }
     }
    }
  ]
```

{% hint style="info" %}
A instrução "ONE" altera sua lista para um objeto com o primeiro elemento da lista e a instrução "MANY" altera um objeto no JSON para uma lista.
{% endhint %}

### **Saída**

```
{
   "counterTop" : {
    "loaf1" : {
      "type" : "white",
       "slices" : "slice1"
    },
    "loaf2" : {
      "type" : "wheat"
    },
    "jar1" : {
       "contents" : "peanut butter"
    },
    "jar2" : {
       "contents" : "jelly"
    }
  }
}
```

## **Remove**

Usado para remover campos do JSON de entrada

Exemplo:

### **Entrada**

```
{
   "counterTop": {
    "loaf1": {
       "type": "white",
       "slices": "slice1"
    },
    "loaf2": {
       "type": "wheat"
    },
    "jar1": {
       "contents": "peanut butter"
    },
    "jar2": {
       "contents": "jelly"
    }
  }
}
```

### **Spec**

```
[
   {
      "operation": "remove",
     "spec": {
        "counterTop": {
          "loaf2": "",
          "jar1": ""
       }
     }
    }
]
```

### **Saída**

```
{
   "counterTop" : {
    "loaf1" : {
      "type" : "white",
       "slices" : "slice1"
    },
    "jar2" : {
      "contents" : "jelly"
    }
  }
}
```

## **modify-overwrite-beta:**&#x20;

Usado para permitir a utilização de funções predefinidas no JOLT para alterar valores e até mesmo tipo dos elementos.

As funções incluem _operations_ básicas de _string_ e matemática (toLower, toUpper, concat, min / max / abs, toInteger, toDouble, toInt) e podem ser aplicadas aos valores JSON de origem.

Exemplo:

### **Entrada**

```
{
   "counterTop": {
    "loaf1": {
       "type": "white",
       "slices": "slice1"
    },
    "jar2": {
       "contents": "jelly"
    }
  }
}
```

### **Spec**

```
[
  {
     "operation": "modify-overwrite-beta",
    "spec": {
       "counterTop": {
         "jar2": {
             //acessando o elemento "contents" e alterando seu valor para upper
           "contents": "=toUpper"
        }
      }
    }
  }
]
```

### **Saída**

```
{
  "counterTop" : {
    "loaf1" : {
      "type" : "white",
       "slices" : "slice1"
    },
    "jar2" : {
      //a saída está em UpperCase
       "contents" : "JELLY"
    }
  }
}
```

## **sort**

Usado para ordenar toda a entrada JSON na saída. A Ordenação não pode ser configurada; todo o JSON será afetado.

* A Ordenação não olha para os valores das variáveis, apenas para seu nome.
* A Saída será ordenada em ordem alfabética. (**Observação:** seguindo o convenção de estrutura JSON, a ordem as variáveis não altera sua entrutura/comportamento.)

Exemplo:

### **Entrada**

```
{
   "counterTop": {
    "loaf1": {
       "type": "white",
       "slices": "slice1"
    },
    "jar2": {
       "contents": "JELLY"
    }
  }
}
```

### **Spec**

```
[
  {
     "operation": "sort"
    }
]
```

### **Saída**

```
{
   "counterTop" : {
    "jar2" : {
       "contents" : "JELLY"
    },
    "loaf1" : {
       "slices" : "slice1",
      "type" : "white"
    }
  }
}{
    "operation": "modify-overwrite-beta",
    "spec": {
      "*": "=recursivelySquashNulls"
    }
  }
```

## **Remover todos os atributos que os valores sejam **_**null**_

```
{
    "operation": "modify-overwrite-beta",
    "spec": {
      "*": "=recursivelySquashNulls"
    }
  }
```

\
[Aprenda mais com outros exemplos e Teste Online](https://jolt-demo.appspot.com/#inception). Para conteúdo avançado sobre o tema,[ confira o repositório sobre JOLT no GitHub](https://github.com/bazaarvoice/jolt).
