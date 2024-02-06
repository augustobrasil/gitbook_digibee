---
description: >-
  Discover more about the JOLT applications and how to use its transformations
  on the Digibee Integration Platform.
---

# Transformer - Getting to know JOLT

**Transformer (JOLT)** applications allow transformations of JSON through JOLT.

For development and tests of all examples contained in this article,[ refer to the JOLT playground](https://jolt-demo.appspot.com/#inception).

## **JOLT - JSON** <a href="#jolt---json-language-for-transform" id="jolt---json-language-for-transform"></a>

JSON is the format that JOLT uses for transformations. Its usage is based on the structure below, which always depends on an input:

```
[ 
  { 
    "operation": "", 
    "spec": { 
        
    } 
  } 
] 
```

Where:

* **"operations"**: type of transformation that will be applied.
* **"spec"**: area where to put the transformation.
* **"\[]"**: the JOLT self base structure is also a JSON, and with it there is an array that allows chaining many operations.

## **Operations** <a href="#operations" id="operations"></a>

JOLT contains the following types of operations:

* **shift**
* **default**
* **remove**
* **sort**
* **cardinality**
* **modify-default-beta**
* **modify-overwrite-beta**

Each operation has its peculiarity and will perform the transformation differently. However, they all follow the same principle for transformations, which is **navigation** in the structure of the input JSON.&#x20;

Below we will see in more detail how this happens.

### **shift**

Changes the structure of a JSON, keeping the values contained in that same JSON file.\
\
Its use consists on navigating the JSON structure to the **field** or **object** that we want to get its value and then inform where this value should be placed in the new JSON that we want.

Let's see the example below:

We have an input JSON containing information about Clients:

```
{ 
  "client": { 
    "name": "Sample Client", 
    "email": "sample-client@email.com", 
    "ssn": "123.456.789.10", 
    "birthDate": "02/15/1985", 
    "address": "Sample Client street, 123",
    "country": "United States",
    "number": "8888-8888"
  } 
}
```

And we want a new JSON with the following structure:

```
{
  "customer" : {
    "fullName" : "Sample Client",
    "birthDate" : "02/15/1985",
    "address" : {
      "street" : "Sample Client street, 123",
      "country" : "United States"
    },
    "phoneNumber" : "8888-8888",
    "mobileNumber" : "8888-8888"
  }
}
```

Our transformation will be:

```
[
  {
    "operation": "shift",
    "spec": {
      "client": {
        "name": "customer.fullName",
        "birthDate": "customer.birthDate",
        "address": "customer.address.street",
        "country": "customer.address.country",
        "number": ["customer.phoneNumber", "customer.mobileNumber"]
      }
    }
  }
]
```

What we did above was **navigating** to the **fields** of our interest and inform where the **values** of each one of these fields should be inserted.

Through the notation **"." (dot)**, we can define levels in the new JSON that we want to create. With that, in `"name":"customer.fullName"` we take the value of the field **name** and throw it into the field **fullName** inside of the object **customer**, and in `"address":"customer.address.street"` we take the value of the field **address** and throw it into the field **street** inside of the object **address** which will also be contained in the object **customer**.

{% hint style="info" %}
We can take the same value and throw it into more than 1 field at the same time.
{% endhint %}

In `"number": ["customer.phoneNumber", "customer.mobileNumber"]`, we take the value of the field **number** and throw it into the fields **phoneNumber** and **mobileNumber**, both contained in **customer**. This approach allows us to transpose a value into _**n**_ new fields.

{% hint style="warning" %}
In this operation, only the fields that are manipulated in the transformation will be considered, so any data in the input JSON that is not used will be discarded.
{% endhint %}

Final JSON:

```
{
  "customer" : {
    "fullName" : "Sample Client",
    "birthDate" : "02/15/1985",
    "address" : {
      "street" : "Sample Client street, 123",
      "country" : "United States"
    },
    "phoneNumber" : "8888-8888",
    "mobileNumber" : "8888-8888"
  }
}
```

### default

Used to add new fields or objects in a JSON, if they do not already exist.

Its use consists in navigating the JSON structure to the desired level and inserting the field or object with its respective value.

{% hint style="warning" %}
In case of the field declared in the transformation already exists in the input JSON, the transformation will have no effect.
{% endhint %}

Let's see the example below:

We have an input JSON containing information about Customer:

```
{
  "customer": {
    "name": "Customer Default",
    "ssn": "123.456.789.10"
  }
}
```

However, we need a JSON that in addition to the name and ssn, also contains the customer's date of birth.

```
{
  "customer": {
    "name": "Customer Default",
    "ssn": "123.456.789.10",
    "birthDate": "01/01/1970"
  }
}
```

Our transformation will be:

```
[  {    
  {
    "operation": "default",
    "spec": {
      "customer": {
        "birthDate": "01/01/1970"
      }
    }
  }
]
```

Above we navigate to the object **customer** and add the field **birthDate** with a default value.

### **remove**

Used to remove fields or objects from a JSON.

Its use consists in navigating the input JSON structure to the desired level and inform the field to be removed.

Let's see the example below:\
\
We have an input JSON containing information about Customer:

```
{
  "customer": {
    "name": "Customer Default",
    "ssn": "123.456.789.10",
    "birthDate": "01/01/1970"
  }
}
```

However, we need a JSON that only contains the customer's name and ssn:

```
{
  "customer": {
    "name": "Customer Default",
    "ssn": "123.456.789.10"
  }
}

```

Our transformation will be:

```
[
  {
    "operation": "remove",
    "spec": {
      "customer": {
        "birthDate": ""
      }
    }
  }
]
```

What we did above was navigate to the field **birthDate** and assign it to **" " (empty quotation marks)**.

The field to be removed must always be assigned to an empty String (""), otherwise, there will be a break in the transformation and it will not occur.

### **sort**

Used to sort fields and objects in a JSON in alphabetical order.

{% hint style="warning" %}
The ordering of fields and objects cannot be configured, therefore all JSON will be affected. Only the fields' names are ordered and not their values.
{% endhint %}

Let's see the example below:

We have an input JSON containing information about Employees:

```
{
  "employee": {
    "phone": "9 9999-9999",
    "name": "Employee Sort",
    "birthDate": "01/01/1980",
    "role": "JOLT Analyst"
  }
}
```

We need all fields contained in the input JSON to be ordered in alphabetical order:

```
{
  "employee": {
    "birthDate": "01/01/1980",
    "name": "Employee Sort",
    "phone": "9 9999-9999",
    "role": "JOLT Analyst"
  }
}
```

For the _operation sort_, we don't need to define the **"spec"** object that we always use together with **"operation"** field.

Our transformation will be:

```
[
  {
    "operation": "sort"
  }
]
```

### **cardinality**

Used to transform simple fields and objects into lists of objects and vice-versa.

{% hint style="warning" %}
When we transform a list object to a simple field or object, only the first element of the list will be considered.
{% endhint %}

Let's see the example below:

We have an input JSON containing information about Products:

```
{
  "products": {
    "name": "Product A",
    "id": "123-A",
    "value": 10
  }
}
```

We need to transform the "products" **object** into a **list**:

```
{
  "products": [
    {
      "name": "Product A",
      "id": "123-A",
      "value": 10
    }
  ]
}
```

\
Our transformation will be:

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

In case we have a list of products:

```
{
  "products": [
    {
      "name": "Product A",
      "id": "123-A",
      "value": 10
    },
    {
      "name": "Product B",
      "id": "456-B",
      "value": 20
    }
  ]
}
```

And we need to transform that **list** into a **simple object**:

```
{
  "products": {
    "name": "Product A",
    "id": "123-A",
    "value": 10
  }
}

```

Our transformation will be:

```
[
  {
    "operation": "cardinality",
    "spec": {
      "products": "ONE"
    }
  }
]
```

## **Deepening knowledge** <a href="#deepening-knowledge" id="deepening-knowledge"></a>

Until here we saw essential concepts to understand JOLT and its utilization. However, before we know the remaining _operations_, we need to know some more elaborate concepts.

Still, as a prerequisite to moving forward, we will see 2 expressions that are used to better understand JOLT.

They are:

* **LHS (Left Hand Side)**\
  Used to reference the left side of the transformation.
* **RHS (Right Hand Side)**\
  Used to reference the right side of the transformation.

That is, all JSON content that is **before** : **(colon)** will be our **LHS** and what is **after** : **(colon)** will be our **RHS**.

Transformation example:

```
[
  {
    "operation": "shift",
    "spec": {
LHS -> "customer": {
  LHS ->  "name": "client.fullName",  <- RHS
  LHS ->  "birhtDate": "client.dateOfBirth",  <- RHS
  LHS ->  "address": "client.address.street",  <- RHS
  LHS ->  "country": "client.address.country"  <- RHS
      }
    }
  }
]
```

Now we can move forward.

The great power of JOLT it's in the possibility of dealing with transformations in a **dynamic** way. For this, we use **wildcards**, which are specific characters allocated in different ways in our transformations, each with a different function.

One wildcard can have different functions depending on its use **(LHS** and **RHS)**, and, in addition, we can combine different wildcards in the same transformation.

Below we will see its definitions and some usage examples.

### **&**

It uses the content of what is declared in the **LHS** to compose the structure of the output JSON, without the need to make this content explicit in the transformation.&#x20;

This wildcard is based on the **navigation** made during the transformation.

Usage: **RHS**\
Operation: shift

Example:

We have a JSON that contains Customer's data:

```
{
  "name": "Client Example",
  "email": "client-example@email.com"
}
```

And we need this data in an object called "client":

```
{
  "client": {
    "name": "Client Example",
    "email": "client-example@email.com"
  }
}
```

Our transformation will be:

```
[
  {
    "operation": "shift",
    "spec": {
      "name": "client.&",
      "email": "client.&"
    }
  }
]
```

In **&**, we take the values of fields **"name"** and **"email"** then we assign it to other fields called **"name"** and **"email"** inside a **"client"** object. Thus we create a new JSON keeping the input field structure of the input JSON.

### **\* (asterisk)**

References all fields and objects in a JSON without having to make their names explicit in the transformation.

Usage: **LHS**\
Operations: shift, remove, cardinality, modify-default-beta and modify-overwrite-beta

Example:

We have an input JSON containing Customer's data:

```
{
  "name": "Customer Example",
  "email": "cliente-exemplo@email.com",
  "document": "1234567890",
  "birthDate": "10/31/1990",
  "address": "Customer Example Street"
}
```

And we need this data in an object named "customer", but we need to change the "**document**" field to a field named "**ssn**":

```
{
  "customer": {
    "name": "Customer Example",
    "email": "client-example@email.com",
    "document": "1234567890",
    "birthDate": "10/31/1990",
    "address": "Customer Example Street"
  }
}

```

Our transformation will be:

```
[
  {
    "operation": "shift",
    "spec": {
      "*": "customer.&",
      "document": "customer.ssn"
    }
  }
]
```

In the line `"*": "customer. &"`, we are taking any existing content in the input JSON and placing it in an object named "customer" keeping the entire structure of whatever that content is. As for the "document" field, we are taking its value and assigning it to a field named "ssn" also within the "customer" object.

Using the wildcard **\*** next to **&** means that for each field that **\*** finds, **&** will keep its name and value. This combined use of wildcards is very useful as it allows us to manipulate a JSON without the need to know and declare its content.

### **@**

References the value of a field or object contained in the input JSON, but has different effects depending on its usage.

Usage: **LHS and RHS**\
Operations: shift (LHS and RHS), modify-overwrite-beta (RHS) and modify-overwrite-beta (RHS).

Shift example:\
We have a JSON containing isolated Product's information:

```
{  
    "key": "code",  
    "value": "123-ABC"
}
```

And we need to group them into a "product" object, relating the "key" field to the "value" field:

```
{  
    "product": {    
        "code": "123-ABC"  
    }
}
```

Our transformation will be:

```
[
  {
    "operation": "shift",
    "spec": {
      "value": "product.@(1,key)"
    }
  }
]

```

In **"@ (1, key)"** we are taking the **value** of the "key" field to be used as the **name** of the field that will receive the value of the "value" field (**"@value"**). The use of @ in both **LHS** and **RHS** involves declaring the **level** at which we are seeking information and counting levels from level 1 onwards.

In this case, the "key" field is on the same level as the "value" field, so we use the number **1**.

The usage of **@** in **LHS** follows the same way as in **RHS**.

modify-default-beta and modify-overwrite-beta examples:

We have a JSON containing isolated Product's information:

```
{
  "product": {
    "name": "Produto A",
    "price": 10
  },
  "manufacturer": "Company A"
}
```

And we need the "product" object to contain a "company" field with the value of the "manufacturer" field, which is outside "product":

```
{
  "product": {
    "name": "Product A",
    "price": 10,
    "company": "Company A"
  },
  "manufacturer": "Company A"
}
```

The transformation will be:

```
[
  {
    "operation": "modify-default-beta",  //for modify-overwrite-beta 
    "spec": {                            //we'd have the same transformation
      "produto": {                       <- level 2   
        "company": "@(2,manufacturer)"   <- level 1 
      }
    }
  }
]
```

What we did was create a field named "company" and assign the value of the field "manufacturer" in it. For that, we went up to level 2 to see the "manufacturer" field and thus get its value.

The difference between modify-default-beta and modify-overwrite-beta is that in **modify-default-beta** the inclusion of the "company" field is only made if there is no other field named "company" within "product".

For **modify-overwrite-beta**, the company field will be included even if the "company" field already exists within "product". As the name overwrite suggests, if the content we want to add already exists in the input JSON, it will always be overwritten.

### **$**

References the **name** of a field or object contained in the input JSON to be used as the **value** of a field or object in the output JSON.

Usage: **LHS**\
Operations: shift

Example:

We have an input JSON containing Product data:

```
{
  "product": {
    "name": "Product Example",
    "value": 10,
    "category": "CATEG-1",
    "weight": 25
  }
}
```

And we need a JSON to know what product information is being provided:

```
{
  "product": [
    "name",
    "value",
    "category",
    "weight"
  ]
}
```

Our transformation will be:

```
[
  {
    "operation": "shift",
    "spec": {
      "product": {
        "*": {
          "$": "product[]"
        }
      }
    }
  }
]
```

\
What we did was select all **(\*)** the fields of the object "product", then take the name **($)** of each one of them and assign them to a list named "product".

That way we can get the name of each field and not their values.

### **#**

If used in **LHS**, it has the function of entering values ​​manually in the output JSON.

In **RHS**, on the other hand, it is applicable only to create **lists** and has the function of grouping certain content of the input JSON within the list to be created.

Usage: **LHS** and **RHS**\
Operations: shift

**LHS** example:

We have an input JSON with Product information:

```
{ 
  "product": { 
    "name": "Product Example", 
    "value": 10, 
    "weight": 25 
  } 
}
```

And we need a JSON that contains product **name**, **value**, **weight,** and **category** information:

```
{ 
  "product": { 
    "name": "Product Example", 
    "value": 10, 
    "category": "CATEG-1", 
    "weight": 25 
  } 
}
```

However, the input JSON never provides **category** information, so we need to manually add this field:

```
[
  {
    "operation": "shift",
    "spec": {
      "product": {
        "*": "product.&",
        "#DEFAULT-CATEGORY": "product.category"
      }
    }
  }
]
```

The value contained after the wildcard **#** will always be assigned to the field declared in the **RHS**, which in our case is the "category" field within the "product" object.

**RHS** Example:

We have an input JSON containing a list of Products:

```
{
  "products": [
    {
      "code": "PROD-A",
      "value": 10
    },
    {
      "code": "PROD-B",
      "value": 20
    }
  ]
}
```

And we just need to change the name of the field "**value**" to "**price**":

```
{  
  "products": [
    {
      "code": "PROD-A",
      "price": 10
    },
    {
      "code": "PROD-B",
      "price": 20
    }
  ]
}
```

Our transformation will be:

```
[
  {
    "operation": "shift",
    "spec": {
      "products": {                      <- level 2 
        "*": {                           <- level 1    
          "code": "products[#2].&",      <- level 0

          "value": "products[#2].price"  <- level 0 
        }
      }
    }
  }
]

```

The use of **#** in **RHS** involves declaring the **level** where we are seeking information. The declaration **\[#2]** represents the creation of a list **(\[ ])** and that it must **group (#)** all the information that is found **2 levels** above.

We need this declaration to guarantee the correct grouping of each product with its respective "code" and "price".

That is, in `"code": "products [# 2]. &"` we are taking the value from the "code" field and throwing it to another "code" field within a list named "products", and in `"value": "products [# 2] .price"` we take the value from the "value" field and throw it into a field named "price" within the same "products" list.

However, when creating the list "products" we will look **2 levels** above **(level of the list "products")** and the way that each item is grouped in the previous "products" list, this grouping will be maintained in the new "products" list.

### **| (pipe)**

It allows referencing multiple fields or objects of an input JSON so that, regardless of the **name** of the field or object, its value is allocated to the same **destination** in the output JSON.

Usage: **LHS**\
Operations: shift

Example:

We have an input JSON containing customer data:

```
{
  "customer": {
    "fullName": "Customer Example",
    "email": "customer-example@email.com"
  }
}
```

And we need a JSON of the following structure:

```
{
  "customer": {
    "name": "Customer Example",
    "email": "customer-example@email.com"
  }
}
```

However, in the input JSON, there is the possibility that the field `"fullName"` comes with the name `"customerName". We`need the transformation to be prepared to recognize the two possibilities:

```
[
  {
    "operation": "shift",
    "spec": {
      "customer": {
        "fullName|customerName": "customer.nome",
        "email": "customer.&"
      }
    }
  }
]

```

### Operations modify-default-beta and modify-overwrite-beta <a href="#operations-modify-default-beta-e-modify-overwrite-beta" id="operations-modify-default-beta-e-modify-overwrite-beta"></a>

As was said in the **@ wildcard** explanation, these operations allow us to dynamically reference values. While modify-default-beta will assign a value to a field if it doesn't exist, modify-overwrite-beta will overwrite any value even if the field already exists.

However, modify-overwrite-beta also allows us to apply **functions** to our JSON.

They are:

* **String**\
  toLower, toUpper, concat, join, split, substring, trim, leftPad e rightPad
* **Number**\
  min, max, abs, avg, intSum, doubleSum, longSum, intSubtract, doubleSubtract, longSubtract, divide e divideAndRound
* **Type**\
  toInteger, toDouble, toLong, toBoolean, toString, recursivelySquashNulls, squashNulls, size
* **List**\
  firstElement, lastElement, elementAt, toList, sort

Examples:

Input JSON:

```
{
  "STRING": {
    "product": "Product A",
    "company": "company a",
    "value": "100",
    "measureWithSpaces": "  10 meters "
  },
  "NUMBER": {
    "array": [ 3, 5, 2, 7, 1 ],
    "negativeValue": -100,
    "positiveValue": 50
  },
  "TYPE": {
    "value": 10.5,
    "stringBoolean": "true",
    "objectWithNull": {
      "fielWithValue": "ABC",
      "nullField": null
    }
  },
  "LIST": {
    "array": [ "c", "t", "m", "a" ],
    "stringField": "123"
  }
}
```

Transformations:

```
[
  {
    "operation": "modify-overwrite-beta",
    "spec": {
      "STRING": {
        "product": "=toLower(@(1,product))",
        "company": "=toUpper(@(1,company))",
        "product_company": "=concat(@(1,product),'_',@(1,company))",
        "joinProductCompany": "=join(' - ',@(1,product),@(1,company))",
        "splitProductCompany": "=split('[-]',@(1,joinProductCompany))",
        "substringProduct": "=substring(@(1,product),0,4)",
        "value": "=leftPad(@(1,value),6,'A')",
        "measure": "=trim(@(1,measureWithSpaces))"
      },
      "NUMBER": {
        "minArray": "=min(@(1,array))",
        "maxArray": "=max(@(1,array))",
        "absoluteValue": "=abs(@(1,negativeValue))",
        "averageArray": "=avg(@(1,array))",
        "sumArray": "=intSum(@(1,array))",
        "subtrArray": "=intSubtract(@(1,positiveValue), 20)",
        "division": "=divide(@(1,positiveValue),2)",
        "divisionRound": "=divideAndRound(3,@(1,positiveValue),3)"
      },
      "TYPE": {
        "integerValue": "=toInteger(@(1,value))",
        "booleano": "=toBoolean(@(1,stringBoolean))",
        "stringValue": "=toString(@(1,value))",
        "stringBoolean": "=size",
        "objectWithNull": "=recursivelySquashNulls"
      },
      "LIST": {
        "arrayFirstItem": "=firstElement(@(1,array))",
        "arrayLastItem": "=lastElement(@(1,array))",
        "arrayElement": "=elementAt(@(1,array),2)",
        "fieldToList": "=toList(@(1,stringField))",
        "orderedArray": "=sort(@(1,array))"
      }
    }
  }
]
```

Output JSON

```
{
  "STRING": {
    "product": "product a",
    "company": "COMPANY A",
    "value": "AAA100",
    "measureWithSpaces": "  10 meters ",
    "product_company": "product a_COMPANY A",
    "joinProductCompany": "product a - COMPANY A",
    "splitProductCompany": [
      "product a ",
      " COMPANY A"
    ],
    "substringProduct": "prod",
    "measure": "10 meters"
  },
  "NUMBER": {
    "array": [ 3, 5, 2, 7, 1 ],
    "negativeValue": -100,
    "positiveValue": 50,
    "minArray": 1,
    "maxArray": 7,
    "absoluteValue": 100,
    "averageArray": 3.6,
    "sumArray": 18,
    "subtrArray": 30,
    "division": 25,
    "divisionRound": 16.667
  },
  "TYPE": {
    "value": 10.5,
    "stringBoolean": 4,
    "objectWithNull": {
      "fielWithValue": "ABC"
    },
    "integerValue": 10,
    "booleano": true,
    "stringValue": "10.5"
  },
  "LIST": {
    "array": [
      "c",
      "t",
      "m",
      "a"
    ],
    "stringField": "123",
    "arrayFirstItem": "c",
    "arrayLastItem": "a",
    "fieldToList": [
      "123"
    ],
    "orderedArray": [ "a", "c", "m", "t" ]
  }
}
```

{% hint style="info" %}
Some functions were not included in the transformation above because they follow the same principle as others that were included, such as the **doubleSum** and **longSum** functions that are applied in the same way as **intSum**. Regarding the **recursivelySquashNulls** and **squashNulls** functions, both are applicable only to **objects** and **lists** and serve to remove fields with null values, while **recursivelySquashNulls** will look at all levels below the object or list, **squashNulls** will look just **1** level below.
{% endhint %}

The modify-overwrite-beta has its execution in **cascade**, that is, each new transformation is impacted by the previous transformations.

To understand this cascading behavior, let's take a snippet of the input JSON and the above transformations:

```
//input JSON
"STRING": {
   "product": "PRODUCT A",
   "company": "company a",
   "value": "100",

//Transformation
"STRING": {
   "product": "=toLower(@(1,product))",
   "company": "=toUpper(@(1,company))",
   "product_company": "=concat(@(1,product),'_',@(1,company))",
```

In `"product": "= toLower (@ (1, product))`" we change the value from "product" to **lower case** and in `"company": "= toUpper (@ (1, company))"`, we change the value of " company to **upper case**.&#x20;

So the moment we do `"product_company": "= concat (@ (1, product), '_', @ (1, company))"`, we are using the values ​​of "product" and "company" already transformed and not their original values ​​contained in the input JSON and with that we will have `"product_company": "product a_Company A"`.

For a more technical reading about JOLT, [access JOLT GitHub documentation](https://github.com/bazaarvoice/jolt).\
