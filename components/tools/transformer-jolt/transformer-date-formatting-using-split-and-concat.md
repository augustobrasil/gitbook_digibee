---
description: >-
  Discover more about Transformer - Date formatting using split and concat and
  how to use it on the Digibee Integration Platform.
---

# Transformer - Date formatting using split and concat

### **Json input**

```
{  
    "data": {    
        "DATE": "18/09/1974"  
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
        "array_aux": "=split('/',@(1,DATE))",
        "DATE": "=concat(@(1,array_aux[2]),@(1,array_aux[1]),@(1,array_aux[0]))"
      }
    }
    },
  {
    "operation": "shift",
    "spec": {
      "data": {
        "DATE": "&"
      }
    }
  }
  ]
```

For this formatting, the following "operation" has been used: "**modify-overwrite-beta**", which allows changing the json.\
Use the command **=split** to split the date using the character '/' and to create a 3-position array. It is also possible to use **regex** on the split. [For more examples, refer to Github - Split Functions](https://github.com/bazaarvoice/jolt/blob/7812399d1c955742d81eae363244a2d0ef86cf3b/jolt-core/src/test/resources/json/modifier/functions/stringsSplitTest.json).

After the split, the command **=concat** gives us the possibility of concatenating array items according to the index.

### **Output** &#x20;

```
{  
    "DATE" : "19740918"
}
```

\
