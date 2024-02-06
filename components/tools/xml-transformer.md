---
description: >-
  Discover more about the XML Transformer component and how to use it on the
  Digibee Integration Platform.
---

# XML Transformer

**XML Transformer** transforms a JSON object into an XML string.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Output JSON Property</strong></td><td>Defines the value of the JSON attribute that will receive the XML in the output.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Generate Root Element On XML</strong></td><td>Defines the value of the root element to be added in the generated XML.</td><td>N/A</td><td>String</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input

A JSON object is expected to be converted, provided that the component's parameters are correctly filled in.

### Output

An XML string that is the result of the conversion of the input JSON object.

## XML Transformer in Action

### Input <a href="#input" id="input"></a>

Considering the configurations:

* **Output JSON Property:** output
* **Generate Root Element On XML:** customers

When the following message is received:

```
{
    "customer": {
        "id":1,
        "name":"Paul"
    }
}
```

### Output <a href="#output" id="output"></a>

The following output structure is generated:

```
{
   "output": "<?xml version=\"1.0\" encoding=\"UTF-8\"?><customers><customer>
<id>1</id><name>Leandro</name></customer></customers>"
}
```

\
