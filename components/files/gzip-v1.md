---
description: >-
  Discover more about the GZIP component and how to use it on the Digibee
  Integration Platform.
---

# GZIP V1 (Deprecated)

{% hint style="info" %}
The GZIP V1 component is deprecated and no longer updated. Please refer to the document with the most recent version of the feature: [GZIP V2](gzip-v2.md).
{% endhint %}

**GZIP V1** zips an entire JSON object as a string.

## Parameters

Take a look at the configuration parameters of the component:

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="243">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Compress and decompress.</td><td>N/A</td><td>String</td></tr><tr><td><strong>JSON Field</strong></td><td>JSON path to be zipped.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Preserve Original</strong></td><td>If activated, the option preserves original fields that have a prefix with an underscore.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Binary Content</strong></td><td>If activated, the option makes the data to be treated as binary, and base64 is expected.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

Supports any structure, but only if the element to be compressed is specified.

### Output <a href="#output" id="output"></a>

Preserves the input message, with JSON object compressed in the base64 format.

**Example:**

The steps inside **Retry** component are executed 3 times until they're successful - "true" should appear in the message:

```
"start": [
{
"type": "connector",
"name": "gzip-connector",
"stepName": "test-compress",
"params": {
"operation" : "compress",
"failOnError": false,
"jsonField": "body.test",
"preserveOriginal" : false,
"isBinary" : false
}
}
]
```
