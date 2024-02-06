---
description: >-
  Discover more about the Stream File Reader component and how to use it on the
  Digibee Integration Platform.
---

# Stream File Reader

**Stream File Reader** reads a local file in a JSON structure, that currently supports CSV only, and triggers subpipelines to process each message. It should be used for heavy files.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="286">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>File name or full file path (i.e. tmp/processed/file.txt) of the local file.</td><td>data.csv</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Name of the characters code for the default file reading.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Element Identifier</strong></td><td>Attribute to be sent in case of errors.</td><td>data</td><td>String</td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Occurs in parallel with the loop execution.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Ignore Invalid Charset</strong></td><td>If the option is activated, the invalid charset configured in the component will be ignored along with the received file.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Advanced</strong></td><td>Definition of advanced parameters.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Skip</strong></td><td>Number of lines to be skipped before the file reading.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Limit</strong></td><td>Maximum number of lines to be read.</td><td>N/A</td><td>Integer</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

The component waits for a message in the following format:

```
{
"filename": "fileName"
}
```

**Local File Name** overrides the default local file.

### Output <a href="#output" id="output"></a>

```
{
"total": 0,
"success": 0,
"failed": 0
}
```

* **total:** total number of processed lines.
* **success:** total number of lines successfully processed.
* **failed:** total number of line whose processing failed.

{% hint style="warning" %}
To know whether a line has been processed correctly, the return value `{ "success": true }` must be present for each processed line.
{% endhint %}

The component throws an exception if the **File Name** doesn't exist or can't be read.

The files manipulation inside a pipeline occurs in a protected way. All the files can be accessed with a temporary directory only, where each pipeline key gives access to its own files set.

This component makes batch processing. To better understand the concept, read the article about [Batch processing](https://docs.digibee.com/documentation/tutorials-and-best-practices/batch-processing).
