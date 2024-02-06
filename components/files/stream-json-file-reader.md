---
description: >-
  Discover more about the Stream JSON File Reader component and how to use it on
  the Digibee Integration Platform.
---

# Stream JSON File Reader

**Stream JSON File Reader** reads a local JSON file, applies a JSON Path expression, returns a JSON structure according to the defined expressions and triggers subpipelines to process each message. The component is to be used for large files.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="307">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>File name or full file path (i.e. tmp/processed/file.json) of the local JSON file.</td><td>data.json</td><td>String</td></tr><tr><td><strong>JSON Path</strong></td><td>JSON Path expression that determines how the JSON file stream reading will occur.</td><td>$</td><td>String</td></tr><tr><td><strong>Element Identifier</strong></td><td>Attribute that will be sent in case of errors.</td><td>data</td><td>String</td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Occurs in parallel with the loop execution.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td><p>When active, this parameter suspends the pipeline execution if there’s a severe occurrence in the iteration structure, disabling its complete conclusion.</p><p></p><p>The <strong>Fail On Error</strong> parameter activation doesn’t have any connection with the errors occurred in the components used for the construction of the subpipelines (onProcess and onException).</p></td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#h_f49963f0c0" id="h_f49963f0c0"></a>

### **Input**

No specific input message is expected, but the existence of a JSON file in the pipeline local directory and the filling of the **File Name** and **JSON Path** fields for the file processing.

### **Output**

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
When the lines are correctly processed, their respective subpipelines return `{ "success": true }` for each of them.
{% endhint %}

The component throws an exception if the **File Name** doesn’t exist or can’t be read.

The files manipulation inside a pipeline occurs in a protected way. All the files can be accessed with a temporary directory only, where each pipeline key gives access to its own files set.

**Stream JSON File Reader** makes batch processing. To better understand the concept, read the [article about Batch processing](https://docs.digibee.com/documentation/tutorials-and-best-practices/batch-processing).&#x20;

## Stream JSON File Reader in action <a href="#h_19235ddca8" id="h_19235ddca8"></a>

### Making the file stream with no filters in JSON Path <a href="#h_44b611cdc5" id="h_44b611cdc5"></a>

#### **Input**

* file.json

```
{
"products" : [
{
"product": "Chair",
"price": 20.75,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "TV",
"price": 399.99,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Couch",
"price": 100,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Table",
"price": 78.99,
"tags": ["NEW", "FURNITURE"]
}
]
}
```

* **File Name:** file.json
* **JSON Path:** $.products\[\*]

#### **Ouput**

```
{
"total": 4,
"success": 4,
"failed": 0
}
```

Each object inside the "products" array of the informed file will be processed in an independent way:

* **First subflow**

```
{"data": {
"product": "Chair",
"price": 20.75,
"tags": ["NEW", "FURNITURE"]
}}
```

* **Second subflow**

```
{"data": {
"product": "TV",
"price": 399.99,
"tags": ["NEW", "FURNITURE"]
}}
```

* **Third subflow**

```
{"data": {
"product": "Couch",
"price": 100,
"tags": ["NEW", "FURNITURE"]
}}
```

* **Forth subflow**

```
{"data": {
"product": "Table",
"price": 78.99,
"tags": ["NEW", "FURNITURE"]
}}
```

### Making the file stream with filters in JSON Path <a href="#h_44b49d4619" id="h_44b49d4619"></a>

#### **Input**

* file.json

```
{
"products" : [
{
"product": "Chair",
"price": 20.75,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "TV",
"price": 399.99,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Couch",
"price": 100,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Table",
"price": 78.99,
"tags": ["NEW", "FURNITURE"]
}
]
}
```

* **File Name:** file.json
* **JSON Path:** $.products\[?(@.price < 80)]

#### **Output**

```
{
"total": 2,
"success": 2,
"failed": 0
}
```

Each object inside the `"products"` array of the informed file will be processed in an independent way:

* **First subflow**

```
{"data": {
"product": "Chair",
"price": 20.75,
"tags": ["NEW", "FURNITURE"]
} }
```

* **Second subflow**

```
{"data": {
"product": "Table",
"price": 78.99,
"tags": ["NEW", "FURNITURE"]
}}
```

### Making the file stream with filters in JSON Path and returning the ‘product’ attribute value only <a href="#h_142229711f" id="h_142229711f"></a>

#### **Input**

* file.json

```
{
"products" : [
{
"product": "Chair",
"price": 20.75,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "TV",
"price": 399.99,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Couch",
"price": 100,
"tags": ["NEW", "FURNITURE"]
},
{
"product": "Table",
"price": 78.99,
"tags": ["NEW", "FURNITURE"]
}
]
}
```

* **File Name:** file.json
* **JSON Path:** $.products\[?(@.price < 80)].product

#### **Ouput**

```
{
"total": 2,
"success": 2,
"failed": 0
}
```

Each object inside the `"products"` array of the informed file will be processed in an independent way:

* **First subflow**

```
{"data": "Chair" }
```

* **Second subflow**

```
{"data": "Table" }
```
