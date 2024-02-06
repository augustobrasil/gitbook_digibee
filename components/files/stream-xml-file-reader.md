---
description: >-
  The Documentation Portal provides guides on all options for components on the
  Digibee Integration Platform. This article covers Stream XML File Reader.
---

# Stream XML File Reader

**Stream XML File Reader** performs the reading of a local XML file and, based on the configuration of a desired node and context fields, delivers a XML structure and context properties for each node found and triggers subpipelines to process each message. The component should be used for large files when parts of the whole need to be read efficiently.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="248">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>File name</strong> <code>(DB)</code></td><td>File name or full file path (i.e. tmp/processed/file.txt) of the local XML file.</td><td>data.xml</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Name of the character code for the file reading.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Node Path</strong> </td><td>Path of the desired node to stream from the XML file (e.g.: //root/level1/level2/desirednode).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Context Paths</strong></td><td>Define tag paths that represent fields adding context to the desired node (e.g.: //root/node1/code,//root/node2/description).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Ignore Paths</strong></td><td>Define paths that will be ignored and not returned into the desired node (e.g.: //root/node1/email,//root/node2/city).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Ignore Nested Child Nodes</strong></td><td>If active, nested child nodes (nodes not direct children of the desired node) will be ignored. In this case, the node at the same level as the desired node will be returned, but nodes below it will be ignored.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Element Identifier</strong></td><td>Attribute that will be sent in case of errors.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Occurs in parallel with loop execution.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>When active, this parameter suspends pipeline execution in the case of a severe occurrence in the iteration structure, preventing its completion. The activation of the "Fail On Error" parameter is not related to errors occurring in components used to construct subpipelines (onProcess and onException).</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Remove whitespaces</strong></td><td>If the option is active, whitespaces at the beginning/end of all XML character values are removed.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Coalesce</strong></td><td>If the option is active, XML character values are read as single strings.</td><td>N/A</td><td>Boolean</td></tr></tbody></table>

## Recommended use for Remove whitespaces and Coalesce

Be careful not to compromise the integrity of the data when activating the **Remove whitespaces** option. When streaming files within large character values, the component processes these values during many steps before consolidating them in a single value, and whitespaces removal is applied during each of these steps.

One way to safely use **Remove whitespaces** is to combine it with the **Coalesce** option. This ensures that the character values inside XML tags will be read at once, without breaking in several parts at first. However, keep in mind that when the **Coalesce** parameter is enabled, it may demand more pipeline resources when reading huge chunks of data at once.

## Messages flow <a href="#h_2cf37c23dc" id="h_2cf37c23dc"></a>

### Input <a href="#h_273a73a6f0" id="h_273a73a6f0"></a>

No specific input message is expected, but the existence of a XML file in the pipeline local directory and the filling of the **File Name** and **Node Path** fields for the file processing.

### Output <a href="#h_e9b66e2893" id="h_e9b66e2893"></a>

```
{
"total": 0,
"success": 0,
"failed": 0
}
```

* **total:** total number of processed lines.
* **success:** total number of successfully processed lines.
* **failed:** total number of lines whose process failed.

{% hint style="info" %}
**Important:** when the lines are correctly processed, their respective subpipelines return { "success": true } for each of them.
{% endhint %}

The component throws an exception if **File Name** doesn’t exist or can’t be read.

The file manipulation inside a pipeline occurs in a protected way. All the files can be accessed with a temporary directory only, where each pipeline key gives access to its own files set.

**Stream XML File Reader** makes batch processing. To better understand the concept, read the [article about Batch processing](https://docs.digibee.com/documentation/tutorials-and-best-practices/batch-processing).

## Stream XML File Reader in Action <a href="#h_bbd1c5a904" id="h_bbd1c5a904"></a>

The following scenarios are based on the following XML file:

* **File name:** file.xml
* **Content:**

```
<?xml version="1.0" encoding="UTF-8"?>
<root>
<list-info qty="4">products</list-info>
<products>
<product>
<price>20.75</price>
<product>Chair</product>
<tags>
<element>NEW</element>
<element>FURNITURE</element>
</tags>
</product>
<product>
<price>399.99</price>
<product>TV</product>
<tags>
<element>NEW</element>
<element>FURNITURE</element>
</tags>
</product>
<product>
<price>100</price>
<product>Couch</product>
<tags>
<element>NEW</element>
<element>FURNITURE</element>
</tags>
</product>
<product>
<price>78.99</price>
<product>Table</product>
<tags>
<element>NEW</element>
<element>FURNITURE</element>
</tags>
</product>
</products>
</root>
```

### Streaming the file informing the desired node <a href="#h_fde9ff01b0" id="h_fde9ff01b0"></a>

#### **Input**

* **File Name:** file.xml
* **Node Path:** //root/products/product

#### **Output**

```
{
"total": 4,
"success": 4,
"failed": 0
}
```

Each element identified by the desired node path will be processed independently:

* **First subflow:**

{% code overflow="wrap" %}
```
{
"node":"<product><price>20.75</price><product>Chair</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Second subflow:**

{% code overflow="wrap" %}
```
{
"node":"<product><price>399.99</price><product>TV</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Third subflow:**

{% code overflow="wrap" %}
```
{
"node":"<product><price>100</price><product>Couch</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Forth subflow:**

{% code overflow="wrap" %}
```
{
"node":"<product><price>78.99</price><product>Table</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

### Streaming the file informing the desired node and context fields <a href="#h_525528055c" id="h_525528055c"></a>

#### **Input**

* **File Name:** file.xml
* **Node Path:** //root/products/product
* **Context Paths:** //root/list-info

#### **Output**

```
{
"total": 4,
"success": 4,
"failed": 0
}
```

Each element identified by the desired node path will be processed independently:

* **First subflow:**

{% code overflow="wrap" %}
```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>20.75</price><product>Chair</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Second subflow:**

{% code overflow="wrap" %}
```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>399.99</price><product>TV</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Third subflow:**

{% code overflow="wrap" %}
```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>100</price><product>Couch</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

* **Forth subflow:**

{% code overflow="wrap" %}
```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>78.99</price><product>Table</product><tags><element>NEW</element><element>FURNITURE</element></tags></product>"
}
```
{% endcode %}

### **Streaming the file informing the desired node, context fields and nodes to be ignored** <a href="#h_bc3121d833" id="h_bc3121d833"></a>

#### **Input**

* **File Name:** file.xml
* **Node Path:** //root/products/product
* **Context Paths:** //root/list-info
* **Ignore Paths:** //root/products/product/tags

#### **Output**

```
{
"total": 4,
"success": 4,
"failed": 0
}
```

Each element identified by the desired node path will be processed independently:

* **First subflow:**

```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>20.75</price><product>Chair</product></product>"
}
```

* **Second subflow:**

```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>399.99</price><product>TV</product></product>"
}
```

* **Third subflow:**

```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>100</price><product>Couch</product></product>"
}

