---
description: >-
  Discover more about the Transformer (JOLT) component and how to use it on the
  Digibee Integration Platform.
---

# Transformer (JOLT)

**Transformer (JOLT)** allows the manipulation of a JSON through JOLT technology.

The component is useful to:

* modify the structure of a JSON and keep its values;
* add, extract, and remove data from a JSON;
* sort the structure of a JSON;
* modify the values contained in a JSON through functions, such as text manipulation, mathematical calculations, and conversions between data types, among others;
* access and manipulate data from arrays.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Type Properties</strong></td><td>Area to include the JOLT transformations.</td><td>N/A</td><td>String</td></tr></tbody></table>

Example of a configured **Transformer (JOLT)**:

![](<../../../.gitbook/assets/transformer jolt1.png>)

{% hint style="info" %}
The JSON configured in **Type Properties** doesn’t represent the JSON to be manipulated, but the JOLT transformation itself. The JOLT itself uses a JSON structure for the transformation construction, which will interpret the JSON received by the **Transformer (JOLT)** component.
{% endhint %}

## JOLT operations <a href="#h_95d6513252" id="h_95d6513252"></a>

### Shift

Used to change the structure of a JSON, keeping the values contained in that same JSON.

**Example:**

Input

```
{  
    "body": {    
        "userName": "John"  
    }
}
```

Transformation

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

Output

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

Input

```
{  
    "body": {    
        "userName": "John"  
    }
}
```

Transformation

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

Output

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

Input

```
{  
    "body": {    
        "userName": "John",    
        "email": "default@email.com"  
    }
}
```

Transformation

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

Output

```
{  
    "body" : {    
        "userName" : "John"  
    }
}
```

### **Sort**

Used to sort fields and objects in a JSON in alphabetical order.

**Example:**

Input

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

Transformation:

```
[
    {    
        "operation": "sort"  
    }
]
```

Output

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

Used to transform simple fields and objects into arrays and vice versa.

**Example:**

Input

```
{
  "products": {
    "name": "Product A",
    "id": "123-A",
    "value": 10
  }
}
```

Transformation

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

Output

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

Input

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

Transformation

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

Output

```
{
  "products" : [ {
    "name" : "Produto A",
    "price" : 10,
    "manufacturer": "Manufacturer default"
  }, {
    "name" : "Produto B",
    "price" : 20,
    "manufacturer": "Manufacturer default"
  } ]
}

```

### **Modify-overwrite-beta**

Used to override values ​​and apply functions to a JSON.

**Example:**

Input

```
{
  "data": {
    "firstName": "John",
    "lastName": "Smith"
  }
}
```

Transformation

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

Output

```
{
  "data" : {
    "firstName" : "John",
    "lastName" : "Smith",
    "fullName" : "John Smith"
  }
}
```

[Click here to read a detailed article about Transformer (JOLT).](https://docs.digibee.com/documentation/components/tools/transformer-jolt/transformer-getting-to-know-jolt)

\
