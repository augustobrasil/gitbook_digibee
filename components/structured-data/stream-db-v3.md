---
description: >-
  Discover more about the Stream DB V3 component and how to use it on the
  Digibee Integration Platform.
---

# Stream DB V3

**Stream DB V3** allows the establishment of a connection with a service that supports the JDBC (Java Database Connectivity) protocol and the execution of the SQL (Structured Query Language) instructions. To see all the databases supported by this component, read the [Supported databases documentation](https://docs.digibee.com/documentation/platform/supported-databases).

Differently from the [**DB V1**](db-v1.md) component, **Stream DB** has been designed to make execution in batches, which means, each return (resulting line or row) of the executed SQL instruction is individually treated through a subpipeline, being able to have its own processing flow. [Read the Subpipelines article to learn more.](https://docs.digibee.com/documentation/build/pipelines/subpipelines)

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="206">Parameter</th><th width="312">Description</th><th width="139.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>For the component to make the authentication to a JDBC service, it's necessary to use a Basic or Kerberos-type account (check the topic <a href="stream-db-v3.md#authentication-via-kerberos">Authentication via Kerberos</a>).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Database URL</strong> <code>(DB)</code></td><td>URL (Uniform Resource Locator) to establish connection to the database server with support to the JDBC protocol. This parameter supports Double Braces (DB).</td><td>jdbc:mysql://35.223.175.97/db-training</td><td>String</td></tr><tr><td><strong>SQL Statement</strong></td><td>SQL instruction to be executed.</td><td>select * from clientes LIMIT 2</td><td>String</td></tr><tr><td><strong>Column Name</strong></td><td>If an error occurs while processing the onProcess subpipeline, the value associated with the column defined in this field will be added to the error message in a new field called "processedId" that can be handled by the onException subpipeline.</td><td>codigo</td><td>String</td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>When activated, this option causes each one of the passes through the pipeline to be made in parallel, reducing the total execution time. However, there's no guarantee that the items will be executed in the order returned by the database.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Blob As File</strong></td><td>If activated, this option causes the blob-type field to be stored in the pipeline context as files; otherwise, the fields are stored as normal texts (strings) and coded in base64.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Clob As File</strong></td><td>If activated, this option causes the clob-type field to be stored in the pipeline context as files; otherwise, the fields are stored as normal texts (strings).</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Charset</strong></td><td>This option will only be shown in case the <strong>Clob As File</strong> option is activated. This parameter allows you to set the Clob file encoding.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>When activated, this parameter suspends the pipeline execution only if there’s a severe occurrence in the iteration structure, disabling its complete conclusion. The <strong>Fail On Error</strong> parameter activation doesn’t have any connection with the errors occurred in the components used for the construction of the subpipelines (onProcess and onException).</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Custom Connection Properties</strong></td><td>Specific connection properties defined by the user.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Keep Connections</strong></td><td>If activated, the option will keep the connection with the database for a maximum of 30 minutes; otherwise, it will be for 5 minutes only.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Advanced</strong></td><td>If activated, the following configurations will be available:</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Pool Size By Actual Consumers</strong></td><td>If the option is activated, the number of pooled connections will be equivalent to the number of consumers configured during pipeline deployment. Otherwise, the pool size is given by the pipeline deployment size, irrespective of the number of consumers.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Exclusive DB Pool</strong></td><td>If the option is activated, a new non-shared pool will always be created for the sole use of this component. Otherwise, a pool might be shared between components if the URL is the same.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Output Column From Label</strong></td><td>For some databases, it's important to keep this option activated if your SELECT is using any alias because that way you guarantee the name of the column will be shown exactly like the configured alias.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Connection Test Query</strong></td><td>SQL instruction to be executed before each connection is established (i.e., <code>select 1 from dual</code>). This parameter is optional and must be applied only to databases that don't have reliable information about the connection status.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Raw SQL Statement</strong> <code>(DB)</code></td><td>If the option is active, the <strong>SQL Statement</strong> parameter allows the use of dynamic queries through Double Braces statements. When using this functionality, you must ensure that the pipeline has security measures against unwanted SQL statements (SQL Injection). See more about this parameter in the <a href="stream-db-v3.md#raw-sql-statement">section</a> below.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
In situations where an Apache Hive database is used, the Updatecount data may be unavailable due to a system behavior. This information will be available only if the updated row control is enabled on the Apache Hive server. [To learn more about Apache Hive support for the Digibee Integration Platform, refer to Supported databases.](https://docs.digibee.com/documentation/platform/supported-databases#apache-hive)
{% endhint %}

## Parameters additional information

### Column Name

See the following example about **Column Name** error message:

```
{
  "timestamp": 1600797662733,
  "error": "Error message",
  "code": 500,
  "processedId": "2"
}
```

### Blob As File

If **Blob As File** is active, the blob-type field is stored as follows:&#x20;

```
// "Blob As File" true
{
  "id": 12,
  "blob": "d3X8YK.file",
}
```

Otherwise, the blob-type field is stored as follows:

{% code overflow="wrap" %}
```

// "Blob As File" false
{
  "id": 12,
  "blob": "iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAIAAACQkWg2AAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAAeSURBVDhPY1Da6EMSYiBJNVDxqAZiQmw0lAZHKAEAaskfEED3lr0AAAAASUVORK5CYII="
}
```
{% endcode %}

### Clob As File

If **Clob As File** is active, the clob-type field is stored as follows:&#x20;

```
// "Clob As File" true
{
  "id": 15,
  "clob": "f7X9AS.file",
}
```

Otherwise, the clob-type field is stored as follows:

```
// "Clob As File" false
{
  "id": 15,
  "clob": "AAAAABBBBBCCCC”
}
```

## Raw SQL Statement

To bring more flexibility when using **Stream DB V3**, we can activate the **Raw SQL Statement** option, previously configure a query, and reference it through Double Braces in the SQL Statement parameter as follows:

### **Query previously defined via Template Transformer**

<figure><img src="../../.gitbook/assets/DB V2 - Raw SQL 01 - apr 23.png" alt=""><figcaption></figcaption></figure>

### **Raw SQL Statement activation**

<figure><img src="../../.gitbook/assets/DB v2 - Raw SQL 02 - apr 23.png" alt=""><figcaption></figcaption></figure>

### **Query referenced in SQL Statement parameter**

<figure><img src="../../.gitbook/assets/DB V2 - Raw SQL 03 - apr 23.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Important:** as a good practice, we strongly recommend that, when activating the **Raw SQL Statement** option, the queries are previously defined using the [Template Transformer](https://docs.digibee.com/documentation/components/tools/template-transformer) component. The use of **Template Transformer** allows validating parameters through FreeMarker technology and also parameter declaration through Double Braces. These parameters are not resolved by **Template Transformer** but by the component **Stream DB V3**, which by default configures and validates the parameters of the SQL statement beforehand (PreparedStatement). By applying these security measures, you reduce the risks of attacks like SQL Injection.
{% endhint %}

In the image below, we have an example of recommended use of the component on the left (with the Double Braces in the WHERE clause, highlighted in green); and another example of non-recommended use on the right (with the FreeMarker in the WHERE clause, highlighted in red), which may pose risks to pipeline safety:

<figure><img src="../../.gitbook/assets/DB V2 - Raw SQL 04 exp - apr 23.png" alt=""><figcaption></figcaption></figure>

## Technology <a href="#technology" id="technology"></a>

### **Authentication via Kerberos** <a href="#authentication-via-kerberos" id="authentication-via-kerberos"></a>

To make an authentication to a database via Kerberos, it's necessary to:

* inform a KERBEROS-type account;
* set a main Kerberos principal;
* set a keytab (that must be the base64 of the own generated keytab file).

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### **Message structure available in the onProcess subpipeline** <a href="#message-structure-available-in-the-onprocess-subpipeline" id="message-structure-available-in-the-onprocess-subpipeline"></a>

Once the SQL instruction is executed, the subpipeline will be triggered receiving the execution result through a message in the following structure:

```
{
    "column1": "data1",
    "column2": "data2",
    "column3": "data3"
}
```

### Output with error <a href="#output-with-error" id="output-with-error"></a>

```
{
    "code": error_code,"error": error message,
    "processId": the_id_column_value
}
```

### Output <a href="#output" id="output"></a>

After the component execution, a message is returned in the following structure:

```
{
    "total": 0,
    "success": 0,
    "failed": 0
}
```

* **total:** total number of processed lines.
* **success:** total number of successfully processed lines.
* **failed:** total number of lines whose processing failed.

{% hint style="info" %}
**Important:** to detect if a line has been correctly processed, each onProcess subpipeline must respond with _{ "success": true }_ to each processed element.
{% endhint %}

**Stream DB V3** makes batch processing. [Refer to the Batch processing article to learn more about this concept.](https://docs.digibee.com/documentation/tutorials-and-best-practices/batch-processing)

## Connection pool <a href="#h_d6ae3483d5" id="h_d6ae3483d5"></a>

By standard, we use a pool based on the configurations of the deployed pipeline. If it's a Small pipeline, then the pool size will be 10; for the Medium it will be 20, and for the Large 40.

It's possible to manage the pool size during the implantation as well. For that, it will be necessary to enable the **Pool Size By Actual Consumers** parameter in the component. With it, it will be used whatever is manually configured in the implantation screen.

In the example of the image above, a SMALL pipeline with 5 consumers was configured. If you want the pool of the database components ([DB V2](db-v2/) and Stream DB V3) to use this size, it's necessary to enable the **Pool Size By Actual Consumers** parameter in all the existing components.

![](<../../.gitbook/assets/streamdb v3.png>)

Be extra careful when configuring the pool size manually so there's no deadlock in concurrent calls to the same database.

Our pool is shared between the database components that access the same database inside the pipeline. If you need an exclusive pool for a determined component, enable the **Exclusive DB Pool** parameter.