```

* **Forth subflow:**

```
{
"context": {
"root": {
"list-info": {
"attributes": {
"qty": "4"
},
"value": "products"
}
}
},
"node": "<product><price>78.99</price><product>Table</product></product>"
}
```

### Streaming the file informing the desired node and ignoring nested child nodes <a href="#h_657cfa45c9" id="h_657cfa45c9"></a>

#### **Input**

* **File Name:** file.xml
* **Node Path:** //root/products/product
* **Ignore Nested Child Nodes:** active

#### **Output**

```
{
"total": 4,
"success": 4,
"failed": 0
}
```

Each element identified by the desired node path will be processed independently:

* **First subflow:**

{% code overflow="wrap" %}
```
{
"data": {
"node": "<product><price>20.75</price><product>Chair</product><tags></tags></product>"
},
"success": true
}
```
{% endcode %}

* **Second subflow:**

```
{
"node": "<product><price>399.99</price><product>TV</product><tags></tags></product>"
}
```

* **Third subflow:**

```
{
"node": "<product><price>100</price><product>Couch</product><tags></tags></product>"
}
```

* **Forth subflow:**

{% code overflow="wrap" %}
```
{
"node": "<product><price>78.99</price><product>Table</product><tags></tags></product>"
}
```
{% endcode %}

## Additional information <a href="#h_b541b1ea6c" id="h_b541b1ea6c"></a>

**Stream XML File Reader** uses an event reading mechanism, through which each type of data present in the file is an event to be processed. With that, there are some types of events that are not covered during the file stream. These are they:

* PROCESSING INSTRUCTION
* START DOCUMENT
* END DOCUMENT
* SPACE
* ENTITY REFERENCE
* ENTITY DECLARATION
* DTD
* NOTATION DECLARATION
