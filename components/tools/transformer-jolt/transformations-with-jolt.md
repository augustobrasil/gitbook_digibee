---
description: >-
  Discover more about the Transformations with JOLT and how to use it on the
  Digibee Integration Platform.
---

# Transformations with JOLT

This article is intended to show examples of transformations in JSON, which are very common in integrations.

For a read on JOLT concepts and explanations:

[Transformer - Getting to know JOLT](transformer-getting-to-know-jolt.md)

Examples contained in this article:

* [Separating a Full Name field into First Name and Last Name fields](transformations-with-jolt.md#h\_18d21e23ce)
* [Separating area code from a phone number](transformations-with-jolt.md#h\_2b66e598e8)
* [Removing special characters from CPF and CNPJ](transformations-with-jolt.md#h\_3255b3ca05)
* [Eliminating duplicate values](transformations-with-jolt.md#h\_ead8cd6c25)
* [Adding numeric values](transformations-with-jolt.md#h\_0fea3e6d9d)
* [Multiplying 2 numeric values](transformations-with-jolt.md#h\_c4ea2b1807)
* [Applying a filter on the content of a field](transformations-with-jolt.md#h\_a8c023e98e)
* [Including default values within a list](transformations-with-jolt.md#h\_c8370a942e)

### **Separating a Full Name field into First Name and Last Name fields** <a href="#h_18d21e23ce" id="h_18d21e23ce"></a>

Input JSON:

```
{  
    "fullName": "Vitor Aquiles Sordi"
}
```

Output JSON:

```
{  
    "name": "Vitor",  
    "lastName": "Sordi"
}
```

Transformation:

```
[
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "fullName": "=split(' ',@(1,fullName))",
      "name": "=firstElement(@(1,fullName))",
      "lastName": "=lastElement(@(1,fullName))"
    }
  },
  {
    "operation": "remove",
    "spec": {
      "fullName": ""
    }
  }
]
```

> The **'remove'** operation only removes the "fullName" field, which is no longer useful. It has no effect on the separation of name and last name.

### **Separating area code from a phone number** <a href="#h_2b66e598e8" id="h_2b66e598e8"></a>

Input JSON:

```
{  
    "telephone": "11999998888"
}
```

Output JSON:

```
{  
    "ddd": "11",  
    "telephone": "999998888"
}
```

Transformation:

```
[
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "ddd": "=substring(@(1,telephone),0,2)",
      "sizeTelehone": "=size(@(1,telephone))",
      "telephone": "=substring(@(1,telephone),2,@(1,sizeTelephone))"
    }
  },
  {
    "operation": "remove",
    "spec": {
      "sizeTelephone": ""
    }
  }
]
```

For this type of transformation, and because of the nature of the substring function, we can specify the **initial** and **final** values for the snippet we want to obtain from a String.

However, in the case of phone numbers, we can have different sizes for the value of the "telephone" field, since it can accept both a landline number and a cell phone number. Also, the field can accept a formatted number like "1199999-8888".

For this reason, we chose to use the function **dynamically**.

First, we get the size of the value of "telephone" and then we pass it as a parameter to the substring function. This way, we do not have to worry about the size of the String, and we guarantee that we always get the last character of it.

### **Removing special characters from CPF and CNPJ** <a href="#h_3255b3ca05" id="h_3255b3ca05"></a>

Input JSON:

```
{  
    "cpf": "123.456.789-10",  
    "cnpj": "11.222.333/0001-10"
}
```

Output JSON:

```
{  
    "cpf": "12345678910",  
    "cnpj": "11222333000110"
}
```

Transformation:

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

> &#x20;The use of **'\[ ]'** in the split function is to apply **regular expressions** as a parameter of the function, and its use is not mandatory.

In the CPF example above, we were able to ensure that each occurrence of the characters **"."** and **"-"**, the split will be applied to the String we are manipulating. If we used the function without the **'\[ ]'** (`"=split('.-',(@1,cpf))"`), it would search for the combination of the characters **".-"** and we would have no effect, because this combination does not exist in the value of the "cpf" field. The same is true for the CNPJ example.

Then, we apply the _join_ function to combine all the values that were previously separated with the split function.

### **Eliminating duplicate values** <a href="#h_ead8cd6c25" id="h_ead8cd6c25"></a>

Input JSON:

```
{
  "products": [
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

Output JSON:

```
{
  "products": [
    {
      "id": "1"
    },
    {
      "id": "2"
    }
  ]
}
```

Transformation:

```
[
  {
    "operation": "shift",
    "spec": {
      "products": {
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
          "$": "products[].id"
        }
      }
    }
  }
]
```

In the first operation shift, in `"*": "ids.&[]"` we take all possible **values** from the "id" fields and use them as the **field names**. This way, we can guarantee that any duplicate ID is a unique field. Then, we assign these new fields to a new list of ids.

In the second operation shift, in `"$"`: "products\[].id", we take the **name** of each field contained in the "ids" list and use it as the **value** of the new "id" fields inside a new "products" list.

### **Adding numeric values** <a href="#h_0fea3e6d9d" id="h_0fea3e6d9d"></a>

Input JSON:

```
{
  "products": [
    {
      "id": 1,
      "name": "Product A",
      "value": 10
    },
    {
      "id": 2,
      "name": "Product B",
      "value": 20
    }
  ]
}
```

Output JSON:

```
{
  "products": [
    {
      "id": 1,
      "name": "Product A",
      "value": 10
    },
    {
      "id": 2,
      "name": "Product B",
      "value": 20
    }
  ],
  "totalValue": 30
}
```

Transformation:

```
[
  {
    "operation": "shift",
    "spec": {
      "products": {
        "*": {
          "*": "products[#2].&",
          "value": ["products[#2].&", "values[]"]
        }
      }
    }
  },
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "totalValue": "=doubleSum(@(1,valores))"
    }
  }
]

```

Using the operation shift, we create a list "values" containing all the values contained in the "products" lists, and ensure that the entire structure of "products" is preserved at the end of the transformation.

Then, we apply the doubleSum function directly to the "values" list so that all values are summed.

This approach is useful when dealing with arrays, since the arithmetic functions in JOLT allow us to work dynamically, visualizing all the values contained in a list at once.

In simpler scenarios, we can apply the functions explicitly as `"=doubleSum(@(1,firstValue),@(1,secondValue))"`.

### **Multiplying 2 numeric values** <a href="#h_c4ea2b1807" id="h_c4ea2b1807"></a>

JOLT does not have a native function for multiplying values.

However, for the multiplication of 2 values, we can proceed as follows:

Input JSON:

```
{  
    "value1": 10,  
    "value2": 2
}
```

Output JSON:

```
{  
    "value1": 10,  
    "value2": 2,  
    "inverseValue": 0.5,  
    "finalValue": 20
}
```

Transformation:

```
[
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "inverseValue": "=divide(1, @(1,value2))",
      "finalValue": "=divideAndRound(2, @(1,value1), @(1,inverseValue))"
    }
  }
]
```

By this transformation, the objective is to perform the multiplication inversely, that is, always dividing one of the values by 1, and then dividing the other value to be multiplied by the result of the first division by 1.

> The `=divide` and `=divideAndRound` functions do not support more than 2 values in their declaration.

### **Applying a filter on the content of a field** <a href="#h_a8c023e98e" id="h_a8c023e98e"></a>

Input JSON:

```
{
  "clients": [
    {
      "name": "Aquiles",
      "email": "aquiles@gmail.com"
    },
    {
      "name": "Marcos",
      "email": "marcos@outlook.com"
    },
    {
      "name": "Yuri",
      "email": "yuri@gmail.com"
    }
  ]
}
```

Output JSON:

```
{
  "clients": [
    {
      "name": "Aquiles",
      "email": "aquiles@gmail.com"
    },
    {
      "name": "Yuri",
      "email": "yuri@gmail.com"
    }
  ]
}
```

Transformation:

```
[
  {
    "operation": "shift",
    "spec": {
      "clients": {
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

In `"*\\@gmail.com"`, we check the value of the "email" field to get only emails with the domain **"gmail.com"**.

In this filter, the wildcard \* allows us to catch any content before "@gmail.com" and the **"\\"** character allows us to treat the **"@"** character exactly as a character and not like the wildcard **@**, also found in JOLT.

Finally, we use the **"\\"** character again to perform the escape of the subsequent "\\" character.

### **Including default values within a list** <a href="#h_c8370a942e" id="h_c8370a942e"></a>

To include default values in an array, you must specify \[] in the list that will inform. See below example.

Input JSON:

```
{
  "list": [
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

Output JSON:

```
{
  "list" : [ {
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

Transformation:

```
[
  {
    "operation": "default",
    "spec": {
      "list[]": {
        "*": {
          "e": "e"
        }
      }
    }
  }
]
```

Or

```
[
  {
    "operation": "modify-default-beta",
    "spec": {
      "list": {
        "*": {
          "e": "e"
        }
      }
    }
  }
]
```
