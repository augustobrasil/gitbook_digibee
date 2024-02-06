---
description: >-
  Discover more about the GZIP V2 component and how to use it on the Digibee
  Integration Platform.
---

# GZIP V2

**GZIP V2** zips a JSON or a text as a string in base64 or file. The component also compresses and decompresses files in gzip format. This version of the component supports Double Braces.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="307">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Action to be executed by the component (Compress Fields, Compress Payload, Compress File, Decompress Fields, Decompress Payload, and Decompress File).</td><td>Compress Fields</td><td>String</td></tr><tr><td><strong>JSON Fields</strong></td><td>JSON path to be compressed or decompressed, considering the fields must be separated by a comma (e.g., field1, field2).</td><td>body.test</td><td>String</td></tr><tr><td><strong>Preserve Original</strong></td><td>If activated, the option preserves the original fields that have a prefix with an underline.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Binary Content</strong></td><td>This option is valid only for the Compress Fields and Compress Payload operations. If activated, the option makes the data to be treated as binary, and a base64 string is expected.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Payload</strong></td><td>This field is valid only for the Compress Payload and Decompress Payload operations and declares what will be compressed/decompressed in the request.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Result As File</strong></td><td>This field is valid only for the Compress Payload and Decompress Payload operations. If activated, the option will save the result of the compression or decompression in a file.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name of the file or full file path (i.e. tmp/processed/file.txt) of the file to be compressed.</td><td>N/A</td><td>String</td></tr><tr><td><strong>GZIP File Name</strong> <code>(DB)</code></td><td>Name of the file or full file path (i.e. tmp/processed/file.txt) of the file in gzip format.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

For the Compress Fields and Decompress Fields operations, the component is expected to receive a JSON with the fields configured in the **JSON Fields** property.

#### **Example**

With the following configurations:

```
JSON Fields = field1,field2
```

The expected JSON must at least have:

```
{
"field1": "SOMETHING",
"field2": "SOMETHING"
}
```

For the Compress Payload and Decompress Payload operations, you must configure the **Payload** field to make the compression/decompression.

#### **Example**

With the following configurations:

```
Payload = {{ message.field1 }}
```

The JSON must have this value:

```
{
"field1": "SOMETHING"
}
```

For the Compress File and Decompress File operations, you must configure the file to be compressed/decompressed and the resulting file of this operation.

#### **Example**

```
File Name = file.csv
GZIP File Name = file.gzip
```

### Output <a href="#output" id="output"></a>

For the Compress Fields and Decompress Fields operations, the input message is preserved.

For the Compress Payload and Decompress Payload operations, if the output is a file:

```
{
"success": "true",
"fileName": "file.csv"
}
```

For the Compress Payload and Decompress Payload operations, if the output is a string:

```
{
"success": "true",
"result": "SOMETHING COMPRESSED/DECOMPRESSED"
}
```

For the Compress File and Decompress File operations:

```
{
"success": "true",
"fileName": "file.csv",
"gzipFileName": "file.csv"
}
```
