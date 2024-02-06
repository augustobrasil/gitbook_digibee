---
description: >-
  Descubra mais sobre o Transformer para a formatação de datas utilizando split
  e concat e saiba como utilizá-lo na Digibee Integration Platform.
---

# Transformer - Formatação de datas utilizando split e concat

### **Entrada json**

```
{
  "data": {
    "PAC_DATA_NASCTO": "18/09/1974"
  }
}
```

### **Transformer Spec**

```
[
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "data": {
        "array_aux": "=split('/',@(1,PAC_DATA_NASCTO))",
        "PAC_DATA_NASCTO": "=concat(@(1,array_aux[2]),@(1,array_aux[1]),@(1,array_aux[0]))"
      }
    }
    },
  {
    "operation": "shift",
    "spec": {
      "data": {
        "PAC_DATA_NASCTO": "&"
      }
    }
  }
  ]
```

\
Para esta formatação foi utilizado o _operation_: "**modify-overwrite-beta**" que possibilita a alteração do json.\
Use o comando **=split** para separar a data pelo caractere '/' e  criar um _array_ de 3 posições. Também é possível utilizar **regex** no _split_. [Para mais exemplos, visite Github - Split Functions](https://github.com/bazaarvoice/jolt/blob/7812399d1c955742d81eae363244a2d0ef86cf3b/jolt-core/src/test/resources/json/modifier/functions/stringsSplitTest.json).

Após o _split_, o comando **=concat** nos dá a possibilidade de concatenar os itens do _array_ de acordo com o _index_.

### **Saída** &#x20;

```
{  
    "PAC_DATA_NASCTO" : "19740918"
}
```

\
