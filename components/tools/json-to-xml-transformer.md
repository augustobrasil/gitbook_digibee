---
description: >-
  Discover more about the JSON to XML Transformer component and how to use it on
  the Digibee Integration Platform.
---

# JSON to XML Transformer

**L Transformer** generates an XML based on a JSON received in its input message.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>JSON Field Path</strong></td><td>JSON as path of the string field in dotted notation.</td><td>payload</td><td>String</td></tr><tr><td><strong>Root Element Name</strong></td><td>Root element of the generated XML.</td><td>body</td><td>String</td></tr><tr><td><strong>Preserve Original</strong></td><td>If activated, the option preserves the original fields.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Header</strong></td><td>XML header to be included before the XML payload.</td><td>&#x3C;?xml version='1.0' encoding='UTF-8' standalone='no' ?></td><td>String</td></tr></tbody></table>

## Messages flow

### Input

The component waits for a message in any format, but will look for a path inside the **JSON Field Path** configuration property.

These are some valid input examples:

#### Example 1

```
{
    "orders": {
     "order": [
       {
         "a": 1,
 "b": 1
       },
       {
         "a": 2,
         "b": 2
       },
       {
         "a": 3,
         "b": 3
       }
   ]
   }
 }
```

#### Example 2

```
{
 "payload": {
   "test": {
     "a": 1,
     "b": 1
   }
 }
}
```

### Output

The structure will be equivalent to the one in the input, but with another model and another template representation as string. In case of error, the "error" property will be created at the same level as the original property.

The JSON dotted notation will look for the root element that is being processed by the pipeline and cross it according to the specifications given in the **JSON Field Path** property.

#### Example

In a **JSON Field Path** representation containing a.b.c.d, "a" will be searched in the root element. Afterwards, it will be "b", then "c" and finally "d". If an array is found during the cross, then the algorithm will generate a cross path for each element of the array. The algorithm replaces all the occurrences of the defined path in **JSON Field Path**.

**Without error**

```
{
"XYZ": "TRANSFORMED TEMPLATE"
"_body": {}
}
```

* **\_body:** if the option **Preserve Original** is enabled, the property will be shown in the output containing the input JSON.
* **ZYX:** dynamic name based on the **JSON Field Path** configuration in the component properties.

**With error**

```
{
 "body": null,
 "_error": "Can not construct instance of java.util.LinkedHashMap: no String-argument constructor/factory method to deserialize from String value ('')\n at [Source: N/A; line: -1, column: -1]",
 "_body": ""
}
```

* **\_body:** if the option **Preserve Original** is enabled, the property will be shown in the output containing the input JSON.
* **\_error:** description of the error occurred in the deployment.
* **XYZ:** dynamic name based on the **JSON Field Path** configuration in the component properties.

## JSON to XML Transformer in action

### Example 1

* **JSON Field Path:** orders
* **Root Element Name:** doc
* **Preserve Original:** enabled
* **Header:** \<?xml version='1.0' encoding='UTF-8' standalone='no' ?>

#### Input

```
{
    "orders": {
     "order": [
       {
         "a": 1,
         "b": 1
       },
       {
         "a": 2,
         "b": 2
       },
       {
         "a": 3,
         "b": 3
       }
     ]
   }
}
```

#### Output

```
{
 "orders": "<?xml version='1.0' encoding='UTF-8' standalone='no' ?><doc><order><a>1</a><b>1</b></order><order><a>2</a><b>2</b></order><order><a>3</a><b>3</b></order></doc>",
 "_orders": {
   "order": [
     {
       "a": 1,
       "b": 1
     },
     {
       "a": 2,
       "b": 2
     },
     {
       "a": 3,
       "b": 3
    }
   ]
 }
}
```

### Example 2

* **JSON Field Path:** payload
* **Root Element Name:** xyz
* **Preserve Original:** disabled

#### Input

```
{
 "payload": {
   "test": {
     "a": 1,
     "b": 1
   }
 }
}
```

#### Output

```
{ 
   "payload": "<xyz><test><a>1</a><b>1</b></test></xyz>"
}
```

\
