---
description: >-
  Learn about Double Braces functions in the Digibee iPaaS and how to use them.
  This page covers how JSON functions allow users to make operations in JSON
  objects.
---

# JSON Functions

The functions were created to:

* speed up the creation of your integrations even more
* decrease the complexity of your pipelines
* simplify data conversions and transformations during the flow of your pipelines

The JSON functions make operations in JSON objects and are available for components that support Double Braces expressions. To know how to provide information to the components using this resource, click [here](./).

## JSONPATH <a href="#jsonpath" id="jsonpath"></a>

This function in Double Braces returns parts of a determined document according to the sent expression.

### **Syntax**

```
JSONPATH(value:string, expression:string)
```

● **value:** string

● **expression:** string containing the expression to be recovered

Let's say you need to obtain part of a document by using expressions. You can do the following:

```
{
"test": {{ JSONPATH ({"store":{"book":[{"category":"reference","author":"Nigel Rees","title":"Sayings of the Century","price":8.95},{"category":"fiction","author":"Evelyn Waugh","title":"Sword of Honour","price":12.99},{"category":"fiction","author":"Herman Melville","title":"Moby Dick","isbn":"0-553-21311-3","price":8.99},{"category":"fiction","author":"J. R. R. Tolkien","title":"The Lord of the Rings","isbn":"0-395-19395-8","price":22.99}],"bicycle":{"color":"red","price":19.95}},"expensive":10}, "$.store.book[?(@.price > 10)]") }}
"test2": {{ JSONPATH (["aa","ss","","e"],"$.[0]" ) }}
}
```

The expected result will be:

```
{
"test": [{"category":"fiction","author":"Evelyn Waugh","title":"Sword of Honour","price":12.99},{"category":"fiction","author":"J. R. R. Tolkien","title":"The Lord of the Rings","isbn":"0-395-19395-8","price":22.99}]
"test2": "aa"
}
```

It's possible to use the functions that _**JSONPATH**_ internally provides, such as:

* min()
* max()
* avg()
* stddev()
* length

### **Example usage**

Let's say that an input array is received:

```
{"numbers": [1,33,56,77.8,66,10475,665464,1,0.01]}
```

And that you want to use the functions described above in the “expression” field:

```
{
"min": {{ JSONPATH(message.numbers, "$.min()") }},
"max": {{ JSONPATH(message.numbers, "$.max()") }},
"avg": {{ JSONPATH(message.numbers, "$.avg()") }},
"stddev": {{ JSONPATH(message.numbers, "$.stddev()") }},
"length": {{ JSONPATH(message.numbers, "$.length()") }}
}
```

The result will be:

```
{
"min": 0.01,
"max": 665464.0
"avg": 75130.42333333334,
"stddev": 208739.83034832493,
"length": 9
}
```

## TOJSON <a href="#tojson" id="tojson"></a>

This function in Double Braces returns the JSON value from the received object.

### **Syntax**

```
TOJSON(value:string)
```

● **value:** string

Let's say you need to obtain the values of a JSON object. You can do the following:

```
{
"test": {{ TOJSON("aaS2fdeS") }}
"test2": {{ TOJSON(111) }}
"test3": {{ TOJSON("false") }}
"test4": {{ TOJSON([{"c":123}]) }}
"test5": {{ TOJSON({"a":123,"array":[1,2,3]}) }}
"test6": {{ TOJSON("{\"name\":\"John\",\"age\":31,\"city\":\"New York\"}") }}
"test7": {{ TOJSON(null) }}
}
```

The expected result will be:

```
{
"test": "aaS2fdeS"
"test2": 111
"test3": false
"test4": [{"c":123}]
"test5": {"a":123,"array":[1,2,3]}
"test6": {"name":"John","age":31,"city":"New York"}
"test2": null
}
```

## UNESCAPEJSON <a href="#unescapejson" id="unescapejson"></a>

This function in Double Braces returns a JSON by removing the found escapes in the provided value.

### **Syntax**

```
UNESCAPE(value:string)
```

● **value:** string

Let's say you need to remove escape characters. You can do the following:

