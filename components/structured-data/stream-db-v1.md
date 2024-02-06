---
description: Know the component and how to use it.
---

# Stream DB V1 (Deprecated)

**Stream DB V1** makes operations through the connection with a database, streaming data to a subpipeline that processes them.

## Parameters

Take a look at the configuration options for the component:

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th width="130.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Database URL</strong></td><td>Connection string to the database.</td><td>N/A</td><td>String</td></tr><tr><td><strong>SQL Statement</strong></td><td>SQL statement to be executed.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Column Name</strong></td><td>Name of the columns to be read.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Coalesce</strong></td><td>When activated, this option controls if the data objects are coalesced into a string or if an error is generated.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Occurs in parallel with the loop execution.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>When activated, this parameter suspends the pipeline execution only if there’s a severe occurrence in the iteration structure.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Custom Connection Properties</strong></td><td>Specific connection properties defined by the user.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Keep Connections</strong></td><td>If activated, the option will keep the connections to the database for 30 minutes maximum; otherwise, it will be kept for 5 minutes only.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Advanced</strong></td><td>Advanced configurations.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Connection Test Query</strong></td><td>SQL statement to be used before each connection is established - this is an optional parameter and must be applied to databases that don't have reliable information about the connection status.</td><td>N/A</td><td>String</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

The component waits for a message in the following format:

```
{
    "parameters": {
        "name": "value"
        ...
    }
}
```

### Message "onProcess" structure <a href="#message-onprocess-structure" id="message-onprocess-structure"></a>

```
{
    "column1":"data1", 
    "column2":"data2", 
    ...
}
```

### Output with error <a href="#output-with-error" id="output-with-error"></a>

```
{
    "code": error_code,"error": error_message,
    "processedId": the_id_column_value
}
```

### Output <a href="#output" id="output"></a>

```
{
    "total": 0,
    "success": 0,
    "failed": 0
}
```

* **total:** total number of processed lines
* **success:** total number of successfully processed lines
* **failed:** total number of lines whose process failed

{% hint style="info" %}
**Important:** when the lines are correctly processed, their respective subpipelines return { "success": true } for each of them.
{% endhint %}

[This component makes batch processing. To better understand the concept, click here.](https://docs.digibee.com/documentation/tutorials-and-best-practices/batch-processing)
