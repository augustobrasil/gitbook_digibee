---
description: >-
  Discover more about the Cassandra DB component and how to use it on the
  Digibee Integration Platform.
---

# Cassandra DB

**Cassandra DB** performs operations on an Apache Cassandra database connection.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="181">Parameter</th><th width="216">Description</th><th width="214.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component to connect to AWS. It can be type AWSv4, with access key and secret or Basic for access to Cassandra server in a data center, with user and password.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Operation to be performed (Insert, Update, Select, Delete).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Connection String</strong></td><td>Connection string with host, port, and keyspace to use.</td><td>cassandra://localhost:9142/keyspace</td><td>String</td></tr><tr><td><strong>Query</strong> <code>(DB)</code></td><td>CQL specification, depending on the selected operation. This parameter accepts Double Braces.</td><td>SELECT * FROM EXAMPLE</td><td>String</td></tr><tr><td><strong>Max Wait For Operation (in ms)</strong></td><td>Time (in ms) the application must wait until the query is finished.</td><td>60000</td><td>Integer</td></tr><tr><td><strong>Heartbeat Connection Timeout (in ms)</strong></td><td>Dummy request to keep connections alive in the pool.</td><td>60000</td><td>Integer</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be stopped; otherwise, the pipeline execution continues, and the result will show the value false for the "success" property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Advanced</strong></td><td>Opens further configuration options.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Pool Size By Actual Consumers</strong></td><td>If "true", the number of pooled connections will be equivalent to the number of consumers configured during pipeline deployment; if "false", then the pool size is given by the pipeline deployment size, irrespective of the number of consumers.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## **Cassandra DB in Action**

CQL (Cassandra Query Language), as the name implies, is the query language for Cassandra. It uses variables in its queries by wrapping them in Double Braces, like \{{id\}}. [Read more in our article about Double Braces Functions.](https://docs.digibee.com/documentation/build/double-braces/double-braces-functions)&#x20;

### Operation Insert

#### Input

* **Account:** cassandra-acc
* **Operation:** Insert
* **Connection String:** `{{global.cassandra-url}}`
* **Query:** `INSERT INTO CUSTOMER (id, first_name) VALUES ({{ message.id }}, {{ message.name }});`
* **Fail On Error:** false

#### Output

```
{
	"data": {},
	"insertCount": 1
}

```

### Operation Update

#### Input

* **Account:** cassandra-acc
* **Operation:** Update
* **Connection String:** `{{global.cassandra-url}}`
* **Query:** `UPDATE CUSTOMER SET first_name = {{ message.newName }} WHERE id = {{ message.id }};`
* **Fail On Error:** false

#### Output

```
{
	"data": {},
	"updateCount": 1
}
```

### Operation Select

{% hint style="info" %}
**Note:** Databases such as Cassandra or AWS Keyspaces may automatically return paginated results if they have a significant number of registers. The Digibee Integration Platform handles this pagination automatically to consolidate the result at the output of the component as an atomic query. This means that no configuration or additional actions are required by the user to obtain these results.
{% endhint %}

#### Input

* **Account:** cassandra-acc
* **Operation:** Select
* **Connection String:** `{{global.cassandra-url}}`
* **Query:** `SELECT * FROM CUSTOMER WHERE id = {{ message.if }};`
* **Fail On Error:** false

#### **Output**

```
{
	"data": [{
		"id": "5095e726-d790-4f93-9a71-10ecf2cdd72f",
		" firstName": "Rafael",
		" lastName": "Garbin"
	}],
	"rowCount": 1
}

```

### Operation Delete

#### Input

* **Account:** cassandra-acc
* **Operation:** Delete
* **Connection String:** `{{global.cassandra-url}}`
* **Query:** `DELETE FROM CUSTOMER WHERE id = {{ message.if }};`
* **Fail On Error:** false

#### Output

```
{
	"data": {},
	"deleteCount": 1
}
```