```
{
"test": {{ UNESCAPE ("{\\\"name\\\":\\\"John\\\",\\\"age\\\":31,\\\"city\\\":\\\"New York\\\"}") }}
}
```

The expected result will be:

```
{
"test": "{\"name\":\"John\",\"age\":31,\"city\":\"New York\"}"
}
```

## GETELEMENTAT <a href="#h_add3ccf5f4" id="h_add3ccf5f4"></a>

This function allows you to capture a specific element from an array.

### **Syntax**

```
GETELEMENTAT(array, index)
```

Let's say you need to capture the first element of the array below:

```
{
"data": [
{
"field": "value-1"
},
{
"field": "value-2"
},
{
"field": "value-3"
}
]
}
```

Capturing the element:

```
{
"element": {{ GETELEMENTAT(message.data, 0) }}
}
```

The result will be:

```
{
"element": {
"field": "value-1"
}
}
```

## LASTELEMENT <a href="#h_60797aa91b" id="h_60797aa91b"></a>

This function allows you to capture the last element from an array.

### **Syntax**

```
LASTELEMENT(array, index)
```

Let's say you need to capture the last element of the array below:

```
{
"data": [
{
"field": "value-1"
},
{
"field": "value-2"
},
{
"field": "value-3"
}
]
}
```

Capturing the element:

```
{
"element": {{ LASTELEMENT(message.data) }}
}
```

The result will be:

```
{
"element": {
"field": "value-3"
}
}
```

If the function receives an empty array, a **null** value will be returned.

## **REMOVEAT** <a href="#h_594c1b8c6d" id="h_594c1b8c6d"></a>

This function allows you to remove a specific element from an array.

### **Syntax**

```
REMOVEAT(array, index)
```

Let's say you need to remove the second element of the array below:

<pre><code><strong>{"data": [
</strong>{
"field": "value-1"
},
{
"field": "value-2"
},
{
"field": "value-3"
}
]
}
</code></pre>

Removing the element:

```
{"data": {{ REMOVEAT(message.data, 1) }}}
```

The result will be:

```
{
"data": [
{
"field": "value-1"
},
{
"field": "value-3"
}
]
}
```

If the function receives an inexistent index, the original array will be returned with no changes.

## PUSH <a href="#h_acc0d544be" id="h_acc0d544be"></a>

This function allows you to add an element at the end of an array.

**Syntax**

```
PUSH(array, element)
```

Let's say you need to insert a new element in the following array :

```
{
"element": {
"example": "123"
},
"array": [
{
"example": "ABC"
},
{
"example": "FFF"
}
]
}
```

Inserting a new element :

```
{
"array": {{ PUSH(message.array, message.element) }}
}
```

The result will be:

```
{
"array": [
{
"example": "ABC"
},
{
"example": "FFF"
},
{
"example": "123"
}
]
}
```

If a nonexistent or null element is added, the value _null_ will be inserted at the end of the array.

## POP <a href="#h_89e4410b68" id="h_89e4410b68"></a>

This function allows you to remove the last element from an array. The result will be the element removed and the remaining array.

### **Syntax**

```
POP(array)
```

Let's say you need to remove the last element from the following array:

```
{
"array": [
{
"id": "ABC"
},
{
"id": "FFF"
},
{
"id": "123"
}
]
}
```

Removing the last element :

```
{"data": {{ POP(message.array) }}}
```

The result will be:

```
{
"data": {
"array": [
{
"id": "ABC"
},
{
"id": "FFF"
}
],
"element": {
"id": "123"
}
}
}
```

If the array is empty, the result will be the same empty array.

## NEWEMPTYOBJECT <a href="#h_acc0d544be" id="h_acc0d544be"></a>

This function allows you to create a new empty object.

### **Syntax**

```
NEWEMPTYOBJECT()
```

Let's say you need to create a new empty object:

```
{"data": {}}
```

Creating:

```
{"data": {{ NEWEMPTYOBJECT() }}}
```

The result will be:

```
{"data": {}}
```

## NEWEMPTYARRAY <a href="#h_1b40411a35" id="h_1b40411a35"></a>

