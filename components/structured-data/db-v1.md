---
description: Know the component and how to use it.
---

# DB V1 (Deprecated)

**DB V1** makes SELECT, INSERT, DELETE and UPDATE operations, returning the values to a JSON structure.

{% hint style="info" %}
**Important:** be careful with the memory consumption for large datasets. If you prefer, you can use Stream DB instead. [To access its article, click here.](https://docs.digibee.com/documentation/components/structured-data/stream-db-v3)
{% endhint %}

## Parameters

Take a look at the configuration options for the component:

<table data-full-width="true"><thead><tr><th width="145">Parameter</th><th width="415">Description</th><th width="111.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Database URL</strong></td><td>Connection string to the database in JDBC format.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>SQL Statement</strong></td><td>SQL statement to be executed.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Coalesce</strong></td><td>When activated, this option controls if the data objects are coalesced into a string or if an error is generated.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Custom Connection Properties</strong></td><td>Specific connection properties defined by the user.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Keep Connections</strong></td><td>If activated, the option will keep the connections to the database for 30 minutes maximum; otherwise, it will be kept for 5 minutes only.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Advanced</strong></td><td>Advanced configurations.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Connection Test Query</strong></td><td>SQL statement to be used before each connection is established - this is an optional parameter and must be applied to databases that don't have reliable information about the connection status.</td><td>N/A</td><td>N/A</td></tr></tbody></table>

## **Example**

```
{
    "parameters": {
        "field1": {
            "a": "b"
        }
    }
}
```

* coalesce = true => field1 = "{\\"a\\": \\"b\\"}"
* coalesce = false => exception
* coalesce = true => field1 = "{\\"a\\": \\"b\\"}"
* coalesce = false => exception

## Messages flow <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### **Input**

```
{
    "parameters": {
        "name": "value"
        ...
    }
}
```

### **Output**

```
{
    "data": [
        {"column1":"data1", "column2":"data2", ... }
    ]
    "rowCount": number_of_returned_rows
    "updateCount": number_of_rows_updated
}
```

### Output with error <a href="#output-with-error" id="output-with-error"></a>

```
{
    "data": [
        {"column1":"data1", "column2":"data2", ... }
    ]
    "rowCount": number_of_returned_rows
    "updateCount": number_of_rows_updated
}
```

[To know the functions and uses for databases, click here.](https://docs.digibee.com/documentation/tutorials-and-best-practices/functions-and-uses-for-databases)
