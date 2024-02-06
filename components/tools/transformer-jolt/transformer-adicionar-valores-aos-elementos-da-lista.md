---
description: >-
  Descubra mais sobre o Transformer e como adicionar valores aos elementos da
  lista na Digibee Integration Platform.
---

# Transformer - Adicionar valores aos elementos da lista

## **Adicionar um valor Fixo em diferentes elementos da lista**

### **Entrada**

```
{
   "happy": "true",
  "statistics": [
    {
      "id": "A",
      "min": "2.0",
      "max": "10.0",
      "avg": "7.9"
    },
    {
      "min": "6",
      "max": "6",
      "avg": "6"
    },
    {
      "id": "C"
    }
  ]
}
```

### **Transformer Spec**

```
[
  {
    "operation": "modify-overwrite-beta",
//para adicionar o valor somente se ele não existir, mude a operation para "modify-default-beta"
    "spec": {
      "statistics": {
        "*": {
          "valorNovo": "teste123"
        }
      }
    }
  }
]
```

### **Saída**

```
{
  "happy": "true",
  "statistics" : [ {
    "id" : "A",
    "min" : "2.0",
    "max" : "10.0",
    "avg" : "7.9",
    "valorNovo" : "teste123"
  }, {
    "min" : "6",
    "max" : "6",
    "avg" : "6",
    "valorNovo" : "teste123"
  }, {
    "id" : "C",
    "valorNovo" : "teste123"
  } ]
}
```

## **Adicionar Valores Dinâmicos**

Para adicionar o valor de forma dinâmica, utilize a estrutura do _Transformer Spec_ abaixo:

```
[
  {
    "operation": "modify-overwrite-beta",
    //para adicionar o valor somente se ele não existir, mude a operation para "modify-default-beta"
    "spec": {
      "statistics": {
        "*": {
          "valorNovo": "@(3,happy)"
        }
      }
    }
  }
]
```

\
Observação: no exemplo acima, o número 3 indica a quantidade de níveis que se deve "subir" para acessar o objeto JSON. Para entender melhor, veja o exemplo abaixo:

### **Entrada**

```
{
  "nivelA": {
    "nivelB": {
      "happy": "true"
    }
  },
  "nivelX": {
    "statistics": [
      {
        "id": "A",
        "min": "2.0",
        "max": "10.0",
        "avg": "7.9"
      },
      {
        "min": "6",
        "max": "6",
        "avg": "6"
      },
      {
        "id": "C"
      }
    ]
  }
}
```

### **Transformer Spec**

```
[
  {
    "operation": "modify-overwrite-beta",
     "spec": {
      "nivelX": {
        "statistics": {
//o item "*" (todos elementos da lista, também é considerado um nível)
          "*": {
            "valorNovo": "@(5,nivelA.nivelB.happy)"
          }
        }
      }
    }
  }
]
```

\


\
