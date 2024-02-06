---
description: >-
  Discover more about each operation that can be used in the Transformer (JOLT)
  and how to use it on the Digibee Integration Platform.
---

# Transformer - Operations overview

This article shows examples of the following JOLT operations (string):

* shift
* sort
* cardinality
* modify-overwrite-beta
* remove

## **shift**

Used to change JSON values or parts of the input tree, and add them to specified locations at the output. The structure is summarized into browsing up to the variable or JSON object that is intended to change the structure, place : (colon) and between "" quotation marks, inform the object destination.&#x20;

* **\* (asterisk):** refer to "all elements" within an object.&#x20;
* **& (ampersand):** copy the variable name to the destination.
* **. (dot):** create levels at the destination JSON.

Example:&#x20;

### **Input**

```
{
  "body": {
    "zip": "05350-000",
    "streetaddress": "Avenida Escola Politécnica",
    "neighbourhood": "Rio Pequeno",
    "city": "São Paulo",
    "state": "SP"
  },
  "client": {
    "code": 2,
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
      "client": {
        "code": "customer.id",
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

### **Output**

```
{
  "customer" : {
    "id" : 2,
    "name" : "RODRIGO LARA",
    "email" : "mail@digibee.com.br",
    "address" : {
      "zip" : "05350-000",
      "streetaddress" : "Avenida Escola Politécnica",
      "neighbourhood" : "Rio Pequeno",
      "city" : "São Paulo",
      "state" : "SP"
    }
  }
}
```

## **default**

Used to add new fields and values to the output JSON.

Example:

### **Input**

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
               "slice4"
             ]
           }
         }
       }
     }
   ]
 }
```

### **Output**

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

## **cardinality**

Used to transform elements at the input JSON into unique values (object) or output lists (array).

Example:

### **Input**

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
**Note:** the "ONE" instruction changes its list to an object with the first list element, while the "MANY" instruction changes a JSON object to a list.
{% endhint %}

### **Output**

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

Used to remover input JSON fields.

Example:

### **Input**

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

### **Output**

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

## **modify-overwrite-beta**

Used to allow using predefined functions at JOLT to change values and even the type of elements.

Functions include basic string and mathematic operations (toLower, toUpper, concat, min / max / abs, toInteger, toDouble, toInt), and can be applied to the origin JSON values.

Example:

### **Input**

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
             //accessing the "contents" element and changing its value to upper 
           "contents": "=toUpper"
        }
      }
    }
  }
]
```

### **Output**

```
{
  "counterTop" : {
    "loaf1" : {
      "type" : "white",
       "slices" : "slice1"
    },
    "jar2" : {
      //the output is in UpperCase
       "contents" : "JELLY"
    }
  }
}
```

## **sort**

Used to sort the entire JSON input at the output. Sorting cannot be configured; the entire JSON will be affected.

* Sorting does not consider variable amounts, only its name.
* The Output will be alphabetically sorted. (**Note:** following the JSON structure convention, the variable order does not change their structure/behavior.)

Example:

### **Input**

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

### **Output**

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
}
```

## **Remove all attributes with null value**

```
[{
    "operation": "modify-overwrite-beta",
    "spec": {
      "*": "=recursivelySquashNulls"
    }
  }]
```

[Learn more about other examples and Online Testing](https://jolt-demo.appspot.com/#inception). For advanced content on the topic, [check out the GitHub repository about JOLT](https://github.com/bazaarvoice/jolt).
