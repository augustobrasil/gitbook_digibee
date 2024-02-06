---
description: >-
  Discover more about the Transformer (JOLT) V2 component and how to use it on
  the Digibee Integration Platform.
---

# Transformer (JOLT) V2

**Transformer (JOLT) V2** allows the manipulation of a JSON through JOLT technology.

The component is useful:

* To modify the structure of a JSON and keep its values.
* To add, extract, and remove data from a JSON.
* To sort the structure of a JSON.
* To modify the values contained in a JSON through functions, such as text manipulation, mathematical calculations, conversions between data types, among others.
* To access and manipulate data from arrays.

## **Parameters**

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="231">Parameter</th><th width="236">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Expression Reference</strong></td><td>If the option is activated, the <strong>JOLT Reference</strong> parameter expects a JOLT expression declaration through Double Braces reference.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>JOLT</strong></td><td>The JOLT expression to be executed.</td><td>N/A</td><td>JSON</td></tr><tr><td><strong>JOLT Reference</strong> <code>(DB)</code></td><td>The Double Braces reference to the JOLT expression to be executed. This parameter is available only if <strong>Expression Reference</strong> is activated.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with an error will be interrupted. Otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## **Recommended use for Expression Reference**

The **Expression Reference** parameter is only recommended for highly dynamic scenarios, as maintaining the JOLT operations separately from the **Transformer (JOLT) V2** component is very complex.

These scenarios require some precautions depending on how they are implemented, such as: managing JOLT operations through the [**Object Store**](../structured-data/object-store.md) component, transformations versioning, segregating definition and execution of the JOLT transformations between pipelines, and so on.

In addition, these scenarios can also increase the need for [**Log**](log.md) components in the pipeline due to the lack of visibility with dynamic scenarios.

## **JOLT operations**

### **Shift**

Used to change the structure of a JSON, keeping the values contained in that same JSON.

**Example:**

**Input**

```
{  
    "body": {    
        "userName": "John"  
    }
}
```

**Transformation**

```
[
  {
    "operation": "shift",
    "spec": {
      "body": {
        "userName": "data.user_name"
      }
    }
  }
]
```

**Output**

```
{  
    "data" : {    
        "user_name" : "John"  
    }
}
```

### **Default**

Used to add new fields or objects in a JSON, if they don't already exist.

**Example:**

**Input**

```
{  
    "body": {    
        "userName": "John"  
    }
}
```

**Transformation**

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
]
```

**Output**

```
{  
    "body": {    
        "userName": "John",    
        "email": "default@email.com"  
    }
}
```

### **Remove**

Used to remove fields or objects from a JSON.

**Example:**

**Input**

```
{  
    "body": {    
        "userName": "John",    
        "email": "default@email.com"  
    }
}
```

**Transformation**

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

**Output**

```
{  
    "body" : {    
        "userName" : "John"  
    }
}
```

### **Sort**

Used to sort fields and objects in a JSON, in alphabetical order.

**Example:**

**Input**

```
{
  "employee": {
    "phone": "999999999",
    "name": "Sort Employee",
    "birthDate": "1980-01-01",
    "role": "analyst"
  }
}
```

**Transformation:**

```
[
    {    
        "operation": "sort"  
    }
]
```

**Output**

```
{
  "employee" : {
    "birthDate" : "1980-01-01",
    "name" : "Sort Employee",
    "phone" : "999999999",
    "role" : "analyst"
  }
}
```

### **Cardinality**

Used to transform simple fields and objects into arrays and vice-versa.

**Example:**

**Input**

```
{
  "products": {
    "name": "Product A",
    "id": "123-A",
    "value": 10
  }
}
```

**Transformation**

```
[
  {
    "operation": "cardinality",
    "spec": {
      "products": "MANY"
    }
  }
]
```

**Output**

```
{
  "products" : [ {
    "name": "Product A",
    "id": "123-A",
    "value": 10
  } ]
}
```

### **Modify-default-beta**

Used to add values ​​and apply functions to a JSON.

**Example:**

**Input**

```
{
  "products": [
    {
      "name": "Product A",
      "price": 10
    },
    {
      "name": "Product B",
      "price": 20
    }
  ]
}
```

**Transformation**

```
[
  {
    "operation": "modify-default-beta",
    "spec": {
      "products": {
        "*": {
          "manufacturer": "Manufacturer default"
        }
      }
    }
  }
]
```

**Output**

```
{
  "products" : [ {
    "name" : "Product A",
    "price" : 10,
    "manufacturer": "Manufacturer default"
  }, {
    "name" : "Product B",
    "price" : 20,
    "manufacturer": "Manufacturer default"
  } ]
}
```

### **Modify-overwrite-beta**

Used to override values ​​and apply functions to a JSON.

**Example:**

**Input**

```
{
  "data": {
    "firstName": "John",
    "lastName": "Smith"
  }
}
```

**Transformation**

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

**Output**

```
{
  "data" : {
    "firstName" : "John",
    "lastName" : "Smith",
    "fullName" : "John Smith"
  }
}
```
