---
description: Learn more about the component and how to use it.
---

# JSLT

The **JSLT** component allows manipulation of a JSON using JSLT, a language for JSON processing and querying. For more information, [see the official documentation on Github](https://github.com/schibsted/jslt).

The component is useful to perform several actions, such as:

* modify the structure of a JSON and keep its values;
* add, extract and remove data from a JSON;
* sort the structure of a JSON;
* modify the values contained in a JSON through functions, such as text manipulation, mathematical calculations, conversions between data types, among others;
* access and manipulate data from arrays.

Take a look at the configuration parameters of the component:

* **Payload:** the JSON content to be manipulated. This field supports[ Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces).
* **JSLT:** the JSLT declaration to be executed.
* **Fail On Error:** if the option is active, the execution of the pipeline with error will be interrupted. Otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.

{% hint style="info" %}
**Important:** the component does not support JSLT import statements.
{% endhint %}

## JSLT expression examples

### Simple data transpose

**Payload**

```
{
  "id" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "type" : "component",
  "prefix": "jslt",
  "myString": "test",
  "myArray": [ 1, 2, 3, 4],
  "boolean": true
}

```

**JSLT**

```
{
  "uuid": .id,
  "obj": {
   "key-1": .type,
   "key-2": .prefix
  },
  * - myString, myArray, id: .
}

```

**Output**

```
{
  "uuid" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "obj" : {
    "key-1" : "component",
    "key-2" : "jslt"
  },
  "type" : "component",
  "prefix" : "jslt",
  "boolean" : true
}

```

### **JSLT Native functions**

{% hint style="info" %}
**Important:** the example below represents some of the available JSLT native functions. For more information about it and the complete list of functions, [visit the Github documentation](https://github.com/schibsted/jslt/blob/master/functions.md).
{% endhint %}

**Payload**

```
{
  "id" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "type" : "component",
  "prefix": "jslt",
  "myString": "TEST",
  "myArray": [ 1, 2, 3, 4],
  "boolean": true
}

```

**JSLT**

```
{
  "uuid": split(.id, "-"),
  "obj": {
   "key-1": uppercase(.type),
   "key-2": join(.myArray, lowercase(.myString))
  },
  * : .
}

```

**Output**

```
{
  "uuid" : [ "w23q7ca1", "8729", "24923", "922b", "1c0517ddffjf1" ],
  "obj" : {
    "key-1" : "COMPONENT",
    "key-2" : "1test2test3test4"
  },
  "id" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "type" : "component",
  "prefix" : "jslt",
  "myString" : "TEST",
  "myArray" : [ 1, 2, 3, 4 ],
  "boolean" : true
}

```

### **Variables and custom functions**

**Payload**

```
{
  "id" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "s1": "jslt",
  "s2": "component"
}

```

**JSLT**

```
let splitted = split(.id, "-")
let size = size($splitted)

def concat(s1, s2)
  if ($s1 != null)
    $s1 + "___" + $s2
  else
    ""

{
  "variables": $splitted,
  "size": $size,
  "customFunction": concat(.s1, .s2)
}

```

**Output**

```
{
  "variables": [
    "w23q7ca1",
    "8729",
    "24923",
    "922b",
    "1c0517ddffjf1"
  ],
  "size": 5,
  "customFunction": "jslt___component"
}

```

### **If and For Operators**

**Payload**

```
{
  "id" : "w23q7ca1-8729-24923-922b-1c0517ddffjf1",
  "status": true
}

```

**JSLT**

```
let aux = split(.id, "-")

def concat(string1, string2)
   $string1 + "-" + $string2

{
  "forResult": [for ($aux) concat("test", .)],
  "ifResult": if (.status)
                 size(.id)
              else
                 0
}

```

**Output**

{% code overflow="wrap" %}
```
{
  "forResult" : [ "test-w23q7ca1", "test-8729", "test-24923", "test-922b", "test-1c0517ddffjf1" ],
  "ifResult" : 38
}

```
{% endcode %}
