---
description: >-
  Discover more about the Base64 component and how to use it on the Digibee
  Integration Platform.
---

# Base64

**Base64** encodes and decodes from/to fields, payload, and files in base64 string format.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data Type</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Defines the operation to be performed: <strong>Encode Fields</strong>, <strong>Encode Payload</strong>, <strong>Encode File</strong>, <strong>Decode Fields</strong>, <strong>Decode Payload</strong>, and <strong>Decode File</strong>.</td><td>Encode Fields</td><td>String</td></tr><tr><td><strong>JSON Fields</strong></td><td>JSON path to be encoded or decoded. The fields must be separated by a comma (for example: field1,field2). This option is valid for the <strong>Encode Fields</strong> and <strong>Decode Fields</strong> operations only.</td><td>fields.field1</td><td>String</td></tr><tr><td><strong>Preserve Original</strong></td><td>If this option is activated, the original fields are preserved, and the prefixes are changed by adding the underline character <code>(_)</code>.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Payload</strong> <code>(DB)</code></td><td>Field to directly inform the payload that will have its content encoded/decoded (for example: <code>body, data, {{ message.payload }}</code>). This option is valid for the <strong>Encode Payload</strong> and <strong>Decode Payload</strong> operations only.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Result As File</strong></td><td>If this option is activated, the result of the encoding or decoding is saved in a file. This option is valid for the <strong>Encode Payload</strong> and <strong>Decode Payload</strong> operations only.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name or full file path (for example, tmp/processed/file.txt) of the file to be compressed.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Output File Name</strong> <code>(DB)</code></td><td>Name of the output file after a file is encoded/decoded. This option is valid for the <strong>Encode File</strong> and <strong>Decode File</strong> operations only.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Is Binary</strong></td><td>If this option is activated, the payload is expected as a binary file. This option is valid for the <strong>Decode Payload</strong> operation.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="warning" %}
The **File Name** and **Output File Name** fields must receive different values. If the values are the same, an error will be produced (an exception).
{% endhint %}

## Messages flow

### Input

For the **Encode Fields** and **Decode Fields** operations, the component expects to receive a JSON containing the fields configured in the JSON Fields property.

**Example**

Configuration:

```
JSON Field = field1,field2
```

The expected JSON must at least have:

```
{   
   "field1": "SOMETHING",   
   "field2": "SOMETHING"
}
```

For the **Encode Payload** and **Decode Payload** operations, you must configure the **Payload** field to encode/decode.

**Example**

Configuration:

```
Payload = {{ message.field1 }}
```

The expected JSON must at least have:

```
{   
   "field1": "SOMETHING"
}
```

For the **Encode File** and **Decode File** operations, you must configure the file that will be encoded/decoded and the resulting file of this operation.

**Example**

```
File Name = input.csv
Output File Name = outputfile.csv
```

### Output

For the **Encode Fields** and **Decode Fields** operations:

```
{
   "field1": "SOMETHING ENCODED/DECODED",
   "field2": "SOMETHING ENCODED/DECODED",
   "_field1": "ORIGINAL VALUE",
   "_field2": "ORIGINAL VALUE",
}
```

For the **Encode Fields** and **Decode Fields** operations, if the input message is preserved:

```
{
   "field1": "SOMETHING ENCODED/DECODED",
   "field2": "SOMETHING ENCODED/DECODED",
   "_field1": "ORIGINAL VALUE",
   "_field2": "ORIGINAL VALUE",
}
```

For the **Encode Payload** and **Decode Payload** operations, if the output is a file:

```
{
   "success": "true",
   "fileName": "file.csv"
}
```

For the **Encode Payload** and **Decode Payload** operations, if the output is a string:

```
{
   "success": "true",
   "result": "SOMETHING ENCODED/DECODED"
}
```

For the **Encode File** and **Decode File** operations:

```
{
   "success": "true",
   "fileName": "file.csv",
   "outputFileName": "file.csv"
}
```