This function allows you to create a new empty array.

### **Syntax**

```
NEWEMPTYARRAY()
```

Let's say you need to create a new empty array:

```
{"data": []}
```

Creating:

```
{"data": {{ NEWEMPTYARRAY() }}}
```

The result will be:

```
{"data": []}
```

## **CARDINALITYONE**

The function allows a cardinality of n:1 to be applied to any informed structure, where regardless of the number of elements in the input, the output will always be 1 element.

### **Syntax**

```
CARDINALITYONE(data)
```

Let's say you need to apply a _n:1_ cardinality on each element from the JSON below:

```
{
"arrayObject": [
{
"id": "PROD-123",
"type": "Product"
},
{
"id": "CUST-456",
"type": "Customer"
}
],
"arrayNumber": [ 23, 790 ],
"emptyArray": [],
"object": {
"test": "value"
},
"singleNumber": 500,
"singleString": "CARDINALITY",
"nullValue": null,
"emptyObject": {}
}
```

Applying the function:

```
{
"arrayObject": {{ CARDINALITYONE(message.arrayObject) }},
"arrayNumber": {{ CARDINALITYONE(message.arrayNumber) }},
"emptyArray": {{ CARDINALITYONE(message.emptyArray) }},
"object": {{ CARDINALITYONE(message.object) }},
"singleNumber": {{ CARDINALITYONE(message.singleNumber) }},
"singleNumber": {{ CARDINALITYONE(message.singleNumber) }},
"singleString": {{ CARDINALITYONE(message.singleString) }},
"emptyObject": {{ CARDINALITYONE(message.emptyObject) }}
}
```

The result will be:

```
{
"arrayObject": {
"id": "PROD-123",
"type": "Product"
},
"arrayNumber": 23,
"emptyArray": null,
"object": {
"test": "value"
},
"singleNumber": 500,
"singleString": "CARDINALITY",
"emptyObject": {}
}
```

## **CARDINALITYMANY**

This function allows an output to be standardized by a multiple cardinality. That means, when an input of an array has n elements, its output will be an array of n elements, and when an input has a sole object, its output will be an array of this same object.

### **Syntax**

```
CARDINALITYMANY(data)
```

Let's say you need to apply a _m:n_ cardinality to each element from the JSON below:

```
{
"arrayObject": [
{
"id": "PROD-123",
"type": "Product"
},
{
"id": "CUST-456",
"type": "Customer"
}
],
"arrayNumber": [ 23, 790 ],
"emptyArray": [],
"object": {
"test": "value"
},
"singleNumber": 500,
"singleString": "CARDINALITY",
"nullValue": null,
"emptyObject": {}
}
```

Applying the function:l

```
{
"arrayObject": {{ CARDINALITYMANY(message.arrayObject) }},
"arrayNumber": {{ CARDINALITYMANY(message.arrayNumber) }},
"emptyArray": {{ CARDINALITYMANY(message.emptyArray) }},
"object": {{ CARDINALITYMANY(message.object) }},
"singleNumber": {{ CARDINALITYMANY(message.singleNumber) }},
"singleNumber": {{ CARDINALITYMANY(message.singleNumber) }},
"singleString": {{ CARDINALITYMANY(message.singleString) }},
"emptyObject": {{ CARDINALITYMANY(message.emptyObject) }}
}
```

The result will be:

```
{
"arrayObject": [
{
"id": "PROD-123",
"type": "Product"
},
{
"id": "CUST-456",
"type": "Customer"
}
],
"arrayNumber": [ 23, 790 ],
"emptyArray": [],
"object": [ {
"test": "value"
} ],
"singleNumber": [ 500 ],
"singleString": [ "CARDINALITY" ],
"emptyObject": [ {} ]
}
```

You can also read about these functions:

* [comparison](comparison-functions.md)
* [numerical](numerical-functions.md)
* [conditional](conditional-functions.md)
* [date](date-functions.md)
* [file](file-functions.md)
* [string](broken-reference)
* [utilities](double-braces-utilities-functions.md)
* [math](math-functions.md)
