---
description: >-
  Understand Double Braces functions in the Digibee iPaaS and how to use them.
  This page covers Utilities functions and how they let users create diverse
  operations.
---

# Utilities Functions

The functions were created to:

* speed up the creation of your integrations even more
* decrease the complexity of your pipelines
* simplify data conversions and transformations during the flow of your pipelines

The utilities functions make diverse operations, which don't fit any of the other categories, and are available for components that support Double Braces expressions. To know how to provide information to the components using this resource, click [here](./).

### BASEDECODE <a href="#basedecode" id="basedecode"></a>

This function in Double Braces decodes a string in a base64 format.

**Syntax**

BASEDECODE(value:string, \[charset:string - optional])

* **value:** string to be decoded
* **charset:** charset for the decodification (standard = UTF-8) (optional)

Let's say you need to decode a string. You can do the following:

```
{
"test": {{ BASEDECODE("eHB0bw==", "UTF-8") }}
}
```

The expected result will be:

```
{
"test": "xpto"
}
```

### BASEENCODE <a href="#baseencode" id="baseencode"></a>

This function in Double Braces codes a string in a base64 format.

**Syntax**

BASEENCODE(value:string, \[charset:string - optional])

* **value:** string to be coded
* **charset:** charset for the codification (standard = UTF-8) (optional)

Let's say you need to code a string. You can do the following:

```
{
"test": {{ BASEENCODE("xpto", "UTF-8") }}
}
```

The expected result will be:

```
{
"test": "eHB0bw=="
}
```

### **BASEURLDECODE**

This function in Double Braces decodes a string in a Base64 format in the standard usage for URL.

**Syntax**

BASEDECODE(value:string, \[charset:string - optional])

* **value**: _string_ to be decoded
* **charset:** charset for decoding (default = UTF-8) (optional)

Let’s say you need to decode a string. You can do the following:

```
{
 "test": {{ BASEURLDECODE("eHB0bw", "UTF-8") }}
}

```

The result will be:

```
{
 "test": "xpto"
}

```

### **BASEURLENCODE**

This function in Double Braces encodes a string in a Base64 format for use in URL’s.

**Syntax**

BASEENCODE(value:string, \[charset:string - optional])

* **value:** string to be encoded
* **charset**: charset for encoding (default = UTF-8) (optional)



Let's say you need to encode a string. You can do the following:&#x20;

```
{
 "test": {{ BASEURLENCODE("xpto", "UTF-8") }}
}

```

The result will be:

```
{
 "test": "eHB0bw"
}

```

### **UUID** <a href="#uuid" id="uuid"></a>

This function in Double Braces generates a unique universal identifier - the number of 128 bits is used to identify information in systems.

**Syntax**

UUID()

Let's say you need to generate a unique identifier. You can do the following:

```
{
"test": {{ UUID() }}
}
```

The expected result will be:

```
{
"test": "4caad555-09b5-479c-98b4-ac72ffbb486c"
}
```

### TOBOOLEAN <a href="#h_bea3588024" id="h_bea3588024"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function allows you to convert a string value to boolean.

**Syntax**

TOBOOLEAN(value)

Let's say you need to convert the values below to boolean:

```
{
"string": "false",
"stringUpperCase": "TRUE",
"boolean": true,
"integer": 1,
"nullValue": null,
"object": {
"string": "abc"
}
}
```

Converting the values:

```
{
"string": {{ TOBOOLEAN(message.string) }},
"stringUpperCase": {{ TOBOOLEAN(message.stringUpperCase) }},
"boolean": {{ TOBOOLEAN(message.boolean) }},
"integer": {{ TOBOOLEAN(message.integer) }},
"nullValue": {{ TOBOOLEAN(message.nullValue) }},
"object": {{ TOBOOLEAN(message.object) }}
}
```

The result will be:

```
{
"string": false,
"stringUpperCase": true,
"boolean": true,
"integer": false,
"nullValue": false,
"object": false
}
```

If the function is applied in strings with different values of "true", "false", "TRUE" and "FALSE", numerical fields, null fields, objects and arrays, the function will always return the result _false_.

### SIZE <a href="#h_2ff9b78be9" id="h_2ff9b78be9"></a>

This function in Double Braces allows the size of _strings_, _arrays_ and _objects_ to be obtained.

**Syntax**

SIZE(value, \[throwErrorOnUnexpectedType:boolean - optional])

* **value:** value to be checked the size
* **throwErrorOnUnexpectedType:** indicates whether an exception will be returned when the _value_ parameter isn’t expected by the function. If not informed, a _true_ value will be assumed and, when a _false_ value is informed, the function's return will be _null_.

Let's say you need to get the size of a text from a _comments_ property contained in your payload. You can use the following snippet in the _**JSON Generator**_ component:

```
{
"commentsSize": {{ SIZE(message.comments) }}
}
```

The result will be a numeric value corresponding to the number of characters contained in the text:

```
{
"commentsSize": 1000
}
```

Now imagine there’s a JSON object in the following structure:

```
{
"body":{
"field1": "test",
"field2": {
"field2.1": "testing"
}
}
}
```

The size of this object must be checked. If using _**JSON Generator**_ again, the following snippet must be configured:

```
{
"bodySize": {{ SIZE(message.body) }}
}
```

The result will be the amount of properties contained in the body object:

```
{
"bodySize": 2
}
```

In this case, the function only considers properties that directly belong to the _body_ object and doesn’t consider nested properties.

You can also check the size of an array:

```
{
"array": [
10,20,30
]
}
```

Considering the array above, use _**JSON Generator**_ one more time to configure the following snippet:

```
{
"arraySize": {{ SIZE(message.array) }}
}
```

When executing the function, the result will represent the number of elements contained in the array:

```
{
"arraySize": 3
}
```

The SIZE function expects _string_, _array_ and _object_ value types. When the value doesn’t match this requirement, an exception will be thrown. However, it’s also possible to configure the function not to throw an exception and simply return _null_. If that’s the case, just configure the second parameter of the function with the value _false_.

Consider the following payload:

```
{
"elements": 13
}
```

And the following _**JSON Generator**_ configuration:

```
{
"elementsSize": {{ SIZE(message.elements, false) }}
}
```

The result of the function execution will be:

```
{
"elementsSize": null
}
```

That way, no exception will be thrown and some verification logic can be adopted in your integration flow.

### URIDECODE

\
This function allows you to decode a URI (string).

**Syntax**

URIDECODE( value:string, \[charset:string - optional ] )

* **uri**: string to be decoded
* **charset**: charset for the decodification ( standard = UTF-8 ) ( opcional )

Let’s say you need to decode a URI. You can do the following:

```
{
 "test": {{ URIDECODE("http%3A%2F%2Flocalhost%3A8080", "UTF-8") }}
}
```

The result will be:

```
{
 "test": "http://localhost:8080"
}
```

### URIENCODE

This function allows you to encode a URI (string).

**Syntax**

URIENCODE( value:string, \[charset:string - optional ] )

* **uri**: string to be encoded
* **charset**: charset for the codification ( standard = UTF-8 ) ( opcional )

Let’s say that you need to encode a URI. You can do the following:

```
{
 "test": {{ URIENCODE("http://localhost:8080", "UTF-8") }}
}

```

The result will be:

```
{
 "test": "http%3A%2F%2Flocalhost%3A8080"
}
```

### Other functions

You can also read about these functions:

* [comparison](comparison-functions.md)
* [numerical](numerical-functions.md)
* [conditional](conditional-functions.md)
* [date](date-functions.md)
* [file](file-functions.md)
* [JSON](json-functions.md)
* [string](broken-reference)
* [math](math-functions.md)
